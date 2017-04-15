---

[TOC]

---

**Foreword**

Notes. Python 2 & 3. Consult the [Hitchicker's Guide to Python](http://docs.python-guide.org/en/latest/).

---

## The `datatime` library

When building an application incorporating a time triggers, events, records log entries, and much more, we need to deal with dates and times; and time zones. Whether it is a simple script that starts every morning to scrape web data, build a report, and send emails or a comprehensive web framework script that records data entries.

### `now` or any date-time

The `datatime` library has handy built-in functions: `date`, `time`, `datetime`, `timedelta`, and `tzinfo`. The following script demonstrates some of the functionalities.

```python
import datetime

print "The datatime library: "
print dir(datetime)
print "=" * 25

print "The current datetime: "
print datetime.datetime.now()

print "...in a variable: "
test_start = datetime.datetime.now()
print test_start
print "=" * 25

print "Replace the attributes: new formatting."
test_start = test_start.replace(hour=7, minute=39, second = 0, microsecond=0)
print test_start
print "=" * 25
```

Results.

```test
import datetime

The datatime library: 
['MAXYEAR', 'MINYEAR', '__doc__', '__name__', '__package__', 'date', 'datetime', 'datetime_CAPI', 'time', 'timedelta', 'tzinfo']
=========================

The current datetime: 
2016-04-08 10:03:06.120000
...in a variable: 
2016-04-08 10:03:06.120000
=========================

Replace the attributes: new formatting.
2016-04-08 07:39:00
=========================
```

### Date-time difference

Create a date-time and compute the time difference.

```python
import datetime

print "Start: "
print test_start
print "=" * 25

duration = datetime.datetime.now() - test_start
print "duration = datetime.datetime.now() - test_start: "
print "duration = ", duration
print "day = ", duration.days
print "microseconds = ", duration.microseconds
print "seconds = ", duration.seconds
print "hours (round(seconds/3600)) = ", round(duration.seconds/3600)
```

Results.

```text
Start: 
2016-04-08 07:39:00
=========================

duration = datetime.datetime.now() - test_start: 
duration =  2:24:06.120000
day =  0
microseconds =  120000
seconds =  8646
hours (round(seconds/3600)) =  2.0
minutes (round(seconds/60)) =  144.0
=========================
```

### Measure duration with `timedelta`

Create a delta.

```python
print "datetime.datetime.now():"
print datetime.datetime.now()

print "datetime.datetime.now() + datetime.timedelta(days=3): "
print datetime.datetime.now() + datetime.timedelta(days=3)
print "...........................................(days=-5): "
print datetime.datetime.now() + datetime.timedelta(days=-5)
print "...........................................(days=-1): "
print datetime.datetime.now() + datetime.timedelta(days=-1)
print "=" * 25
print ""

print "datetime.datetime.now() + datetime.timedelta(hours=1): "
print datetime.datetime.now() + datetime.timedelta(hours=1)
print "datetime.datetime.now() + datetime.timedelta(0, 3600): "
print datetime.datetime.now() + datetime.timedelta(0, 3600)
print "=" * 25
print ""

work = 9
print "work = ", work

print "datetime.datetime.now() + datetime.timedelta(hours=work):"
print datetime.datetime.now() + datetime.timedelta(hours=work)
print "=" * 25
print ""
```

Results.

```text
datetime.datetime.now():
2016-04-08 10:06:25.895000
datetime.datetime.now() + datetime.timedelta(days=3): 
2016-04-11 10:06:25.895000
...........................................(days=-5): 
2016-04-03 10:06:25.895000
...........................................(days=-1): 
2016-04-07 10:06:25.895000
=========================

datetime.datetime.now() + datetime.timedelta(hours=1): 
2016-04-08 11:06:25.895000
datetime.datetime.now() + datetime.timedelta(0, 3600): 
2016-04-08 11:06:25.895000
=========================

work =  9
datetime.datetime.now() + datetime.timedelta(hours=work):
2016-04-08 19:06:25.895000
=========================
```

Use `timedelta`.

```python
print "Simplify: "
now = datetime.datetime.now()
print "now: "
print now
print "now.date: "
print now.date()
print "now.time: "
print now.time()
print "=" * 25
print ""

print "1 hour: "
hour = datetime.timedelta(hours=1)
print hour
print "=" * 25
print ""

print "Add 1 day: "
tomorrow = datetime.datetime.now().replace(hour=9, minute=0) + datetime.timedelta(days=1)
print tomorrow

print "Add 1 day (2): "
workday = datetime.timedelta(hours=8)
print tomorrow + workday
print "=" * 25
print ""

print "Appointment: "
appointment = datetime.timedelta(minutes=45)
# year, month, day, hour, minute
start =  datetime.datetime(2016, 8, 17, 12, 45)
end = start + appointment
print end
print "=" * 25
print ""
```

Results.

```text
Simplify: 
now: 
2016-04-08 10:16:11.476000
now.date: 
2016-04-08
now.time: 
10:16:11.476000
=========================

1 hour: 
1:00:00
=========================

Add 1 day: 
2016-04-09 09:00:11.476000
Add 1 day (2): 
2016-04-09 17:00:11.476000
=========================

Appointment: 
2016-08-17 13:30:00
=========================
```

### `now` vs. `today`

The difference between `now` and `today` is...

```python
import datetime

now = datetime.datetime.now()
today = datetime.datetime.today()
print now
print today
print "=" * 25
print ""
```

Results.

```text
2016-04-08 10:34:28.444000
2016-04-08 10:34:28.444000
=========================
```

...`now` can take a timezone. We deal with timezones further down. `Today`...

```python
import datetime

today = datetime.datetime.combine(datetime.date.today(), datetime.time())
print today # today at midnight
print today.month
print today.hour
print today.year
print today.weekday() # 0 = Monday, 1, 2, 3, 4
print "=" * 25
print ""
```

Results.

```text
2016-04-08 00:00:00
4
0
2016
5
=========================
```

### Formatting date-time

Format date and time.

```python
import datetime

now = datetime.datetime.now()
print now

# how to better present
# strftime (strings-from-time) or turn datetime digits into strings

print "formatting datetime:"
print now.strftime('%B %d')
print now.strftime('%m/%m/%y')
```

Results.

```text
2016-04-08 11:08:26.757000
formatting datetime:
April 08
04/04/16
```

`strptime` (strings-parse-time) turns strings into datetime digits. Look for help online for date and time types.

```python
import datetime

print "Formatting datetime: "
print now.strftime('%B %d')
print now.strftime('%m/%m/%y')
print "=" * 25
print ""

print "bithday: "
birthday = datetime.datetime.strptime('2016-04-21', '%Y-%m-%d')
print birthday
print "=" * 25
print ""

print "bithday_party: "
birthday_party = datetime.datetime.strptime('2016-04-22 12:00', '%Y-%m-%d %H:%M')
print birthday_party
print "=" * 25
print ""
```

Results.

```text
Formatting datetime: 
April 08
04/04/16
=========================

bithday: 
2016-04-21 00:00:00
=========================

bithday_party: 
2016-04-22 12:00:00
=========================
```

### A little printing app

Build an application that prints out a date in a sentence.

```python
import datetime

answer_format = '%m/%d'
link_format = '%b_%d'
link = 'https://en.wikipedia.org/wiki/{}'

while True:
	answer = raw_input("What date would you like? Please use the MM/DD format. Enter 'q' to quit.")
	answer2 = str(answer)
	if answer2.upper() == 'Q':
		break
	
	try:
		date = datetime.datetime.strptime(answer, answer_format)
		output = link.format(date.strftime(link_format))
		print(output)
		file = open('output.txt', 'w')
		file.write(output)
		file.close()
	except:
		print("That's not a valid date. Please try again.")
		break
```

Run it; it creates an output file. Open output.txt. Copy the link and paste it into a web browser.

## Build a Quiz application

### Build the skeleton

Build an application (questions.py) that add and multiply numbers.

```python
import datetime

class Question:
	answer = None
	text = None


class Add(Question):
	def __init__(self, num1, num2):
		self.text = '{} + {}'.format(num1, num2)
		self.answer = num1 + num2


class Multiply(Question):
	def __init__(self, num1, num2):
		self.text = '{} x {}'.format(num1, num2)
		self.answer = num1 * num2


print "Add: "
add1 = Add(5, 7)
print add1.text
print add1.answer
print "Multiply: "
multiply1 = Multiply(2, 2)
print multiply1.text
print multiply1.answer
```

Results.

```text
Add: 
5 + 7
12
Multiply: 
2 x 2
4
```

Import the questions.py module in another script: quiz.py. Build the skeleton.

```python
import datetime
import random

from questions import Add, Multiply # import the other module


class Quiz:
    questions = []
    answers = []
	
    def __init__(self):
        # generate 10 random questions with numbers from 1 to 10
        # add these questions into self.questions
        pass
        
    def take_quiz(self):
        # log the start time
        # ask all of the questions
        # log if they got the question right
        # log the end time
        # show a summary
        pass
        
    def ask(self, question):
        # log the start time
        # capture the answer
        # check the answer
        # log the end time
        # if the answer's right, send back True
        # otherwise, send back False
        # send back the elapses time, too
        pass
        
        
    def total_correct(self):
        # return the total # of correct answers
        pass

        
    def summary(self):
        # print how many you got right and the total of questions: 5/10
        # print the total time for the quiz: 30 seconds!
        pass
```

Results (similar).

```text
Add: 
5 + 7
12
Multiply: 
2 x 2
4
```

### Generate questions

Complete some functions and test the script.

```python
import datetime
import random

from questions import Add, Multiply


class Quiz: # ADD
    questions = []
    answers = []
	
    def __init__(self):
        """
        generate 10 random questions with numbers from 1 to 10
        add these questions into self.questions
        """
        question_types = (Add, Multiply)
        
        for _ in range(10): # _ we don't care if it's 1, 5 or 12, as long as it is a number
            num1 = random.randint(1, 10)
            num2 = random.randint(1, 10)
            question = random.choice(question_types)(num1, num2)
            # add these questions into self.questions
            self.questions.append(question)
        
    def take_quiz(self):
        # log the start time
        # ask all of the questions
        # log if they got the question right
        # log the end time
        # show a summary
        pass
        
    def ask(self, question):
        # log the start time
        # capture the answer
        # check the answer
        # log the end time
        # if the answer's right, send back True
        # otherwise, send back False
        # send back the elapses time, too
        pass
    

    def total_correct(self): # ADD
        """return the total # of correct answers"""
        total = 0
        for answer in self.answers:
            if answer[0]:
                total += 1
        return total
    
    def summary(self): # ADD
        """
        print how many you got right and the total of questions: 5/10
        print the total time for the quiz: 30 seconds!
        """
        print("You got {} out of {} right.".format(
                self.total_correct(), len(self.questions)
        ))
        print("It took you {} seconds total.".format(
                (self.end_time-self.start_time).seconds
        ))

        
quiz1 = Quiz()
print quiz1.answers
print quiz1.questions
print "=" * 25
print quiz1.questions[0].text
print quiz1.questions[0].answer
```

Results.

```text
Add: 
5 + 7
12
Multiply: 
2 x 2
4
[]
[<questions.Add instance at 0x00000000022B7E88>, <questions.Multiply instance at 0x00000000022FBC88>, <questions.Multiply instance at 0x00000000022FB688>, <questions.Multiply instance at 0x00000000022FBDC8>, <questions.Add instance at 0x00000000022FBE08>, <questions.Multiply instance at 0x00000000022FBE48>, <questions.Multiply instance at 0x00000000022FBE88>, <questions.Add instance at 0x00000000022FBEC8>, <questions.Multiply instance at 0x00000000022FBF08>, <questions.Multiply instance at 0x00000000022FBF48>]
=========================
3 + 1
4
```

### Finalize the application

Complete the script and test it.

```python
import datetime
import random

from questions import Add, Multiply


class Quiz:
    questions = []
    answers = []
	
    def __init__(self):
        """
        generate 10 random questions with numbers from 1 to 10
        add these questions into self.questions
        """
        question_types = (Add, Multiply)
        
        for _ in range(10): # _ we don't care if it's 1, 5 or 12, as long as it is a number
            num1 = random.randint(1, 10)
            num2 = random.randint(1, 10)
            question = random.choice(question_types)(num1, num2)
            # add these questions into self.questions
            self.questions.append(question)
        
    def take_quiz(self): # ADD
        """
        log the start time, ask all of the questions
        log if they got the question right, log the end time
        show a summary
        """
        # log the start time
        self.start_time = datetime.datetime.now()

        # ask all of the questions
        for question in self.questions:
            self.answers.append(self.ask(question))
        else: # if the loop reached the end, so else happends
            self.end_time = datetime.datetime.now()

        # show a summary
        return self.summary()     


    def ask(self, question): # ADD
        """
        log the start time, capture the answer, check the answer
        log the end time, if the answer's right, send back True
        otherwise, send back False, send back the elapses time, too
        """
        correct = False
        # log the start time
        question_start = datetime.datetime.now()

        # capture the answer
        answer = raw_input(question.text + ' = ')

        # check the answer
        if answer == str(question.answer):
            correct = True

        # log the end time
        question_end = datetime.datetime.now()

        # if the answer's right, send back True
        # otherwise, send back False
        # send back the elapses time, too
        return correct, question_end - question_start


    def total_correct(self):
        """return the total # of correct answers"""
        total = 0
        for answer in self.answers:
            if answer[0]:
                total += 1
        return total
    
    def summary(self):
        """
        print how many you got right and the total of questions: 5/10
        print the total time for the quiz: 30 seconds!
        """
        print("You got {} out of {} right.".format(
                self.total_correct(), len(self.questions)
        ))
        print("It took you {} seconds total.".format(
                (self.end_time-self.start_time).seconds
        ))

        
Quiz().take_quiz() # ADD
```

The results are dynamic. We would get something that look like the following:

```text
Add: 
5 + 7
12
Multiply: 
2 x 2
4
7 x 6 = 54
9 x 10 = 90
4 x 3 = 12
3 + 6 = 9
5 + 6 = 11
10 x 6 = 60
4 x 6 = 24
9 + 9 = 18
2 x 5 = 10
8 + 3 = 11
You got 9 out of 10 rights.
It took you 21 seconds total.
```

## Time zones

Timezones are major challenges for websites and web frameworks. The following is coded in Python 3 since the most common Python frameworks (Flask, Django, Pyramid) at the time this documentation is written work under Python 3. One of the reason is the multi-language ability.

### Time zones with `datatime` only

We build two timezone-aware variables.

```python
import datetime

pacific = datetime.timezone(datetime.timedelta(hours=-8))
eastern = datetime.timezone(datetime.timedelta(hours=-5))

print(pacific)
print(eastern)
```

Results.

```python
UTC-08:00
UTC-05:00
```

We build one timezone-naive variable and one timezone-aware variable.

```python
# ...

naive = datetime.datetime(2014, 4, 21, 9)
print(naive)

aware = datetime.datetime(2014, 4, 21, 9, tzinfo=pacific)
print(aware)
```

Results.

```python
2014-04-21 09:00:00
2014-04-21 09:00:00-08:00
```

Show these in eastern time.

```python
# ...

print(naive.astimezone(eastern))
```

Results: cannot be applied to a naive datetime.

```python
# ...

print(aware.astimezone(eastern))
```

Results.

```text
2014-04-21 12:00:00-05:00
```

Other interesting time zones.

```python
# ...

aukland = datetime.timezone(datetime.timedelta(hours=13))
print(aukland)
print(aware.astimezone(aukland))
print("=" * 25)

mumbai = datetime.timezone(datetime.timedelta(hours=13, minutes=30))
print(mumbai)
print(aware.astimezone(mumbai))
```

Results.

```text
UTC+13:00
2014-04-22 06:00:00+13:00
=========================
UTC+05:30
2014-04-21 22:30:00+05:30
```

### Time zones with `datatime` and `pytz`

`pytz` simplify things (a lot!).

```python
import datetime
import pytz

pacific = pytz.timezone('US/Pacific')
eastern = pytz.timezone('US/Eastern')

fmt = '%Y-%m-%d %H:%M:%S %Z%z'
utc = pytz.utc

print("set: ")
start = pacific.localize(datetime.datetime(2014, 4, 21, 9))
print(start.strftime(fmt))
print("=" * 25)

print("convert: ")
start_eastern = start.astimezone(eastern)
print(start_eastern)
print("=" * 25)

print(start)
print("=" * 25)
```

Results.

```text
set: 
2014-04-21 09:00:00 PDT-0700
=========================
convert: 
2014-04-21 12:00:00-04:00
=========================
2014-04-21 09:00:00-07:00
=========================
```

More conversions.

```python
# ...

print("set: ")
start_utc = datetime.datetime(2014, 4, 21, 1, tzinfo=utc)
print(start_utc.strftime(fmt))
print("=" * 25)

print("convert: ")
start_pacific = start_utc.astimezone(pacific)
print(start_pacific)
print("=" * 25)
```

Results.

```text
set: 
2014-04-21 01:00:00 UTC+0000
=========================
convert: 
2014-04-20 18:00:00-07:00
=========================
```

Set a date-time and convert it.

```python
# ...

print("set aukland and mumbai")
auckland = pytz.timezone('Pacific/Auckland')
mumbai = pytz.timezone('Asia/Calcutta')

print("create a date")
apollo_13_naive = datetime.datetime(1970, 4, 11, 14, 13)
apollo_13_eastern = eastern.localize(apollo_13_naive)

print("print it: ")
print(apollo_13_naive)
print(apollo_13_eastern)
print("=" * 25)

print("convert it, change location: ")
apollo_13_utc = apollo_13_eastern.astimezone(utc)
print(apollo_13_utc.astimezone(pacific).strftime(fmt))
print(apollo_13_utc.astimezone(auckland))
print(apollo_13_utc.astimezone(mumbai))
```

Results.

```text
set aukland and mumbai
create a date
print it: 
1970-04-11 14:13:00
1970-04-11 14:13:00-05:00
=========================
convert it, change location: 
1970-04-11 11:13:00 PST-0800
1970-04-12 07:13:00+12:00
1970-04-12 00:43:00+05:30

```

### Find out more about `pytz`

Find out about timezones: `print(pytz.all_timezones)`. Or focus on a country's timezones. The US.

```python
print(pytz.country_timezones['us'])
```

Results.

```text
['America/New_York', 'America/Detroit', 'America/Kentucky/Louisville', 'America/Kentucky/Monticello', 'America/Indiana/Indianapolis', 'America/Indiana/Vincennes', 'America/Indiana/Winamac', 'America/Indiana/Marengo', 'America/Indiana/Petersburg', 'America/Indiana/Vevay', 'America/Chicago', 'America/Indiana/Tell_City', 'America/Indiana/Knox', 'America/Menominee', 'America/North_Dakota/Center', 'America/North_Dakota/New_Salem', 'America/North_Dakota/Beulah', 'America/Denver', 'America/Boise', 'America/Phoenix', 'America/Los_Angeles', 'America/Anchorage', 'America/Juneau', 'America/Sitka', 'America/Metlakatla', 'America/Yakutat', 'America/Nome', 'America/Adak', 'Pacific/Honolulu']
```

Canada.

```python
print(pytz.country_timezones['ca'])
```

Results.

```text
['America/St_Johns', 'America/Halifax', 'America/Glace_Bay', 'America/Moncton', 'America/Goose_Bay', 'America/Blanc-Sablon', 'America/Toronto', 'America/Nipigon', 'America/Thunder_Bay', 'America/Iqaluit', 'America/Pangnirtung', 'America/Atikokan', 'America/Winnipeg', 'America/Rainy_River', 'America/Resolute', 'America/Rankin_Inlet', 'America/Regina', 'America/Swift_Current', 'America/Edmonton', 'America/Cambridge_Bay', 'America/Yellowknife', 'America/Inuvik', 'America/Creston', 'America/Dawson_Creek', 'America/Fort_Nelson', 'America/Vancouver', 'America/Whitehorse', 'America/Dawson']
```

Russia.

```python
print(pytz.country_timezones['ru'])
```

Results.

```text
['Europe/Kaliningrad', 'Europe/Moscow', 'Europe/Simferopol', 'Europe/Volgograd', 'Europe/Kirov', 'Europe/Astrakhan', 'Europe/Saratov', 'Europe/Ulyanovsk', 'Europe/Samara', 'Asia/Yekaterinburg', 'Asia/Omsk', 'Asia/Novosibirsk', 'Asia/Barnaul', 'Asia/Tomsk', 'Asia/Novokuznetsk', 'Asia/Krasnoyarsk', 'Asia/Irkutsk', 'Asia/Chita', 'Asia/Yakutsk', 'Asia/Khandyga', 'Asia/Vladivostok', 'Asia/Ust-Nera', 'Asia/Magadan', 'Asia/Sakhalin', 'Asia/Srednekolymsk', 'Asia/Kamchatka', 'Asia/Anadyr']
```

### Build a script to convert time zones

Build a script that takes a datetime and give it back in 6 other timezones. For any given datetime, an appointment for example, we can know the equivalent elsewhere in the world.

```python
from datetime import datetime

import pytz

OTHER_TIMEZONES = [
	pytz.timezone('US/Eastern'),
	pytz.timezone('Pacific/Auckland'),
	pytz.timezone('Asia/Calcutta'),
	pytz.timezone('UTC'),
	pytz.timezone('Europe/Paris'),
	pytz.timezone('Africa/Khartoum'),
]

fmt = '%Y-%m-%d %H:%M:%S %Z%z'

while True:
	date_input = input("When is your meeting? Please use MM/DD/YYYY HH:MM format. ")
	try:
		local_date = datetime.strptime(date_input, '%m/%d/%Y %H:%M')
	except ValueError:
		print("{} doesn't seem to be a valid date & time.".format(date_input))
	else:
		local_date = pytz.timezone('US/Pacific').localize(local_date)
		utc_date = local_date.astimezone(pytz.utc)
		
		output = []
		for timezone in OTHER_TIMEZONES:
			output.append(utc_date.astimezone(timezone))
		for appointment in output:
			print(appointment.strftime(fmt))
		break
```

Results (1 inputs, 6 outputs).

```text
When is your meeting? Please use MM/DD/YYYY HH:MM format. 01/01/2018 13:00
2018-01-01 16:00:00 EST-0500
2018-01-02 10:00:00 NZDT+1300
2018-01-02 02:30:00 IST+0530
2018-01-01 21:00:00 UTC+0000
2018-01-01 22:00:00 CET+0100
2018-01-02 00:00:00 EAT+0300
```