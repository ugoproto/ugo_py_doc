---

[TOC]

---

**Foreword**

Notes. Python 2. Consult the [Hitchicker's Guide to Python](http://docs.python-guide.org/en/latest/).

---

## 1, PEP20

PEP : Python Enhancement Proposals. In the Python shell, type `import this`. We get the following 'easter egg'.

```python
The Zen of Python, by Tim Peters

Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```

The 'easter egg' is a poem. A poem of best practices.

- Explicit is better than implicit. Don't add numbers to strings.
- Readability counts. Use the grammar of PEP8. Add comments.
- Special cases aren't special enough to break the rules. The`len` function for all. A function applies to all. A method applied to some. Find the built-in function before coding new functions.
- The code should be pleasant and easy to read.

## 2, PEP8

PEP : Python Enhancement Proposals. Improves the look of the code. Here are a few principles:

- Import at the top and separate.
- 1 space between parameters and variables.
- 4-space indentation.
- Two-line space between independent functions.
- 1 space between operators.
- 2-line space between class and other objects.
- Classes are capitalized.
- Functions and methods are not capitalized.
- 1-line space between class functions.
- Constant variable in uppercase.
- Variable in lowercase and long names.

Here is an example where to apply these principles.

```python
import sys # import at the top and separate
import random


def foo_Bar(arg1, arg2, arg3, arg4): # 1 space between parameters and variables
	return arg1, arg2, arg3, arg4 # 4-space indentation
	
	
def bar(*args): # 2-line space between independent functions
	# bad spacing
	return 2 + 2 # 1 space between operators
	

class Submarine: # 2-line space between class and other objects; classes are capitalized
	def one(self): # functions and methods are not capitalized
		return 1
		
	def two(self): # 1-line space between class functions
		return 2

CONSTANT = 10 # constant variable in uppercase
		
alpha, beta, charlie, delta = foo_Bar( # variable in lowercase and long names
 "a long string", # one practical way to stack things
 "a longer string",
 "yet another long string", 
 "and other crazy string")

one = 1 # 1 space
three = 3
fourteen = 14

print alpha
print fourteen

print Submarine().two() # class.method
```

## 3, PEP Diagnoses with `flake8` & `pylint`

The modules can be integrated with IDE and text editors (VIM, Emacs, gedit, Notepad++, etc.).

**`flake8`**

- Install `flake8` with pip.
- Run a script with `flake8`: `python flake8 <script.py>`. 
- Instead of running the code, `flake8` runs a diagnosis and returns the results. 
- The results suggest improvement to the look of the script. 
- It shows a list: the line number, the character positions, and the improvement. We can then go back to the script, improve it and rerun `flake8`.

**`pylint`**

- Install `pylint` with pip.
- Run a script with `flake8`: `python pylint script.py`. 

`pylint` runs a diagnosis and returns a report about the script.

## 4, Help & Docstrings

- In the shell, for any command '<cmd>', type `help(<cmd>)` to get a definition.
- Type `dir(<cmd>)` to get the attributes from the Python glossary.
- A docstrings is an enhancement to the `help` glossary.

Without docstrings.

```python
def does_something(arg):
	if isinstance(arg, (int, float)):
		return arg + 10
	elif isinstance(arg, str):
		return str * 3
	else:
		raise TypeError("does_something only takes ints, floats, and strings")
```

- We should never read a code to figure out what it does! 
- Add docstrings: """   """ on 1 line
- Add docstrings: several lines (see below).

```python
def does_better(arg):
	"""Takes one argument and does something based on type.
	If arg is a string, returns arg * 3;
	If arg is an int or float, returns arg + 10
	"""
	if isinstance(arg, (int, float)):
		return arg + 10
	elif isinstance(arg, str):
		return str * 3
	else:
		raise TypeError("does_something only takes ints, floats, and strings")
```

- In the shell, type `help(docstrings.does_better)` to print the function's docstring.

## 5, `pdb` Debugs Scripts

Go inside the code.

The next following script is bugged.

```python
# a list
my_list = [5, 2, 1, True, "abcdefg", 3, False, 4]

# modify the list
del my_list[3]
del my_list[4]
del my_list[6]
print my_list
```

We run the code and we get an error. The sloppy fix would be to add print statements.

```python
# a list
my_list = [5, 2, 1, True, "abcdefg", 3, False, 4]

# modify the list
del my_list[3] # ADD
print my_list
del my_list[4] # ADD
print my_list
del my_list[6] # ADD
print my_list
```

Instead, use the Python debugger: `pdb.set_trace()` in the code.

```python
import pdb # ADD


# a list
my_list = [5, 2, 1, True, "abcdefg", 3, False, 4]

pdb.set_trace() # ADD
del my_list[3]
del my_list[4]
del my_list[6]
print my_list
```

When we run the script, the routine stops at each line following the `set_trace()` function. We get a `(Pdb)` prompt. We can type in the variable name as if we were in the shell to see what is going on.

We punch `n` or `next` to step forward in the script. `pdb` pinpoint the trouble areas. In the current case, we want to delete a value at index 6 when the list had been reduced to 5 values (it is impossible to delete what is inexistant!).

```python
import pdb


# a list
my_list = [5, 2, 1, True, "abcdefg", 3, False, 4]

pdb.set_trace()
del my_list[3] # [5, 2, 1, "abcdefg", 3, False, 4]
del my_list[4] # [5, 2, 1, 3, False, 4]
del my_list[6] # [5, 2, 1, 3, 4]
print my_list
```

An alternative way.

```python
# a list
my_list = [5, 2, 1, True, "abcdefg", 3, False, 4]

import pdb; pdb.set_trace() # ADD
del my_list[3] # [5, 2, 1, "abcdefg", 3, False, 4]
del my_list[4] # [5, 2, 1, 3, False, 4]
del my_list[4] # [5, 2, 1, 3, 4]
print my_list
```

Change the script and rerun it.

```python
import pdb


# a list
my_list = [5, 2, 1, True, "abcdefg", 3, False, 4]

pdb.set_trace()
del my_list[3] # [5, 2, 1, "abcdefg", 3, False, 4]
del my_list[4] # [5, 2, 1, 3, False, 4]
del my_list[4] # [5, 2, 1, 3, 4]
print my_list
```

Once the script is debugged, delete the `pdb` stuff (it is a temporary measure).

```python
# a list
my_list = [5, 2, 1, True, "abcdefg", 3, False, 4]

del my_list[3] # [5, 2, 1, "abcdefg", 3, False, 4]
del my_list[4] # [5, 2, 1, 3, False, 4]
del my_list[4] # [5, 2, 1, 3, 4]
print my_list
```