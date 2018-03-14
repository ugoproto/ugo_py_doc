<!--
---

[TOC]
-->
---

**Foreword**

Notes. Python 3. From Le Livre du Zéro, Simple IT, 2011.

---

# Shebang Line

<sub>shebang, top, file, environment, language, kernel, python2, python 2, python3, python 3, utf, utf8, utf-8</sub>

Other names: sha-bang, hashbang, pound-bang, hash-pling.
 
**At the top of scripts**

- In Windows, Python 2:
    - `#! python`.
- Windows, Python 3:
    - `#! python 3`.
- UNIX, Python 2:
    - `#!/usr/bin/env python`.
- UNIX, Python 3:
    - `#!/usr/bin/env python 3`.
- Add:
    - `# -*coding: utf-8 -*-`.
    - `# -*coding: latin-1 -*-`.

**Launch a script**

- In Windows, Python 2:
    - `python script.py`.
    - `py script.py`.
    - `py -2 script.py`.
    - `py -2.7 script.py`.
- In UNIX, Python 2:
    - `python script.py`.
- In Windows, Python 3:
    - `py -3 script.py`.
    - `py -3.5 script.py`.
- In UNIX, Python 3:
    - `python3 script.py`.
    
**Launch the shell/bash**

- The shell, Python 2:
    - `python`.
    - `py -2`.
    - `py -2.7`.
- The bash, Python 2:
    - `python`.
    - `python2`.
- The shell, Python 3:
    - `py -3`.
    - `py -3.5`.
- The bash, Python 3:
    - `python3`.

# Chapter 8, Exceptions

Basic.

- `try:` block.
- `except` errors.
- `else:`.
- `finally:`.
- `assert` tests and conditions.
- `raise` an exception.

# Chapter 10, Strings

Basic.

A `"string"`.

- `str()` function.
- `upper()` and `lower()` methods; upper/lower characters.
- `capitalize()` method; first-letter upper character.
- `left()`, `right()`, `center()` methods.
- `strip()`, `lstrip()`, `rstrip()` methods; remove white space.
- `format()` method.
- `count()` method.
- `find()` method.
- `replace()` method.
- `[:]` to subset a string.
- `while` loop on a string.

# Chapter 11, Lists and Tuples 1

Basic.

<sub>delete, length, size</sub>

Lists are mutable; can add or remove elements from a list; can change the order of elements.

A `[list]`.

- `insert()` method.
- `append()` method.
- `extends()` method.
- `del()` function; delete an indexed element.
- `remove()` method; remove an occurrence.
- `len()` function; length.
- `for` loop, `in` a list.
- `enumerate()` function; return the index and elements.
 
Tuples are immutable; cannot be modified.

`(tuple)`.

# Chapter 12, Lists and Tuples 2

Basic.

<sub>flexible, function, flexibility, parameter</sub>

With lists, functions can have an undetermined number of parameters (very flexible!):

- `def my_function(*parameter):`.
- `def my_function(a, b, *parameter):`.

Strings and lists. Create, split, loop through a sequence. Even in a list of list.

- `split()` method.
- `join()` method.
- `for` loop, `in` a list.

Find the `type()` of a variable (integer, float, boolean, etc.)

# Chapter 13, Dictionaries

Basic.

<sub>dictionary, flexible, function, flexibility, parameter</sub>

Dictionaries are mutable; you can add or remove elements from a dictionary; order of elements is unimportant.

One-entry dictionary: `{'key': 'value'}`.

With dictionaries, functions can have an undetermined number of parameters (very flexible!):

- `def my_function(**parameter):`.
- `def my_function(a, b, **parameter):`.

Combine lists and dictionaries in a function with an undetermined number of parameters:

- `def my_function(*, parameter, **parameter):`.
- `def my_function(a, b, *parameter, **parameter):`.

- `del dict['key']` function; delete.
- `pop()` method; pop out an element.
- `for` loop, `in` a dictionary.
- `in dict.keys()` method; extract the dictionary `dict` in order.
- `in dict.values()` method; extract the values from dictionary `dict`.
- `in dict.items()` method to extract the keys and values from dictionary `dict`.

# Chapter 14, Files

Basic.

`os` module. Perform bash, shell operations such as opening, closing, reading, and writing files. Manage relative and absolute path. In UNIX and Windows.

- `open()` method.
- `close()` method.
- `read()` method.
- `write()` method.

- `with/as` method; create aliases.

`pickle` module. Record objects in a file and retrieve them.

- `Pickler()` method.

# Chapter 17, Classes and docstrings

Basic.

<sub>class, instance, self</sub>

`docstring` module. Under a `Class`, a docstring documents the class. Under `def __init__():`, a docstring documents the attributes. Under `def function():`, a docstring documents the use of the function or class method, under `variable`, a docstring documents the use of the variable.

`object.__doc__` method; accesses the docstring.

`__all__` function; displays the list of public names (of objects).

`pydoc` module. Displays information about an object with the `help(object)` function.

`dir(object)` function; returns an object's parameters (all the attributes, methods, functions).

`object.__dict__` method; returns an object's attributes.

`object.__dict__["att_a"] = "att_b"` changes an object's attribute.

# Chapter 18, (Class) Properties

Basic.

<sub>instance, constructor</sub>

More about the `def __init__():` constructor.

# Chapter 19, Special Methods

Basic.

<sub>mathematics, display results</sub>

- `def __repr__(self):` modifies the way an object is displayed when called.
- `def __str__(self):` method modifies the way an object is displayed when printed.

- `def __getattr__():` defines a message when an inexistent object's attributes is called (like a `try` block) vs the built-in `object.__dict__`
- `def __setattr__():` does the same when an object's attribute is modified vs the built-in `object.__dict__["att_a"] = "att_b"`
- `def __delattr__():` does the same when an object's attribute is deleted.
- `def __hasattr__():` returns true or false if the attribute exists.

- `def __getitem__():`, `def __setitem__():`, and `def __delitem__():` all define what to do when we write, respectively: `object[index]`, `object[index] = value`, and `del object[index]`.

- `object.__contains__` checks out if a list contains a specific element; like `in`

- `object.__len__()` shows the size of an object.

- `object.__add__(4)` is equivalent to `object + 4`; 
- `def __add():` as well.
- `object.__sub__()` or `-`.
- `__mul__` or `*`.
- `__truediv__` or `/`.
- `__floordiv__` or `//`.
- `__mod__` or `%`.
- `__pow__` or `**`.
- `__radd__`, `__iadd__`, etc.
- `def __eq__():` or `==`.
- `__ne__` or `!=`.
- `__gt__` or `>`.
- `__ge__` or `>=`.
- `__lt__` or `<`.
- `__le__` or `<=`.

- `pickle` module. Record objects in a file and retrieve them.

- `__getstate__` method.
- `__setstate__` method.

# Chapter 20, Heritage

Basic.

<sub>except</sub>

Class heritage transfers all attributes, parameters and methods from a class to a subclass.

- `issubclass` verifies (true or false) if a class is a subclass of another class.
- `isinstance` verifies if an object comes from a class.

A subclass can inherit from two or more classes (multiple heritage).

More exceptions in a `try` block, `except`, heritage, `AttributeError`, `Exception`, `BaseException`, and resolution. 

Exceptions are classes with hierarchy.

# Chapter 21, The for Loop Again

Basic.

Related to the `for` loop and how to dig deeper into the iterator with `__iter__` and `__next__`.

Iterator can also skip items in a list: iterate from 1 to 5, them jump to 10 and go on. A sort of conditional `break`. For that, we must generate intervals with `yield`.

# Chapter 23, Decorators

Advanced!

<sub>simplify code</sub>

A decorator simplifies:

```python
def function(...):
	...
...
function = decorator (function)
```
With:

```python
@decorator
def function(...):
	...
```

There are decorators without parameters, with parameters, applied to classes; chained together.

Use:

1. Limit a class instance to only one instance  or one object (a `singleton`).
2. Add more control on the type of data going into functions. 

# Chapter 24, Metaclasses

Advanced!

`__init__` initiates an object with attributes, but does not create the object itself. 

It is done by coding a new instance or with `__new__`. The method is useful to create immutable objects that cannot be modified.

Create dynamic classes with `type`.

# Chapter 25, Regular Expressions

Basic.

<sub>regex, string, search, beginning, end, replace,  occurrence, character, class, group, number, numbered group, name, named</sub>

`re` module.

# Chapter 26, Time

Basic.

<sub>date, time, year, month, day, hour, minute, second, time zone, timezone, time delta, timedelta, time stamp, timestamp, format</sub>

`time` module and `datetime` module.

# Chapter 27, System Programming

Basic.

<sub>input, output, stdin, stdout, open, close, read, write, directory, file</sub>

`sys` module and `os` module. Access system variables and control the operating system.

`signal` module. Read process signals sent to programs (such as stopping and exiting). 

Access and control the OS console, enter CLI arguments, program actions usually done with the mouse and the keyboard. 

`system` module, related to `os`.

- `os.system('ls')` on Linux.
- `os.system('dir')` on Windows.

For example:

```python
import os

cmd = os.popen('ls')

cmd
cmd.read()
```

# Chapter 28, Maths

Basic.

`math` module.

Enables new methods in arithmetics, trigonometry, rounding: `pow()`, `sqrt()`, `exp()`, `fabs()`, `radians()`, `degrees()`, `ceil()`, `floor()`, `trunc()`, etc

`fractions` module.

`Fraction()`, `from_float()`, etc.

`random` module.

`random()`, `randrange()`, `randint()`, `choice()`, etc.

# Chapter 29, Password Management

Web framework.

`getpass` module.

Receive a password, cypher a password, etc.

# Chapter 30, Network

Web framework.

<sub>tcp, protocol, client, server, connection, http, port, socket, connect,  </sub>

`socket` module and `select` module.

# Chapter 31, Tkinter

Software, application.

<sub>gui, graphic, interface, window, button, interactive, box, toggle, widget, labels, square, checkbox, list, command</sub>

`Tkinter` module.

# Chapter 33, Distribute Scripts and Programs

Basic.

Method 1: Executable File

`cx_freeze` creates a standalone executable file. `cx_Freeze` is portable (Windows, Linux, Mac OS X), compatible with Py -2 and Py -3, simple, fast, flexible.

Download, install, use the `cxfreeze` script

Alternative: `py2exe` (Windows only).

Method 2: Setup File

The traditional way of distributing a code and a more powerful approach.


# Chapter 34, PEP

Basic.

- PEP 20: The Zen of Python.
- PEP 8: coding conventions.
	- identation, tabulation, line length, line spacing, encoding, importing, spacing, commenting, naming, coding comparisons.
- PEP 257: documentation and docstrings.

# Chapter 35, More...

Basic.

- References.
- Wiki.
- PEP.
- Documentation.
- Basic library
- Additional libraries.
	- graphical interfaces: Tk, PyQT, PyGTK, wx Python.
	- web framworks: Django, CherryPy.
	- networks: Twisted.
- Index.
