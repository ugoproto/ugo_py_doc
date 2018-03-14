<!--
---

[TOC]
-->
---

**Foreword**

Notes. Python 2 in Windows. UNIX-based OS generate slighly different results. Contrary to Windows, UNIX-based OS easily process international characters. Consult the [Hitchicker's Guide to Python](http://docs.python-guide.org/en/latest/).

- Check out 'Managing Your Biological Data with Python, Chapter 9, Pattern Matching and Text Mining'.
- [Test](http://www.regexplanet.com/advanced/java/index.html).

---

# Additional Commands (unused)

- `span`, return a tuple containing the start, end positions of the match.
- `start`, return the starting position of the match.
- `end`, return the ending position of the match.
- `group`, return the string matched by the RE
- `groups`, return a tuple containing the strings fal all the subgroups
- `split(s)`, split the string into a list, splitting it wherever the RE matches
- `sub(r, s)`, find all substrings where the RE matches and replaces them with a different string
- `subn(r, s)`, do the same thing, but return the new string and the number of replacements
- `IGNORECASE`, `I`, case-insensitive matches.

# `match` & `search` -- One Expression, One Search

First, we have a text file called names.txt.

```text
Liff, Kenneth	kenneth@submarine.com	(555) 555-5555	Teacher, Submarine	@kennethliff
McFarland, Arthur	arty@submarine.com	(555) 555-5555	Teacher, Submarine
Arthur, King	king_arthur@camelot.co.uk	King, Camelot
Österberg, Gustav	governor@norrbotten.co.se	Governor, Norrbotten	@gustata
, Tim	tim@killerrabbit.com	Enchanter, Killer Rabbit Cave
Carson, Ryan	ryan@submarine.com	(555) 555-5543	CEO, Submarine	@ryancarson
Doctor	The doctor+companion@tardis.co.uk	Time Lord, Gallifrey
Exampleson, Exampleme	me@example.com	555-555-5552	Example, Example Co.	@exemple
Obama, Barack	president.44@us.gov	555 555-5551	President, United States of America	@potus44
Chalks, Andrew	andrew@submarine.com	(555) 555-5553	Teacher, Submarine	@chalkers
Vader, Darth	darth-vader@empire.gov	(555) 555-4444	Sith lord, Galactic Empire	@darthvader
```

Second, we want to process the file: extract strings. 

We could use `re.match`, but the function is picky. `re.search` is more forgiving in terms of precision. In both cases, the function should return the first match it finds, then stop.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# print what is in memory
print re.search(r'McFarland', data).group() # r for raw string, no need for \
print re.search(r'Arthur', data).group() # search in the strings
```

Results (in Windows).

```text
<_sre.SRE_Match object at 0x00000000021DB510>
<_sre.SRE_Match object at 0x00000000021DB510>
```

Results may vary in UNIX-type OS. In Linux, we get.

```text
<_sre.SRE_Match object; span=(0, 8), match='McFarland'>
<_sre.SRE_Match object; span=(10, 15), match='Arthur'>
```

Change the script and rerun it.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# print what is in memory
print re.search(r'McFarland', data).group() # CHANGE
print re.search(r'Arthur', data).group() # CHANGE
```

Results.

```text
McFarland
Arthur
```

Alternatively.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# print what is in memory
last_name = r'McFarland'
first_name = r'Arthur'
print re.search(last_name, data).group() # CHANGE
print re.search(first_name, data).group() # CHANGE
```

## Recap

- `match`.
- `search`.

# Escape Characters -- Comprenhensive Search

- `\w`, match any Unicode word character.
- `\W`, match anything that isn't a Unicode word character.
- `\s`, any whitespace.
- `\S`, not.
- `\d`, any number 0-9.
- `\D`, not.
- `\b`, boundaries or the edges of a word.
- `\B`, not.

Try.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

print re.match(r'\w, \w', data) # CHANGE
```

Results.

```text
None
```

We get `None` because of `re.match`. Instead, try.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# catch phone numbers
print re.search(r'\d\d\d-\d\d\d\d', data).group() # CHANGE
```

Results.

```text
555-5555
```

Improve the code.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# catch complete phone numbers
print re.search(r'\(\d\d\d\) \d\d\d-\d\d\d\d', data).group() # CHANGE
```

Results.

```text
(555) 555-5555
```

## Recap

- `match`.
- `search`.
- Escape characters (see above).

# Repetitions -- Power Search

- `{3}`, repeat 3 times.
- `{,3}`, repeat 0 to 3 times.
- `{3,}`, repeat 3 or more times.
- `{3, 5}`, repeat 3, 4 or 5 times.
- `?`, repeat 0 or once.
- `*`, repeat at least 0 times (no upper bound).
- `+`, repeat at least once (no upper bound).

Catch a name.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# catch a name
print re.search(r'\w+, \w+', data).group() # CHANGE
```

Results.

```text
Liff, Kenneth
```

Catch a phone number.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# catch a complete phone numbers
print re.search(r'\(\d{3}\) \d{3}-\d{4}', data).group() # CHANGE
```

Results.

```text
(555) 555-5555
```

Catch multiple phone numbers.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# more universal way (parentheses, hyphen, space become optional)
# on multiple lines!
print re.findall(r'\(?\d{3}\)?-?\s?\d{3}-\d{4}', data) # CHANGE
```

Results.

```text
['(555) 555-5555', '(555) 555-5555', '(555) 555-5543', '555-555-5552', '555 555-5551', '(555) 555-5553', '(555) 555-4444']
```

Catch multiple names.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# universal way for names
print re.findall(r'\w*, \w+', data)  # CHANGE: findall
```

Results.

```text
['Liff, Kenneth', 'Teacher, Submarine', 'McFarland, Arthur', 'Teacher, Submarine', 'Arthur, King', 'King, Camelot', 'sterberg, Gustav', 'Governor, Norrbotten', ', Tim', 'Enchanter, Killer', 'Carson, Ryan', 'CEO, Submarine', 'Lord, Gallifrey', 'Exampleson, Exampleme', 'Obama, Barack', 'President, United', 'Chalks, Andrew', 'Teacher, Submarine', 'Vader, Darth', 'lord, Galactic']
```

## Recap

- `match`.
- `search`.
- Escape characters (previous section).
- Repetitions (see above).
- `findall`.

# Sets -- Target Search

Catch patterns. We only need unique characters even when a word contains repetitive characters.

- `[aple]`, search for 'apple'.
- `[a-z]`, search for any lowercase letters.
- `[^2]`, search for anything that is not 2.
- `.`, stands for any possible character.

For finding email addresses, search better 'cures' on email adresses. Search for email address regex or email address regular expressions on Stack Overflow, Quora, etc.

We can also try.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# find emails
print re.findall(r'[-\w\d+.]+@[-\w\d.]+', data) # CHANGE
```

Results.

```text
['kenneth@submarine.com', 'arty@submarine.com', 'king_arthur@camelot.co.uk', 'governor@norrbotten.co.se', 'tim@killerrabbit.com', 'ryan@submarine.com', 'doctor+companion@tardis.co.uk', 'me@example.com', 'president.44@us.gov', 'andrew@submarine.com', 'darth-vader@empire.gov']
```

Retrieve 'submarine'. All characters are unique. The set should be 'submarine'.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# set [submarine] should catch 'submarine'
# add word boundaries, at least once, ignore lower or upper cases
print re.findall(r'\b[submarine]+\b', data, re.IGNORECASE) # CHANGE
```

Results.

```text
['submarine', 'Submarine', 'submarine', 'Submarine', 'se', 'submarine', 'Submarine', 'me', 'us', 'submarine', 'Submarine']
```

However, we also collect shorter strings ('se', 'me', 'us', 'Maria') with characters from [submarine]. If we wanted to limit the search to 'submarine' only.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# always 9 letters
print re.findall(r'\b[submarine]{9}\b', data, re.IGNORECASE) # CHANGE
```

Results.

```text
['submarine', 'Submarine', 'submarine', 'Submarine', 'submarine', 'Submarine', 'submarine', 'Submarine']
```

## Recap

- `match`.
- `search`.
- Escape characters (previous section).
- Repetitions (previous section).
- `findall`.
    - `re.IGNORECASE`.

# Boundaries -- Smart Search

- `'''`, add a multiline string.
- `\b@`, word boundary `@`.
- `\b `, word boundary ` `.
- `^`, ignore.
- `\t`, tab character.
- `.`, any character.

Find emails with word boundaries, spaces, words, explicit spaces (without using VERBOSE!!!), at least once for any number of characters, ignore tabs, and ignore newlines.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# multiline strings
print re.findall(r'''
	\b@[-\w\d.]* # First a word boundary, an @, and then any number of characters
	[^gov\t] # Ignore 1+ instances of the letters 'g', 'o' or 'v' and a tab
	\b # Another word boundary
''', data, re.VERBOSE|re.I)
```

Results.

```text
['@submarine.com', '@submarine.com', '@camelot.co.uk', '@norrbotten.co.se', '@killerrabbit.com', '@submarine.com', '@tardis.co.uk', '@example.com', '@us.', '@submarine.com', '@empire.']
```

We left off a few details in the email addresses. 

Retrieve the names and workplaces.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# name and place of work
print re.findall(r'''
	\b[-\w]*, # Find a word boundary, 1+ hyphens or characters, and a comma
	\s  # Find 1 whitespace
	[-\w ]+ # 1+ hyphens and characters and explicit spaces
	[^\t\n] # Ignore tabs and newlines
''', data, re.X)
```

Results.

```text
['Liff, Kenneth', 'Teacher, Submarine', 'McFarland, Arthur', 'Teacher, Submarine', 'Arthur, King', 'King, Camelot', 'sterberg, Gustav', 'Governor, Norrbotten', 'Enchanter, Killer Rabbit Cave', 'Carson, Ryan', 'CEO, Submarine', 'Lord, Gallifrey', 'Exampleson, Exampleme', 'Example, Example Co.', 'Obama, Barack', 'President, United States of America', 'Chalks, Andrew', 'Teacher, Submarine', 'Vader, Darth', 'lord, Galactic Empire']
```

The only problem: it did not catch `Ö` and `, Tim`. This is the problem with Windows: it is picky with some characters and requires extra coding to work around these problems. UNIX-based OS do not have these problems.

## Recap

- `match`.
- `search`.
- Escape characters (previous section).
- Repetitions (previous section).
- `findall`.
    - `re.IGNORECASE`.
    - `re.VERBOSE|re.I`, more readable, introduce whitespaces or comments.
    - `re.X`.

# Groups -- Subdivided Search

- last and first names.
- emails.
- phone numbers.
- job and workplaces.
- Twitter accounts.
- etc...

For that, we need parentheses.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# retrieve groups...
print re.findall(r'''
    ([-\w ]+,\s[-\w ]+)\t # last and first names
    ([-\w\d.+]+@[-\w\d.]+)\t # emails
    (\(?\d{3}\)?-?\s?\d{3}-\d{4})\t # phone numbers
    ([\w\s]+,\s[\w\s]+)\t # job and work place
    (@[\w\d]+)$ # Twitter account
''', data, re.X)
```

Results (a tupple).

```text
[('Liff, Kenneth', 'kenneth@submarine.com', '(555) 555-5555', 'Teacher, Submarine', '@kennethliff'), ('Carson, Ryan', 'ryan@submarine.com', '(555) 555-5543', 'CEO, Submarine', '@ryancarson'), ('Obama, Barack', 'president.44@us.gov', '555 555-5551', 'President, United States of America', '@potus44'), ('Chalks, Andrew', 'andrew@submarine.com', '(555) 555-5553', 'Teacher, Submarine', '@chalkers'), ('Vader, Darth', 'darth-vader@empire.gov', '(555) 555-4444', 'Sith lord, Galactic Empire', '@darthvader')]
```

The only problem: it did not catch `Ö` and `, Tim`. This is the problem with Windows: it is picky with some characters and requires extra coding to work around these problems. UNIX-based OS do not have these problems.

On the other hand, there are some details missing. We need to make the code more universal for the first and last names. The phone number should be optional, tabs are optional, without Twitter accounts, and tabs should become a new line instead.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# retrieve groups...
print re.findall(r'''
    ^([-\w ]*,\s[-\w ]+)\t # last and first names CHANGE
    ([-\w\d.+]+@[-\w\d.]+)\t # emails
    (\(?\d{3}\)?-?\s?\d{3}-\d{4})?\t # phone numbers CHANGE
    ([\w\s]+,\s[\w\s.]+)\t? # job and work place CHANGE
    (@[\w\d]+)?$ # Twitter account CHANGE
''', data, re.X|re.MULTILINE)
```

Results (a tupple). More.

```text
[('Liff, Kenneth', 'kenneth@submarine.com', '(555) 555-5555', 'Teacher, Submarine', '@kennethliff'), ('McFarland, Arthur', 'arty@submarine.com', '(555) 555-5555', 'Teacher, Submarine', ''), ('Carson, Ryan', 'ryan@submarine.com', '(555) 555-5543', 'CEO, Submarine\t', '@ryancarson'), ('Exampleson, Exampleme', 'me@example.com', '555-555-5552', 'Example, Example Co.\t', '@exemple'), ('Obama, Barack', 'president.44@us.gov', '555 555-5551', 'President, United States of America\t', '@potus44'), ('Chalks, Andrew', 'andrew@submarine.com', '(555) 555-5553', 'Teacher, Submarine\t', '@chalkers'), ('Vader, Darth', 'darth-vader@empire.gov', '(555) 555-4444', 'Sith lord, Galactic Empire\t', '@darthvader')]
```

The only problem: it did not catch `Ö` and `, Tim`. This is the problem with Windows: it is picky with some characters and requires extra coding to work around these problems. UNIX-based OS do not have these problems.

Turn the results into a **dictionary** with 'patterns' or `P<...>`.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# build a dictionary CHANGE ALL
line = re.search(r'''
    ^(?P<name>[-\w ]*,\s[-\w ]+)\t
    (?P<email>[-\w\d.+]+@[-\w\d.]+)\t
    (?P<phone>\(?\d{3}\)?-?\s?\d{3}-\d{4})?\t
    (?P<job>[\w\s]+,\s[\w\s.]+)\t?
    (?P<twitter>@[\w\d]+)?$
''', data, re.X|re.MULTILINE)

print "print line..."
print line
print "=" * 25
print "print line.group()..."
print line.group()
print "=" * 25
print "print line.groupdict()..."
print line.groupdict()
```

Results (a tupple). Say we remove the first line in the data...

```text
print line...
<_sre.SRE_Match object at 0x00000000021DDDD8>
=========================
print line.group()...
McFarland, Arthur	arty@submarine.com	(555) 555-5555	Teacher, Submarine
=========================
print line.groupdict()...
{'phone': '(555) 555-5555', 'job': 'Teacher, Submarine', 'name': 'McFarland, Arthur', 'twitter': None, 'email': 'arty@submarine.com'}
```

## Recap

- `match`.
- `search`.
- Escape characters (previous section).
- Repetitions (previous section).
- `findall`.
    - `re.IGNORECASE`.
    - `re.VERBOSE|re.I`.
    - `re.X`.
    - `re.X|re.MULTILINE` or `re.X|re.M`.

# Compile & Build Dictionaries -- Operationalized Search

Compile a pattern into an object. Replace `findall` or `search` with `compile`. Remove `data` to make a generic function to process any data.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# build a dictionary CHANGE
line = re.compile(r'''
    ^(?P<name>[-\w ]*,\s[-\w ]+)\t
    (?P<email>[-\w\d.+]+@[-\w\d.]+)\t
    (?P<phone>\(?\d{3}\)?-?\s?\d{3}-\d{4})?\t
    (?P<job>[\w\s]+,\s[\w\s.]+)\t?
    (?P<twitter>@[\w\d]+)?$
''', re.X|re.MULTILINE)

print re.search(line, data).groupdict() # CHANGE
```

Results (a tupple). Say we remove the first line in the data...

```text
{'phone': '(555) 555-5555', 'job': 'Teacher, Submarine', 'name': 'McFarland, Arthur', 'twitter': None, 'email': 'arty@submarine.com'}
```

Alternatively.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# build a dictionary CHANGE
line = re.compile(r'''
    ^(?P<name>[-\w ]*,\s[-\w ]+)\t
    (?P<email>[-\w\d.+]+@[-\w\d.]+)\t
    (?P<phone>\(?\d{3}\)?-?\s?\d{3}-\d{4})?\t
    (?P<job>[\w\s]+,\s[\w\s.]+)\t?
    (?P<twitter>@[\w\d]+)?$
''', re.X|re.MULTILINE)

print line.search(data).groupdict() # CHANGE
```

Compiling not only does it make the script universal (ready for any data), but it also make the execution faster. It becomes easier to compile the script into an executable.

We want all the lines, but a specific group (say 'names').

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# build a dictionary
line = re.compile(r'''
    ^(?P<name>[-\w ]*,\s[-\w ]+)\t
    (?P<email>[-\w\d.+]+@[-\w\d.]+)\t
    (?P<phone>\(?\d{3}\)?-?\s?\d{3}-\d{4})?\t
    (?P<job>[\w\s]+,\s[\w\s.]+)\t?
    (?P<twitter>@[\w\d]+)?$
''', re.X|re.MULTILINE)

for match in line.finditer(data): # CHANGE
	print match.group('name')
```

Results (a tupple).

```text
Liff, Kenneth
McFarland, Arthur
Carson, Ryan
Exampleson, Exampleme
Obama, Barack
Chalks, Andrew
Vader, Darth
```

The only problem: it did not catch `Ö` and `, Tim`. This is the problem with Windows: it is picky with some characters and requires extra coding to work around these problems. UNIX-based OS do not have these problems.

Create sub-patterns and extract specific groups.

```python
import re

# read the file
name_file = open("names.txt")
data = name_file.read()

# data is now in memory
name_file.close()

# build a dictionary
line = re.compile(r'''
    ^(?P<name>(?P<last>[-\w ]*),\s(?P<first>[-\w ]+))\t # CHANGE
    (?P<email>[-\w\d.+]+@[-\w\d.]+)\t
    (?P<phone>\(?\d{3}\)?-?\s?\d{3}-\d{4})?\t
    (?P<job>[\w\s]+,\s[\w\s.]+)\t?
    (?P<twitter>@[\w\d]+)?$
''', re.X|re.MULTILINE)

for match in line.finditer(data):
	print '{first} {last} <{email}>'.format(**match.groupdict())
```

Results

```text
Kenneth Liff <kenneth@submarine.com>
Arthur McFarland <arty@submarine.com>
Ryan Carson <ryan@submarine.com>
Exampleme Exampleson <me@example.com>
Barack Obama <president.44@us.gov>
Andrew Chalks <andrew@submarine.com>
Darth Vader <darth-vader@empire.gov>
```

The only problem: it did not catch `Ö` and `, Tim`. This is the problem with Windows: it is picky with some characters and requires extra coding to work around these problems. UNIX-based OS do not have these problems.

## Recap

- `match`.
- `search`.
- Escape characters (previous section).
- Repetitions (previous section).
- `findall`.
    - `re.IGNORECASE`.
    - `re.VERBOSE|re.I`.
    - `re.X`.
    - `re.X|re.MULTILINE` or `re.X|re.M`.
- `compile`.
- `groupdict`.
- `line.finditer`.
- `match.group`.
- `match.groupdict`.
