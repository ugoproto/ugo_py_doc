# Automate the Boring Stuff with Python

**Foreword**

Notes. Python 3. From No Starch Press, 2015. Creative Commons. More at:

- Online at [automatetheboringstuff.com](https://automatetheboringstuff.com/)
- More at [Invent with Python.com](http://inventwithpython.com/hacking/chapters/)
	- [Books](http://inventwithpython.com/index.html):
		- Develop video games!
		- Make games with graphics!
		- Encrypt messages and hack ciphers!

-----

[TOC]

-----

## Chapter 2, Flow Control

<sub>boolean, comparison, operator, flow control, condition, conditional, loop</sub>

- `True`, `False`.
- `and`, `or`, `not`.
- `==`, `!=`, `<`, `>`, etc.
- `if`, `else`, `elif`
- Loops: `while`, `for` with `in`, `range`.
- `break`, `continue`.
- `import random, sys, os, math`.
- `random.randint`.
- `from random import *`.
- `sys.exit()`.

## Chapter 3, Functions

<sub>global, local, variable, scope</sub>

Exception handling with `try:` and `except`.

## Chapter 4, Lists (and Tuples)

<sub>data type, index, sublist, subset, slice,  change, concatenate, concatenation, tuple, convert, tuple to list</sub>

- `len()` function; length.
- `in` and `not in` operators.
- `+=`, `-=`, `*=`, `/=`, `%=` augmented assignments.
- `index()` method; extract the position of an element.
- `append()` method.
- `insert()` method.
- `remove()` method.
- `sort()` method.
- `copy` module and `copy()` method.
- `deepcopy()` method; for inner list or a list of lists (ensure the key exists).

## Chapter 5, Dictionaries and Structuring Data

<sub>loop</sub>

Dictionaries are not indexed and ordered like lists.

- `keys()` method; extract keys.
- `values()` method; extract values.
- `items()` method; extract both.
- `get()` method; check out both.
- `in` and `not in` operators. 
- `setdefault()` method, check out a key and set value to a key.

Pretty print with the `pprint()` and `pformat()` functions.

Nested dictionaries and lists.

## Chapter 6, Manipulating Strings

Escape character: `\`: `\'`, `\"`, `\t`, `\n`, `\\`.

Raw strings: `print(r'That is Carol')`.

Triple quotes:

```python
print('''Dear Alice,
bla-bla-bla
cheers''')

print("""Dear Alice,
bla-bla-bla
cheers""")
```

Comment: `#`.
Multiline comments: `""" """`.

- Slice, subset with `[:]`.
- `in` and `not in` operators.
- `lower()` method.
- `upper()` method.
- `capitalize()` method.
- `is` method; check if x is part of y.
- `islower()` method.
- `isupper()` method.
- `isalpha()` method; check letters, not blank.
- `isalnum()` method; check letters and numbers, and not blank.
- `isdecimal()` method; check numeric characters and not blank.
- `isspace()` method; check spaces, tabs and new lines and not blank.
- `istitle()` method; check if it begins with an uppercase letter followed with lowercase letters.
- `startwith()` method; check if a string begins with a string of characters.
- `endwith()` method; idem.
- `join()` method; concatenate.
- `split()` method.
- `rjust()` method; justify.
- `ljust()` method justify.
- `center()` method.
- `strip()` method; remove white space.
- `rstrip()` method; ; remove white space to the right.
- `lstrip()` method; remove white space to the left.

`pyperclip` module.

The `pyperclip.pyclip` function send text to and receive text from the clipboard:

In addition:

```python
import pyperclip

pyperclip.copy('Hello world!')
pyperclip.paste()
```

## Chapter 7, Pattern Matching and Regular Expressions

<sub>patterns of text, with, without regular expression, regex, object, match, matching, group, grouping, pipe, question mark, star, ?, *, plus, +, curly bracket, {, }, character class, digit, numeric, letter, underscore, space, tab, newline, caret, ^, dollar sign, $, wildcard, dot, ., dotstar, newline, symbols, case-sensitive, case-insensitive</sub>

`re` module.

- `re.compile()` method; find a single occurrence.
- `re.findall()` method; find all occurrences.
- `sub()` method; substitute.
- `re.IGNORECASE`; ignore capitalization with the `compile()` method.
- `re.DOTALL`; ignore dots with the `re.compile()` method.
- `re.VERBOSE`; write comment with the `re.compile()` method.

## Chapter 8, Reading and Writing Files

<sub>file, file path, filename</sub>

`os` module.

- A relative path: `..\eggs\spam.txt`, `.\fizz\spam.txt`.
- An absolute path: `C:\bacon\fizz\spam.txt`.
- `os.getcwd()` or `os.chdir()` functions; extract the current working directory.
- `os.makedir()`function; create a new folder.

`os.path` module. 

Handle absolute and relative paths. Find file sizes and folder contents. Check path validity.

Windows: backslash or `\`:

```python
import os
os.path.join('usr', 'bin', 'spam')
```

Yields:

```python
'usr\\bin\\spam'
```

UNIX: forwardslash or `/`:

```python
import os
os.path.join('usr', 'bin', 'spam')
```

Yields:

```python
'usr/bin/spam'
```

Read and write files:

- `os.path.open()` function.
- `os.path.read()` method.
- `os.path.readline()` method.
- `os.path.write()` method.
- `os.path.close()` method.

`shelve` module.

Handle binary files.

`pprint` module. 

Pretty printing:

- `pprint.pprint()`.
- `pprint.pformat()`.

## Chapter 9, Organizing Files

<sub>pdf, every sub-folder, folder, foldername, subfolder, filename, file, remove, zero, change titles, compress, decompress, zip, unzip</sub>

`shutil` module. 

Copy, move, rename, and delete files and folders. `shutil.rmtree()` function; delete file and folder.

`os` module. 

Delete, empty, remove files and folders, and change the path. `os.walk()` method; walk the tree directory.

`send2trash` module. 

Delete files and folders, but much safer.

`zipfile` module. 

Compress and uncompress. Read the content of compressed and zipped files.

- `zipfile.extracall()`; method  extracts all the files and folders from a zip file.
- `write()` method; create a zip file.

## Chapter 10, Debugging

Handle errors with `try` and `except`.

Raise exceptions with a `raise` statement and the `Exception()` function.

`traceback` module. 

Discover what and how an error happens and obtain it as a string with the `traceback.format_exc()` method. 

An assertion is a sanity check performed with an `assert` statement. 

`logging` module. 

Display log messages as the program runs. Log to a file. Debug a code. Enable and disable logging. Enable an IDLE debugger.

Set a `breakpoint` to check out potential bugs.

## Chapter 11, Web Scraping

<sub>html</sub>

`webbrowser` module.

Open a browser to a specific webpage (in conjunction with the `sys` module). 

Use:

- Get a street address from the command line to the clipboard.
- Go to a Google Maps page.
- Read command line arguments from `sys.argv`.
- Read the clipboard content.
- Open all links on a page in separate tabs.
- Open the browser to the url for local weather.
- Open several social network sites.

`requests` module.

Download files and webpages; similar to opening, reading, writing, closing files and folders. 

- Simpler than the `urllib2` module.
- Can check out errors.
- Save the downloaded files.

HTML crash course!

`bs4` module (BeautifulSoup).

- `BeautifulSoup()` function; parses HTML. 
- `select()` method;  find an element. 
- Get data from an element's attributes.

Use:

- Search Google.
- Retrieve search results.
- Open tabs for each results.
- Read the command line arguments from `sys.argv`.
- Fetch results with the `requests` module.
- Find the links.
- Download all images, videos, files, etc.
- Back up an entire site by following all of its links.
- Copy all the messages off a web forum.
- Duplicate the catalogue of items for sale on an online store.

`selenium` module.

Launches and controls a web browser. Fill and submit forms. Simulate mouse clicks. Find elements on a page. Click on a page. Send special keys.

Combining modules :

- Command line emailer.
- Image site downloader.
- Link verification.

## Chapter 12, Excel Spreadsheets

`openpyxl` module.

Read Excel documents. Open Excel documents. Get sheets from a workbook. Get cells from the sheets. Convert letters and numbers. Get rows and columns from sheets. Write results to a file.

Use:

- Compare data across multiple rows in a spreadsheet.
- Open multiple files and compare data.
- Check blank rows or invalid data in any cells.
- Read data and use it as the input for Python programs.
- Write Excel Documents.
- Create and save Excel documents.
- Create and remove sheets.
- Write values to cells.
- Update a spreadsheet.
- Read data from one spreadsheet and write it to parts of other spreadsheets.
- Read data from websites, text files, or the clipboard and write it to a spreadsheet.
- Clean up data, regular expressions.
- Set the font style, objects, formulas.
- Adjust rows and columns.
- Set row height and column width.
- Merge and unmerge cells.
- Freeze panes.
- Create charts.
- Insert blank rows.
- Convert text files to spreadsheets, vice-versa.

## Chapter 13, PDF and Word Documents

`PyPDF2` module.

Extract text from a PDF. Decrypt a PDF. Create PDF. Copy pages, rotate pages, overlay pages from a PDF. Add a logo, a timestamp, a watermark to a PDF.

Use:

- Combine pages from many PDF.
- Cut out specific pages.
- Reorder pages.
- Create a PDF from only those pages that have some specific text.

`python-docx` module.

Read word documents. Get the full text from a .docs file. Style paragraphs. Create word documents with nondefault styles. Write word documents. Add headings, lines, page breaks, and pictures. 

Use:

- PDF Paranoia or encrypting a bunch of files.
- Custom invitations in Word.
- Brute-force PDF password breaker.

## Chapter 14, CSV Files and JSON Data

`csv` module.

Read, open CSV. Split the file. Print CSV. Loop within a file or through many files. Write CSV. Change delimiters and lineterminators. Remove the header.

Use:

- Compare data between different rows in a CSV file or between multiple CSV files.
- Copy specific data from a CSV file to an Excel file; vice-versa.
- Check for invalid data or formatting mistakes in CSV files and alert the user.
- Read data from CSV file as input for Python programs.
- Excel to CSV to Excel converter (in conjunction with the `openpyxl` module).

`json` module.

Alike web scraping. API. Read,  load, write, dump data.

Use:

- Fetch weather from a website.
- Collect weather forecasts for several campsites or hiking trails.
- Schedule a program to regularly check weather and send your a frost alert.
- Pull weather data from multiple sites to show all at once, or calculate and show the average of multiple weather predictions.

## Chapter 15, Time, Scheduling Tasks, and Launching Programs

`time` module.

Read the system clock for the current time. Pause a program (sleep). Round numbers.

Use:

- Track how much time spent on tasks with a stopwatch.
- Record track times or lap times.
- Build a program that launches other programs on a schedule by using the `subprocess` and `threading` modules.
- Create a timesheet app that records when you enter data, and use the current time to clock them in or out.
- Add a feature to a program to display the elapsed time since a process started (in conjunction with the `requests` module).
- Check how long a program has been running and offer the user a chance to cancel tasks.

`datetime` module.

Compute time and date delta. Retrieve a specific moment. Add a timestamp. Add pauses to a routine. Convert datetime object to strings. Convert strings to datetime objects.   

Use:

- Multithreading; modify a program to use a function. Create and start threads (see above).
- Pass command line arguments.
- Task scheduler.
- Open websites (time event).
- Run Python scripts (time event).
- Open files (time event).
- Create a countdown program.
- Schedule downloader (time event).

## Chapter 16, Sending Email and Text Messages

<sub>http, smtp, mail, imap</sub>

`smtplib` module.

Connect to an SMTP server. Log in. Search for emails. Send a message. Encrypt emails. Retrieve and delete emails. Disconnect from the SMTP server.

`imapclient` module.

Connect to an IMAP server. Log in. Search for emails. Fetch an email and mark it as read. Get email addresses from a raw message. Get the body from a raw message. Delete emails. Disconnect from the IMAP server.

Use:

- Send members dues reminders.
- Send text messages.
- Random emailer.
- 'Umbrella' reminder (in conjunction with weather forecasts and the `requests` module).
- Auto-unsubscriber.

`twilio` module.

Send text messages, SMS.

## Chapter 17, Manipulating Images

Color and RGBA crash course!

`PIL` module.

Manipulate images with Pillow. Work with the image data type. Crop, copy, paste an image. Multiply images tiles. Resize, rotate, flip an image. Change pixels. Draw on images (points, lines, rectangles, ellipses, polygons, text). 

Use:

- Loop through a folder of images.
- Image batch processing: resizing, cropping, copying and pasting, rotating, etc.
- Adding a logo to several images.
- Identify the photo folders.
- Create custom cards with custom invitations in Word (see chapter 13).

## Chapter 18, Controlling the Keyboard and Mouse with GUI Automation 

<sub>virtual keystrokes, mouse clicks</sub>

`pyautogui` module and dependencies based of the OS in use.

Shutdown the computer. Log out from a session. Pauses, fail-safes. Control mouse movements and move the mouse. Get the mouse position and control the mouse. Control the keyboard. Send a string from the keyboard. Type in key name. Press and release buttons. Activate hotkey.

Use:

- Image recognition.
- Automatic form filler.
- Look busy!
- Instant messenger bot.
- Game-playing bot tutorial.

## Appendix A

- PIP.
- Installing modules.

## Appendix B

- Running programs.
- Shebang line.
- On Windows.
- On UNIX.

## Appendix C

Answers from questions: chapter 2 to 18.

## Additional Content

- Download files used in the book.
- List of JSON API:
	- Twitter API.
	- Facebook Social Graph API.
	- Flickr.
	- YouTube.
	- OpenStreetMap.
	- Google Maps.
	- Imgur API.
	- 26 Weather APIs.
	- Rotten Tomatoes.
	- Reddit.
- List of programming practice sites. (programming problems you can try to practice your coding skills).
- List of web comics.
- Schedulers (operating system scheduling process).
- How to do PyCon or any tech conference.
