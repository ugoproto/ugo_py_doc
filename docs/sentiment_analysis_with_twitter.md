---

**Foreword**

Code snippets and excerpts from the tutorial. Python 3. From DataCamp.

---

# Import the modules and connect to Tweeter

From this [link](https://www.youtube.com/watch?v=o_OZdbCzHUA), analyze sentiments and perform text mining: tokenization, bag words, sentiment value from a lexicon. Psychology and Sociology. Consumer satisfaction. Comments.

Find out about [tweepy](http://www.tweepy.org/) (Twitter API) and [textblob](https://textblob.readthedocs.io/en/dev/). TextBlob stands on the shoulders of NLTK and process textual data. It provides a simple API for diving into common natural language processing (NLP) tasks such as part-of-speech tagging, noun phrase extraction, sentiment analysis, classification, translation, and more.


```python
import pandas as pd

# store the keys in a file to keep them private
twitter_api = pd.read_csv('twitter_api.csv', header=0, sep=',')
```


```python
import tweepy
from textblob import TextBlob

# must have a Twitter account, see the video

# authenticate with...
# api_key
consumer_key = twitter_api.get_value(0, 'api_key')
# api_secret
consumer_secret = twitter_api.get_value(0, 'api_secret')
# access token
access_token = twitter_api.get_value(0, 'access_token')
# access secret
access_token_secret = twitter_api.get_value(0, 'access_secret')

auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_token_secret)

api = tweepy.API(auth)
```

# Retrieve tweets


```python
# retrieve tweets with the API
public_tweets = api.search('Climate')

for tweet in public_tweets:
    print(tweet.text)
```

# Perform sentiment analysis


```python
# perform sentiment analysis on each tweet
# -1 < polarity < 1 (negativity vs positivity (sentiment))
# 0 < subjectivity < 1 (factual vs opinion)
for tweet in public_tweets:
    print(tweet.text)
    analysis = TextBlob(tweet.text)
    print(analysis.sentiment)
    print("----------")
```


```python
# create a list of dictionaries
# each dictionary contains a tweet text and user
# the list bundle up the dictionaries
saved_tweets = []
for tweet in public_tweets:
    parsed_tweet = {}
    parsed_tweet['text'] = tweet.text
    parsed_tweet['user'] = tweet.user.screen_name
    saved_tweets.append(parsed_tweet)
```


```python
# convert the list into a data frame
saved_tweets_df = pd.DataFrame(saved_tweets)
# print the head
print(saved_tweets_df.head(3))
```


```python
# save the data frame into a csv file
saved_tweets_df.to_csv('saved_tweets_df.csv')
```

# An overview of NLP (with `nltk` and `textblob`)

Make sure to install the `nltk` (with pip or conda) module and then run `python -m textblob.download_corpora`.


```python
# a comment or an opinion
comment = TextBlob("I am angry that I never get good players in my pool")
```


```python
print(comment)
```


```python
# tags are not token
print(comment.tags)
```


```python
# words are like tokens
print(comment.words)
```


```python
# -1 < polarity < 1 (negativity vs positivity (sentiment))
print(comment.sentiment.polarity)
```


```python
# 0 < subjectivity < 1 (factual vs opinion)
print(comment.sentiment.subjectivity)
```


```python
# both
print(comment.sentiment)
```


```python
# a fact
fact = TextBlob("The sun is setting at the moment")

print(fact.sentiment)
```

# Applications

## Query Tweeter, generate categorical results, populate a list of dictionaries

Pointers:

- Use of functions and a class.
- Error-handling authentication.
- Query tweets, retweets, etc.
- Generate categorical results with sentiment analysis.
- Create a list of little dictionaries for parsing and containing tweet data and metadata.
- Error-handling parsing.
- Filter retweets.

```python
import os
import re
import tweepy
from tweepy import OAuthHandler
from textblob import TextBlob


class TwitterClient(object):
    '''
    Generic Twitter Class for the App
    '''
    def __init__(self, query, retweets_only=False, with_sentiment=False):
        # keys and tokens from the Twitter Dev Console
        consumer_key = os.environ['CONSUMER_KEY']
        consumer_secret = os.environ['CONSUMER_SECRET']
        access_token = os.environ['ACCESS_TOKEN']
        access_token_secret = os.environ['ACCESS_TOKEN_SECRET']
        # Attempt authentication
        try:
            self.auth = OAuthHandler(consumer_key, consumer_secret)
            self.auth.set_access_token(access_token, access_token_secret)
            self.query = query
            self.retweets_only = retweets_only
            self.with_sentiment = with_sentiment
            self.api = tweepy.API(self.auth)
            self.tweet_count_max = 100  # To prevent Rate Limiting
        except:
            print("Error: Authentication Failed")

    def set_query(self, query=''):
        self.query = query

    def set_retweet_checking(self, retweets_only='false'):
        self.retweets_only = retweets_only

    def set_with_sentiment(self, with_sentiment='false'):
        self.with_sentiment = with_sentiment

    def clean_tweet(self, tweet):
        return ' '.join(re.sub("(@[A-Za-z0-9]+)|([^0-9A-Za-z \t])|(\w+:\/\/\S+)", " ", tweet).split())

    def get_tweet_sentiment(self, tweet):
        analysis = TextBlob(self.clean_tweet(tweet))
        if analysis.sentiment.polarity > 0:
            return 'positive'
        elif analysis.sentiment.polarity == 0:
            return 'neutral'
        else:
            return 'negative'

    def get_tweets(self):
        tweets = []

        try:
            recd_tweets = self.api.search(q=self.query,
                                          count=self.tweet_count_max)
            if not recd_tweets:
                pass
            for tweet in recd_tweets:
                parsed_tweet = {}

                parsed_tweet['text'] = tweet.text
                parsed_tweet['user'] = tweet.user.screen_name
                
                if self.with_sentiment == 1:
                    parsed_tweet['sentiment'] = self.get_tweet_sentiment(tweet.text)
                else:
                    parsed_tweet['sentiment'] = 'unavailable'

                if tweet.retweet_count > 0 and self.retweets_only == 1:
                    if parsed_tweet not in tweets:
                        tweets.append(parsed_tweet)
                elif not self.retweets_only:
                    if parsed_tweet not in tweets:
                        tweets.append(parsed_tweet)

            return tweets

        except tweepy.TweepError as e:
print("Error : " + str(e))
```

## Query Tweeter, generate categorical results, populate a dictionary of lists, write files, compute statistics

Pointers:

- Scope the queries: keywords, dates.
- Generate categorical results with sentiment analysis.
- Generate a dictionary of lists.
- Write a file for each candidate (not pandas involved); the list.
- Enrich each tweet for each candidate with sentiment analysis and the mean values; the list.
- Build a list of all sentiment analysis.
- With the dictionary of lists, sort the mean values and rank the keywords.

```python
import tweepy
from textblob import TextBlob
#French adaptor
from textblob_fr import PatternTagger, PatternAnalyzer

import numpy as np
import operator


# Step 1 - Authenticate
consumer_key= 'CONSUMER_KEY_HERE'
consumer_secret= 'CONSUMER_SECRET_HERE'

access_token='ACCESS_TOKEN_HERE'
access_token_secret='ACCESS_TOKEN_SECRET_HERE'

auth = tweepy.OAuthHandler(consumer_key, consumer_secret)
auth.set_access_token(access_token, access_token_secret)

api = tweepy.API(auth)

#Step 2 - Prepare query features

#List of candidates to French Republicans Primary Elections
candidates_names = ['Sarkozy', 'Kosciusko', 'Cope', 'Juppe', 'Fillon', 'Le Maire', 'Poisson']
#Hashtag related to the debate
name_of_debate = "PrimaireLeDebat" 
#Date of the debate : October 13th
since_date = "2016-10-13"
until_date = "2016-10-14"

#Step 2b - Function of labelisation of analysis
def get_label(analysis, threshold = 0):
	if analysis.sentiment[0]>threshold:
		return 'Positive'
	else:
		return 'Negative'


#Step 3 - Retrieve Tweets and Save Them
all_polarities = dict()
for candidate in candidates_names:
	this_candidate_polarities = []
	#Get the tweets about the debate and the candidate between the dates
	this_candidate_tweets = api.search(q=[name_of_debate, candidate], count=100, since = since_date, until=until_date)
	#Save the tweets in csv
	with open('%s_tweets.csv' % candidate, 'wb') as this_candidate_file:
		this_candidate_file.write('tweet,sentiment_label\n')
		for tweet in this_candidate_tweets:
			analysis = TextBlob(tweet.text, pos_tagger=PatternTagger(), analyzer=PatternAnalyzer())
			#Get the label corresponding to the sentiment analysis
			this_candidate_polarities.append(analysis.sentiment[0])
			this_candidate_file.write('%s,%s\n' % (tweet.text.encode('utf8'), get_label(analysis)))
	#Save the mean for final results
	all_polarities[candidate] = np.mean(this_candidate_polarities)
 
#Step bonus - Print a Result
sorted_analysis = sorted(all_polarities.items(), key=operator.itemgetter(1), reverse=True)
print 'Mean Sentiment Polarity in descending order :'
for candidate, polarity in sorted_analysis:
print '%s : %0.3f' % (candidate, polarity)
```
