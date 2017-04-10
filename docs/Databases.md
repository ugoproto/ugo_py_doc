# Databases

**Foreword**

Notes. Python 3. Consult the [Hitchicker's Guide to Python](http://docs.python-guide.org/en/latest/).

Although we work with SQLite, most concepts are applicable to MySQL and PostgreSQL.

-----

[TOC]

-----

## 1, SQLite3

Follow the tutorial on [TutorialPoint](https://www.tutorialspoint.com). Especially the [Quick Guide](https://www.tutorialspoint.com/sqlite/sqlite_quick_guide.htm) for installation, basic commands, syntax, comments, SQL statement, data type, affinity type, boolean, date & time, creating a db, a table, dropping a table, querying, operators, expressions, and clauses. Each topic has also a dedicated section such as unions, joins, truncated table, etc.

- Install.
    - Download from the [SQLite website](http://www.sqlite.org/download.html).
    - Follow the Quick Guide or Find instruction online.
    - On Windows, the db is on C:\sqlite and this is where we store the db.
    - On Linux, the db is in the root directory(/usr/lib/...), but the db are/can be stored in the Personal folder (or in a directory of choice; for example, in a new subdirectory under Documents).

## 2, SQLite3 CLI

**Basics**

- In the shell/bash:
    - `sqlite3 test.db`, create and open a db (show the prompt); the db is located in SQLite's directory.
- Basic commands inside a db.
    - `.help`.
    - `.databases`, show all databases.
    - `create table first (a int, b string);`, create a table with two fields.
    - `.schema`, show the last commands.
    - `.tables`, show all tables in the db.
    - `insert into first (a, b) values (1, "hello");`, load the table.
    - `select * from first;`, extract all values from the table.
    - `.quit` or `.exit`.
    - `drop table first;`, delete a table.
    - Delete a db by deleting the file in the directory.
- Intermediate commands.
    - `.mode insert`, change the view (insertions to build the db).
    - `.dump`, dump on screen.
    - `.output .\Documents\sqlite3Files.sql`, create a folder in a file (Windows).
    - `.output ./Documents/sqlite3Files.sql`, create a folder in a file (UNIX-based).
        - `.dump`, dump into the above. VERY USEFUL for recreating a db/table.
    - `.output stdout`, to the screen.
    - `.mode column`, change the view (flat table with fixed width).
        - `.width 15 20`, define the width by column.
            - `.output ./Documents/sqlite3Files/table.sql`, prepare the dump.
            - `select * from table;`, extract.
            - `.output stdout`, dump.
    - `.mode line`, change the view (long list without commas).
            - Idem.
    - `.mode html`, change the view (html formats ready to be dumbed).
            - `.output ./Documents/sqlite3Files/table.html`, prepare the dump.
            - `select * from table;`, extract.
            - `.output stdout`, dump.
    - `.mode tabs`, change the view (flat table separated by tabs).
            - `.output ./Documents/sqlite3Files/table.tsv`, prepare the dump.
            - `select * from table;`, extract.
            - `.output stdout`, dump.
    - `.mode csv`, change the view (flat table separated by commas or semi-colons).
            - `.separator ;`, change the separator.
            - `.output ./Documents/sqlite3Files/table.csv`, prepare the dump.
            - `select * from table;`, extract.
            - `.output stdout`, dump.
    - `.mode tcs`, change the view (flat table with double-quotes).
    - `.headers on`, show the headers.
    - `.show`, show the (above) parameters (and change them).
    - `.prompt 'sqlite3> '`, change the prompt.
    - `.read <path>`, repopulate the db with the above.

**Advanced**

There are plenty of resources on SQLite: books, online documents, online tutorials, etc. We can learn how to:

- Build a db, tables.
- Query a db, create, alter, select, order by, limit, offset, update, delete, and other functions.
- Joins and Triggers.

## 3, SQL DB GUI, Administation, and Management Tools

With db managers, we can create scripts to automate operations.

- SQLite is free, open source, and cross-platform.
    - DB Browser for SQLite, free, for all OS.
    - Add-ons to browsers such as the SQLite Managers for Firefox.
- MySQL is free, open source, and cross-platform.
    - MySQL Workbench, free, for all OS.
        - Database Design & Modeling, SQL Development (replacing MySQL Query Browser), and Database Administration (replacing MySQL Administrator). MySQL features: SQL editor, SQL code completion, SQL code formatter, SQL Syntax highlighting, server start/stop, server status/health, server logs, server/replication configuration, user management, session management, and much more.
    - Web-based managers...
- PostgreSQL is free, open source, also cross-platform.
    - pgAdminIII.
    - Web-based managers...
- SQL in general.
    - DB Browser, free, for all OS.
    - phpMyAdmin, free, for all OS.
    - Toad, free, for Windows.
    - HeidiSQL, free, for Windows.
    - Web-based managers...

## 4, Excel Data and SQLite

1. Option 1

- Export data (save as) from Excel in a.csv file.
- Import the .csv into SQLite.
    - In can be done with a manager such as DB Browser for SQLite.
    - It can be done with a web-based manager such as SQLite Managers for Firefox.
    - Adjust the general and the field parameters.
    - Create a primary key.
    - Populate a table with the .csv file.
    
2. Option 2

- Connect Excel with SQLite with an add-ons.
    - There are add-ons or add-ins that can execute SQL queries in a cell and dumb the results in other cells.
    - Excellic, Microsoft SQL Server Data Mining, SaveToDB, Database Connection Wizard, Publish Wizard, etc.

## 5, R and Python with SQL

- R can import data from / export data to relational db using specialized packages such as `DBI`, `RSQLite`, `RMySQL`, `RPostgreSQL`, etc.
- Python libraries are: `python-sql`, `sqlalchemy`, `records`, `peewee`, etc.
    - `pip install <library>`.    
    
## 6, The Chinook SQLite Sample Database

Learn, practice and test commands with a fake database. 

- Download the [database](http://chinookdatabase.codeplex.com/).
- Consult the [diagram](SQLite Sample Database
http://www.sqlitetutorial.net/sqlite-sample-database/).
    - We can also download the database and diagrams.
    
## 7, Using a Python ORM: `peewee`

1.1

We can run queries with SQL or use a Python wrapper: `peewee`. It is a lightweight Object Relational Mapper (ORM). `peewee` works with SQLite, MySQL, and PostgreSQL.

Install it with pip.

We can manage our db with Python scripts.

1.2

In `peewee`, models are Python classes. Everything in the db is an object: tables, rows, columns, entries, etc.

We create a new db, `students.db`, with Python. We connect to the db and create two fields with their SQL parameters. We run the script in the terminal.

```python
from peewee import *

db = SqliteDatabase('C:\sqlite\students.db')


class Student(Model): # use a singular name convention
    username = CharField(max_length=255, unique=True) # varchar, unique value, no duplicates
    points = IntegerField(default=0) # if not supplies, it inputs 0 by default

    class Meta: # a class inside a class (meta-class)
        database = db

if __name__ == '__main__': # for running the script directly, not import it
    db.connect()
    db.create_tables([Student], safe=True) # safe is a mandatory convention
```

We get no result in the terminal: good sign. Check out the db to see the results.

The script run on Windows in Python 2. In Python 3, we would need minor adjustments; they are documented along the way. In addition, in UNIX-based OS, we would need two extra lines at the top of the script.

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
```

Or.

```python
#!/usr/bin/env python 3
# -*- coding: utf-8 -*-
```

1.3

Five useful methods:

- `.create()`, add a new record to the table.
- `.select()`, pick rows out of the table.
- `.save()`, update an existing row in a table.
- `.get()`, fetch a single record from a table.
- `.delete_instance()`, delete a row from a table.

Improve the script.

```python
from peewee import *

db = SqliteDatabase('C:\sqlite\students.db')


class Student(Model):
    username = CharField(max_length=255, unique=True)
    points = IntegerField(default=0)

    class Meta:
        database = db


# ADD a dictionary
students = [
	{'username': 'kennethliff',
	'points': 4888},
	{'username': 'chalkers',
	'points': 11912},
	{'username': 'joykesten2',
	'points': 7363},
	{'username': 'craigsrob',
	'points': 4079},
	{'username': 'adammcfarland',
	'points': 14717}
]    


def add_students(): # ADD a function
	for student in students:
        Student.create(username=student['username'],
                        points=student['points']) 


if __name__ == '__main__':
    db.connect()
    db.create_tables([Student], safe=True)
    add_students() # ADD
```

We can run the script one, but not twice because of the `unique=True` in the `class Student(Model):`. We get an `IntegrityError` in the terminal. We need to add a `try` block.

```python
from peewee import *

db = SqliteDatabase('C:\sqlite\students.db')


class Student(Model):
    username = CharField(max_length=255, unique=True)
    points = IntegerField(default=0)

    class Meta:
        database = db


students = [
	{'username': 'kennethliff',
	'points': 4888},
	{'username': 'chalkers',
	'points': 11912},
	{'username': 'joykesten2',
	'points': 7363},
	{'username': 'craigsrob',
	'points': 4079},
	{'username': 'adammcfarland',
	'points': 14717}
]    


def add_students(): # CHANGE the function
	for student in students:
		try:
			Student.create(username=student['username'],
							points=student['points'])
		except IntegrityError:
			student_record = Student.get(username=student['username'])
			student_record.points = student['points']
			student_record.save()
            
   
if __name__ == '__main__':
    db.connect()
    db.create_tables([Student], safe=True)
    add_students()
```

We get no result in the terminal: good sign. We can run the script at will. We can check out the results in the db.

Add a function to select the top students, order them in descending order (high to low) and get them.

```python
from peewee import *

db = SqliteDatabase('C:\sqlite\students.db')


class Student(Model):
    username = CharField(max_length=255, unique=True)
    points = IntegerField(default=0)

    class Meta:
        database = db


students = [
	{'username': 'kennethliff',
	'points': 4888},
	{'username': 'chalkers',
	'points': 11912},
	{'username': 'joykesten2',
	'points': 7363},
	{'username': 'craigsrob',
	'points': 4079},
	{'username': 'adammcfarland',
	'points': 14717}
]    


def add_students():
	for student in students:
		try:
			Student.create(username=student['username'],
							points=student['points'])
		except IntegrityError:
			student_record = Student.get(username=student['username'])
			student_record.points = student['points']
			student_record.save()

            
def	top_student():
	student = Student.select().order_by(Student.points.desc()).get() # ADD
	return student            
   
if __name__ == '__main__':
    db.connect()
    db.create_tables([Student], safe=True)
    add_students()
    print("Our top student right now is: {0.username}.".format(top_student())) # ADD
```

This time, we should get a result in the terminal.

```text
Our top student right now is: adammcfarland.
```

Change the points in the dictionary and rerun the script.

```python
from peewee import *

db = SqliteDatabase('C:\sqlite\students.db')


class Student(Model):
    username = CharField(max_length=255, unique=True)
    points = IntegerField(default=0)

    class Meta:
        database = db


students = [
	{'username': 'kennethliff',
	'points': 14718}, # CHANGE, make it the top student
	{'username': 'chalkers',
	'points': 11912},
	{'username': 'joykesten2',
	'points': 7363},
	{'username': 'craigsrob',
	'points': 4079},
	{'username': 'adammcfarland',
	'points': 14717}
]    


def add_students():
	for student in students:
		try:
			Student.create(username=student['username'],
							points=student['points'])
		except IntegrityError:
			student_record = Student.get(username=student['username'])
			student_record.points = student['points']
			student_record.save()

            
def	top_student():
	student = Student.select().order_by(Student.points.desc()).get()
	return student            
   
if __name__ == '__main__':
    db.connect()
    db.create_tables([Student], safe=True)
    add_students()
    print("Our top student right now is: {0.username}.".format(top_student()))
```

Results in the terminal.

```text
Our top student right now is: kennethliff.
```

**Recap:**

- `.create()`, add a new record to the table.
- `.select()`, pick rows out of the table.
- `.get()`, fetch a single record from a table.

Create, Read, Ipdate, and Delete is knows as CRUD; the backbone of ORM.

2.1

Now, we build a diary app using a SQLite db. Such an application can be integrated to a web framework (like Flask). We must be able to load data and extract them. 

The more general use could be a log book: we can write stuff and retrieve it. We can classify the entries and search for a specific word. Etc.

We start with a skeleton, bare functions and docstrings.

```python
from peewee import *

db = SqliteDatabase('C:\sqlite\diary.db')


class Entry(Model):
    # content
    # timestamp

    class Meta:
        database = db


def menu_loop():
    """Show the menu."""


def add_entry():
    """Add an entry."""


def view_entries():
    """View previous entries."""


def delete_entry(entry):
    """Delete an entry."""


if __name__ == '__main__': # for running the script directly, not import it
    menu_loop()
```

2.2

Let's add some flesh to the skeleton. Add the the `datetime` library and a new function to initialize the diary.

```python
import datetime # ADD
from peewee import *

db = SqliteDatabase('C:\sqlite\diary.db')


class Entry(Model): # CHANGE
    content = TextField() # content: TextField ia more flexible, holds any type of data; contrary to CharField, a varchar with a maximum length
    timestamp = DateTimeField(default=datetime.datetime.now) # timestamp; now does take parentheses

    class Meta:
        database = db


def initialize(): # ADD
    """Create the database and the table if they don't exist."""
    db.connect()
    db.create_tables([Entry], safe=True)
        
        
def menu_loop():
    """Show the menu."""


def add_entry():
    """Add an entry."""


def view_entries():
    """View previous entries."""


def delete_entry(entry):
    """Delete an entry."""


if __name__ == '__main__': # for running the script directly, not import it
    initialize() # INSERT
    menu_loop()
```

We get no result in the terminal: good sign. We can check out the results in the db.

2.3

We add a menu using a dictionary (we need the `OrderedDict` library).

```python
from collections import OrderedDict # ADD
import datetime
from peewee import *

db = SqliteDatabase('C:\sqlite\diary.db')


class Entry(Model):
    content = TextField()
    timestamp = DateTimeField(default=datetime.datetime.now)

    class Meta:
        database = db


def initialize():
    """Create the database and the table if they don't exist."""
    db.connect()
    db.create_tables([Entry], safe=True)
        
        
def menu_loop():
    """Show the menu."""
    choice = None # new variable with a default value
    
    while choice != 'q': # ADD
        print("Enter 'q' to quit.") # starting message
        for key, value in menu.items(): # loop through the dictionary
            print('{}) {}'.format(key, value.__doc__)) # value from the menu variables furthur down in the script; __doc__ is the docstrings
        choice = raw_input('Action: ').lower().strip() # lowercase, remove white spaces

        if choice in menu: # check if the selection is in the menu
            menu[choice]() # execute the choice

def add_entry():
    """Add an entry."""


def view_entries():
    """View previous entries."""


def delete_entry(entry):
    """Delete an entry."""


menu = OrderedDict([ # ADD tuple
    ('a', add_entry),
    ('v', view_entries),
])


if __name__ == '__main__':
    initialize()
    menu_loop()
```

This is coded in Python 2. In Python 3, we would replace `raw_input` by `input`; a major difference between the two versions.

The result is dynamic. We can input `Actions` in the terminal and the script continues to run until we quit with `q`. We cannot do much since the functions are still empty (`def add_entry():` and `def view_entries():`). The following is a snapshot.

```text
Enter 'q' to quit.
a) Add an entry.
v) View previous entries.
Actions:
```

3.1

Add the `sys` library. We want to enter data (load the db).

```python
from collections import OrderedDict
import datetime
import sys # ADD
from peewee import *

db = SqliteDatabase('C:\sqlite\diary.db')


class Entry(Model):
    content = TextField()
    timestamp = DateTimeField(default=datetime.datetime.now)

    class Meta:
        database = db


def initialize():
    """Create the database and the table if they don't exist."""
    db.connect()
    db.create_tables([Entry], safe=True)
        
        
def menu_loop():
    """Show the menu."""
    choice = None
    
    while choice != 'q':
        print("Enter 'q' to quit.")
        for key, value in menu.items():
            print('{}) {}'.format(key, value.__doc__))
        choice = raw_input('Action: ').lower().strip()

        if choice in menu:
            menu[choice]()

            
def add_entry(): # IMPROVE
    """Add an entry."""
    print("Enter your entry. Press ctrl+z when finished.")
    data = sys.stdin.read().strip()

    if data:
        if raw_input('Save entry? [Yn] ').lower() != 'n':
            Entry.create(content=data)
            print("Saved successfully!")
    

def view_entries():
    """View previous entries."""


def delete_entry(entry):
    """Delete an entry."""


menu = OrderedDict([
    ('a', add_entry),
    ('v', view_entries),
])


if __name__ == '__main__':
    initialize()
    menu_loop()
```

The result is dynamic.

To the question `Enter your entry. Press ctrl+d when finished.`, write `Working with databases. I enjoy my day.`. Press enter, then press ctrl+z, then enter in Windows, ctrl+d in UNIX-based OS (for End-of-File key sequence). Save it (with a `y` input). Repeat. This time, do not save it (`n`). Check out the results in the database.

`raw_input` in Python 2 vs. `input` in Python 3. In Python 2, we can print with `print " "` or `print(" ")`. The later is only possible in Python 3.

3.2

We now want to read the data (query the db). We also want to search throught the entries. In SQL, we would code: `SELECT * FROM entry WHERE content LIKE '%search_query$' ORDER BY timestamp DESC;`.

```python
from collections import OrderedDict
import datetime
import sys
from peewee import *

db = SqliteDatabase('C:\sqlite\diary.db')


class Entry(Model):
    content = TextField()
    timestamp = DateTimeField(default=datetime.datetime.now)

    class Meta:
        database = db


def initialize():
    """Create the database and the table if they don't exist."""
    db.connect()
    db.create_tables([Entry], safe=True)
        
        
def menu_loop():
    """Show the menu."""
    choice = None
    
    while choice != 'q':
        print("Enter 'q' to quit.")
        for key, value in menu.items():
            print('{}) {}'.format(key, value.__doc__))
        choice = raw_input('Action: ').lower().strip()

        if choice in menu:
            menu[choice]()

            
def add_entry():
    """Add an entry."""
    print("Enter your entry. Press ctrl+z when finished.")
    data = sys.stdin.read().strip()

    if data:
        if raw_input('Save entry? [Yn] ').lower() != 'n':
            Entry.create(content=data)
            print("Saved successfully!")
    

def view_entries(search_query=None): # IMPROVE
    """View previous entries."""
    entries = Entry.select().order_by(Entry.timestamp.desc()) # sort them
    if search_query:
        entries = entries.where(Entry.content.contains(search_query))

    for entry in entries:
        timestamp = entry.timestamp.strftime('%A %B %d, %Y %I:%M%p') # day name, month, date, year, hour (12h), minute, am/pm
        print(timestamp)
        print('='*len(timestamp)) # print the number of characters in the timestamp
        print(entry.content)
        print('n) next entry')
        print('q) return to main menu')

        next_action = raw_input('Action: [Nq] ').lower().strip()
        if next_action == 'q':
            break


def search_entries():
    """Search entries for a string."""
    view_entries(raw_input('Search query: '))


def delete_entry(entry):
    """Delete an entry."""


menu = OrderedDict([
    ('a', add_entry),
    ('v', view_entries),
    ('s', search_entries), # ADD
])


if __name__ == '__main__':
    initialize()
    menu_loop()
```

The result is dynamic. Try entering stuff, save it. Back to the menu, read the entry. We should get a date, a line of `=` and the entry. Quit and go back to the menu. Try search for a word. It should find a single word among all the entry and pull out the entry where the word appears.

3.3

Complete the last function: `def delete_entry(entry):`.


```python
from collections import OrderedDict
import datetime
import sys
from peewee import *

db = SqliteDatabase('C:\sqlite\diary.db')


class Entry(Model):
    content = TextField()
    timestamp = DateTimeField(default=datetime.datetime.now)

    class Meta:
        database = db


def initialize():
    """Create the database and the table if they don't exist."""
    db.connect()
    db.create_tables([Entry], safe=True)
        
        
def menu_loop():
    """Show the menu."""
    choice = None
    
    while choice != 'q':
        print("Enter 'q' to quit.")
        for key, value in menu.items():
            print('{}) {}'.format(key, value.__doc__))
        choice = raw_input('Action: ').lower().strip()

        if choice in menu:
            menu[choice]()

            
def add_entry():
    """Add an entry."""
    print("Enter your entry. Press ctrl+z when finished.")
    data = sys.stdin.read().strip()

    if data:
        if raw_input('Save entry? [Yn] ').lower() != 'n':
            Entry.create(content=data)
            print("Saved successfully!")
    

def view_entries(search_query=None):
    """View previous entries."""
    entries = Entry.select().order_by(Entry.timestamp.desc())
    if search_query:
        entries = entries.where(Entry.content.contains(search_query))

    for entry in entries:
        timestamp = entry.timestamp.strftime('%A %B %d, %Y %I:%M%p')
        print(timestamp)
        print('='*len(timestamp))
        print(entry.content)
        print('n) next entry')
        print('d) delete entry') # ADD
        print('q) return to main menu')

        next_action = raw_input('Action: [Ndq] ').lower().strip()
        if next_action == 'q':
            break
        elif next_action == 'd': # ADD
            delete_entry(entry)


def search_entries():
    """Search entries for a string."""
    view_entries(raw_input('Search query: '))


def delete_entry(entry): # IMPROVE
    """Delete an entry."""
    if raw_input("Are you sure? [yN] ").lower() == 'y':
        entry.delete_instance()
        print("Entry deleted!")


menu = OrderedDict([
    ('a', add_entry),
    ('v', view_entries),
    ('s', search_entries),
])


if __name__ == '__main__':
    initialize()
    menu_loop()
```

The result is dynamic. Enter something. Save it. View it. Delete it (the last entry). Confirm it. Go back to the main menu. View the previous entries. The last entry was deleted and we see the previous entry.

3.4

We can polish up the final result. We need to ventilate the onscreen printouts by cleaning the screen here and there. On Windows, we clear the screen with `cls`; on UNIX-based OS, with `clear`.

Here is the final product. It's not perfect, but it works.

```python
from collections import OrderedDict
import datetime
import os # ADD
import sys
from peewee import *

db = SqliteDatabase('C:\sqlite\diary.db')


class Entry(Model):
    content = TextField()
    timestamp = DateTimeField(default=datetime.datetime.now)

    class Meta:
        database = db


def initialize():
    """Create the database and the table if they don't exist."""
    db.connect()
    db.create_tables([Entry], safe=True)


def clear(): # ADD
    os.system('cls' if os.name == 'nt' else 'clear') # ADD; cls for Windows, clear for Linux or Mac OS X
    

def menu_loop():
    """Show the menu."""
    choice = None
    
    while choice != 'q':
        clear()
        print("Enter 'q' to quit.")
        for key, value in menu.items():
            print('{}) {}'.format(key, value.__doc__))
        choice = raw_input('Action: ').lower().strip()

        if choice in menu:
            clear()
            menu[choice]()

            
def add_entry():
    """Add an entry."""
    print("Enter your entry. Press ctrl+z when finished.")
    data = sys.stdin.read().strip()

    if data:
        if raw_input('Save entry? [Yn] ').lower() != 'n':
            Entry.create(content=data)
            print("Saved successfully!")
    

def view_entries(search_query=None):
    """View previous entries."""
    entries = Entry.select().order_by(Entry.timestamp.desc())
    if search_query:
        entries = entries.where(Entry.content.contains(search_query))

    for entry in entries:
        timestamp = entry.timestamp.strftime('%A %B %d, %Y %I:%M%p')
        clear()
        print(timestamp)
        print('='*len(timestamp))
        print(entry.content)
        print('\n\n'+'='*len(timestamp)) # ADD
        print('n) next entry')
        print('d) delete entry')
        print('q) return to main menu')

        next_action = raw_input('Action: [Ndq] ').lower().strip()
        if next_action == 'q':
            break
        elif next_action == 'd':
            delete_entry(entry)


def search_entries():
    """Search entries for a string."""
    view_entries(raw_input('Search query: '))


def delete_entry(entry):
    """Delete an entry."""
    if raw_input("Are you sure? [yN] ").lower() == 'y':
        entry.delete_instance()
        print("Entry deleted!")


menu = OrderedDict([
    ('a', add_entry),
    ('v', view_entries),
    ('s', search_entries),
])


if __name__ == '__main__':
    initialize()
    menu_loop()
```






















