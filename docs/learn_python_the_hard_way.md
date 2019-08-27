---

**Foreword**

Notes, code snippets, and excerpts from the course. Python 2. From the book and website:

- [LPTHW](https://learnpythonthehardway.org/book/)

---

# Exercise 1, A Good First Program

<sub>shebang, begin, script</sub>

- This is a shebang (language): `# -*- coding: utf-8 -*-`.
- `#` is an octothorpe or pound or hash or mesh.
- Add a second line (Python version): `#! /usr/bin/env python 2`.

```python
# -*- coding: utf-8 -*-
#! /usr/bin/env python 2

print "Hello World!"
print "Hello Again"
print "I like typing this."
print "This is fun."
print 'Yay! Printing.'
print "I'd much rather you 'not'"
print 'I said do not touch this.'
print "testing2"
```

	Hello World!
	Hello Again
	I like typing this.
	This is fun.
	Yay! Printing.
	I'd much rather you 'not'
	I said do not touch this.
	testing2

## Shorcuts, Good to Know

- In the terminal, type `pydoc <python item>` to invoke the documentation on a python item (built-in functions, methods, objects, etc.).
- ++ctrl+c++ and/or ++ctrl+d++ break a loop.

# Exercise 3, Numbers and Math

<sub>print, format, calculate</sub>

```python
print "I will now count my chickens:"
```

	I will now count my chickens:

```python
print "Hens", 25 + 30 / 6
print "Roosters", 100 - 25 * 3 % 4

print "Now I will count the eggs:"

print 3 + 2 + 1 - 5 + 4 % 2 - 1 / 4 + 6
# copy 3 + 2 + 1 - 5 + 4 % 2 - 1 / 4 + 6 straight into the shell and run it
# you will get the result only (don't add print before the statement)
```

    Hens 30
    Roosters 97
    Now I will count the eggs:
    7

```python
print "Is it true that 3 + 2 < 5 - 7"
print 3 + 2 < 5 - 7
```

    Is it true that 3 + 2 < 5 - 7
    False

```python
print "What is 3 + 2?", 3 + 2
print "What is 5 - 7?", 5 - 7
```

    What is 3 + 2? 5
    What is 5 - 7? -2

```python
print "Oh, that's why it's False."
print "How about some more."
```

    Oh, that's why it's False.
    How about some more.

```python
print "Is it greater?", 5 > -2
print "Is it greater or equal?", 5 >= -2
print "Is it less or equal?", 5 <= -2
```

    Is it greater? True
    Is it greater or equal? True
    Is it less or equal? False

```python
print (1 + 1) # integer
```

    2

```python
print (1.0 + 1) # float
```

    2.0

# Exercise 4, Variables and Names

```python
cars = 100
space_in_a_car = 4.0 # float
drivers = 30
passengers = 90
cars_not_driven = cars - drivers
cars_driven = drivers
carpool_capacity = cars_driven * space_in_a_car
average_passengers_per_car = passengers / cars_driven

print "There are", cars, "cars available."
print "There are only", drivers, "drivers available."
print "There will be", cars_not_driven, "empty cars today."
print "We can transport", carpool_capacity, "people today."
print "We have", passengers, "to carpool today."
print "We need to put about", average_passengers_per_car, "in each cars."
```

    There are 100 cars available.
    There are only 30 drivers available.
    There will be 70 empty cars today.
    We can transport 120.0 people today.
    We have 90 to carpool today.
    We need to put about 3 in each cars.

- A constant variable, a variable that should never be altered, should be set in capital as `PI = 3.1416`.

# Exercise 5, More Variables and Printing

- Call a variable with:
	- `%r`; raw variable.
	- `%s`; string.
	- `%d`; digit.
- Make the choice depending on the variable type.
- However, if calling a 'string' (text, NLP), it must be done with `%s`; 'numbers' is done with `%r` and `%d` (possibly with `%s`). 
- The use and effects of the different calls is explained in Exercises 6 and 21.

```python
my_name = 'Zed A. Shaw'
my_age = 35 # not a lie
my_height = 74 # inches
my_weight = 180 # lbs
my_eyes = 'Blue'
my_teeth = 'White'
my_hair = 'Brown'

print "Let's talk about %s." % my_name
```

    Let's talk about Zed A. Shaw.

```python
# does the same thing
print "He's %d years old." %my_age
print "He's", my_age,"years old."
print "He will be", my_age + 1,"years old next year."
```

    He's 35 years old.
    He's 35 years old.
    He will be 36 years old next year.
 
```python
print "He's %d inches tall." % my_height
print "He's %d pounds heavy" % my_weight
print "Actually that's not too heavy."
print "He's got %s eyes and %s hair." % (my_eyes, my_hair)
print "His teeth are usually %s depending on the coffee." % my_teeth
```

    He's 74 inches tall.
    He's 180 pounds heavy
    Actually that's not too heavy.
    He's got Blue eyes and Brown hair.
    His teeth are usually White depending on the coffee.

```python
# this line is tricky, try to get it exactly right
print "If I add %d, %d, and %d I get %d." % (
    my_age, my_height, my_weight, my_age + my_height + my_weight)
```

    If I add 35, 74, and 180 I get 289.
    

# Exercise 6, Strings and Text

<sub>concatenate</sub>

- `%s` and `%r` help when concatenating strings.
- `%r` does not coerce the variable into a format (`%s` string or `%d` digit).


```python
x = "There are %d types of people." % 10
binary = "binary"
do_not = "don't"

y = "Those who know %s and those who %s." % (binary, do_not) # assign strings or chains of strings to a variable

print x 
print y
```

    There are 10 types of people.
    Those who know binary and those who don't.

```python
print "I said: %r." % x
print "I also said: '%s'." % y
```

    I said: 'There are 10 types of people.'.
    I also said: 'Those who know binary and those who don't.'.

```python
hilarious = False
joke_evaluation = "Isn't that joke so funny?! %r"

print joke_evaluation % hilarious
```

    Isn't that joke so funny?! False

```python
# add two strings together, concatenate them
w = "This is the left side of..."
e = " a string with a right side."

# with Numpy, it would have added (mathematically speaking)
print w + e
```

    This is the left side of... a string with a right side.
    

# Exercise 15, Reading Files

- Before running this script, create a text file.
- Type `"Test file thing" > test.txt`.
- Then type `cat test.txt`.
- 'test.txt' is now saved along the other scripts.
- Run the script: `python ex15.py test.txt`
- With IPython, type: `%run ex15.py test.txt`
- Run the script without the extra argument `test.txt` to check the result.

```python
%run ex15.py test.txt
```

    Here's your file 'test.txt':
    Test file thing
    Type the filename again:
    > test.txt
    Here's your file 'test.txt' again:
    Test file thing

```python
%run ex15.py
```
    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    \\Learn Python the Hard Way\ex15.py in <module>()
          1 from sys import argv
          2 
    ----> 3 script, filename = argv
          4 
          5 # similarities
    

    ValueError: need more than 1 value to unpack

- Load the script in IPython with `%load` to study it (don't run it!).
- This type of script requires 'external' arguments when launched: `python ex15.py test.txt`
- In the script itself, always preceed the 'external' arguments, like `filename`, with `script` since your write `python ex15.py test.txt` or `python script argument` when you launch the script.

```python
# %load ex15.py
from sys import argv

script, filename = argv

# similarities between
# var = raw_input("string", digit, "prompt")
# var = open("string")

txt = open(filename) # reference to a file, not the file
print "Here's your file %r:" % filename
print txt.read()

print "Type the filename again:"
file_again = raw_input("> ")

text_again = open(file_again)
print "Here's your file %r again:" % file_again
print text_again.read()
```

- The script again (this time, a manual import or copy-paste).

```python
from sys import argv

# always preceed the arguments like 'filename' with 'script'
script, filename = argv

# similarities
# var = raw_input("string", digit, "prompt")
# var = open("string")

txt = open(filename) #reference to a file, not the file
print "Here's your file %r:" % filename
print txt.read()

print "Type the filename again:"
file_again = raw_input("> ")

text_again = open(file_again)
print "Here's your file %r again:" % file_again
print text_again.read()
```

- Now, use this alternative code instead.
- It does not require an external argument; the argument (`filename`) is in the script itself (it has become a variable).
- 'Internal' arguments are for functions (`def function(arg1, arg2):`); see Exercise 18.


```python
filename = "test.txt" # however, the code is limited to this file only

txt = open(filename) # reference to a file, not the file
print "Here's your file %r:" % filename
print txt.read()

print "Type the filename again:"
file_again = raw_input("> ")

text_again = open(file_again)
print text_again.read()
```

# Exercise 16, Reading and Writing Files

<sub>open, close, readlines, truncate</sub>

- `'w'`, write, `'r'`, read, `'a'`, append.
- `'w+'`, read-write, `'r+'`, read-write, `'a+'`, read-append.
- `'r'` being the default argument, it is facultative when writing `open('file', 'r')`.
- The other arguments are mandatory; without them in `open('file, 'w')`, you cannot write, truncate, append or replace.
- First, load the script in IPython by typing `%load ex16_1.py`; it then turn to  a comment `# %load ex16_1.py`.

```python
# %load ex16.py
from sys import argv

script, filename = argv

print "We're going to erase %r." % filename
print "If you don't want that, hit CTRL-C (^C)."
print "If you do want that, hit RETURN."

raw_input("?")

print "Opening the file..."
target = open(filename, 'w')

print "Truncating the file!"

target.truncate()

print "Now, I'm going to ask you  for three lines."

line1 = raw_input("line 1: ")
line2 = raw_input("line 2: ")
line3 = raw_input("line 3: ")

print "I'm going to write these to the file."

target.write(line1) # 'write' variable line1
target.write("\n") # add a new line
target.write(line2)
target.write("\n")
target.write(line3)
target.write("\n")

print "And finally, we close it."
target.close()
```

- Now, run the external file in IPython (it imports the code behind the scene).
- Careful: the script requires a second argument (`filename`).

```python
%run ex16.py text.txt
```

    We're going to erase 'text.txt'.
    If you don't want that, hit CTRL-C (^C).
    If you do want that, hit RETURN.
    ?
    Opening the file...
    Truncating the file!
    Now, I'm going to ask you  for three lines.
    line 1: Good morning.
    line 2: How are you?
    line 3: I wish you a good day.
    I'm going to write these to the file.
    And finally, we close it.
    
- Read the file.

```python
filename = 'text.txt'

target = open(filename, 'r')
print target.read()
target.close()
```

    Good morning.
    How are you?
    I wish you a good day.

- Now, truncate (empty, delete, erase, clear) the file, reopen it, and to read it.

```python
filename = 'text.txt'

target = open(filename, 'w')
print "Truncating the file!"
print "-" * 25
target.truncate()
target.close()

target = open(filename, 'r')
print target.read()
target.close()
```

```text
Truncating the file!
------------------------
    
```

# Exercise 17, More Files

<sub>length, len()</sub>

- `target.read()`; read the whole file (EOF).
- `target.read(10)`; read the amount of bytes between the parentheses (1 byte = 1 character).
- `target.readline()`; read one line character at a time; the first line or the file until the first `\n`.
- `target.readline(10)`; read 10 bytes of the first line, but never more than the first line.
- `readlines()`; read in the whole file at once and splits it by line (create a list).
- `xreadlines()`; read big files.
- First, load `script ex17_1.py` in IPython. This script needs two additional arguments.

```python
# %load ex17_1.py
from sys import argv
from os.path import exists # does the file exists, T or F?

script, from_file, to_file = argv

print "Copying from %s to %s" % (from_file, to_file)

in_file = open(from_file, 'r') # 'r' is facultative
indata = in_file.read() # read the content, store in memory

print "The input file is %d bytes long" % len(indata) # number of bytes in the file or length of 'indata'

print "Does the output file exist? %r" % exists(to_file) # if the second file hasn't been created, this row will yield a 'False'

# after you run this script, if you run it again, il will yield a 'True'
print "Ready, hit RETURN to continue, CTRL-C to abort."
raw_input("? ")

out_file = open(to_file, 'w')
out_file.write(indata)

print "Alright, all done."

out_file.close()
in_file.close()
```

```python
%run ex17_1.py text2.txt new.txt
```

    Copying from text2.txt to new.txt
    The input file is 49 bytes long
    Does the output file exist? True
    Ready, hit RETURN to continue, CTRL-C to abort.
    ? 
    Alright, all done.

```python
target = open("text2.txt")
print target.read()
target.close()
```

    Good morning.
    How are you?
    I wish you a good day.

```python
target = open("new.txt")
print target.read()
target.close()
```

    Good morning.
    How are you?
    I wish you a good day.

```python
# %load ex17_2.py
from sys import argv
from os.path import exists # does the file exists, T or F?

script, from_file, to_file = argv

# FIRST
in_file = open(from_file, 'r')
indata = in_file.read()

print "The input file is %d bytes long" % len(indata)

in_file.close()

print "-" * 25

# SECOND
checkfile = open(from_file, 'r')
print checkfile.readline() # read line 1, show
print checkfile.readline() # read line 2
print checkfile.readline() # read line 3

checkfile.close()

print "-" * 25

# THIRD
checkfile2 = open(from_file, 'r')
out_file = open(to_file, 'w')

indata = checkfile2.read()
out_file.write(indata)

print "Alright, all done."

checkfile2.close()
out_file.close()

print "-" * 25

# FOURTH

checkfile3 = open(to_file, 'r')

print checkfile3.read()

checkfile3.close()
```

```python
%run ex17_2.py text2.txt new2.txt
```

    The input file is 49 bytes long
    -------------------------
    Good morning.
    
    How are you?
    
    I wish you a good day.
    -------------------------
    Alright, all done.
    -------------------------
    Good morning.
    How are you?
    I wish you a good day.
    

# Exercise 18, Names, Variables, Code, Functions

<sub>argument, flexible, indefinite</sub>

- A function can have no, one or several arguments.
    - `def function():`.
    - `def function(one)`.
    - `def function(one, two, three)`.
- `*args` means indifinite number of arguments. 
- All the arguments are is a list ('args').

```python
# indefinite
def print_two(*args):
    
    arg1, arg2 = args
    print "arg1: %r, arg2: %r" % (arg1, arg2)

# two arguments
def print_two_again(arg1, arg2):
    
    print "arg1: %r, arg2: %r" % (arg1, arg2)

# one argument
def print_one(arg1):
    
    print "arg1: %r" % arg1

# no arguments
def print_none():
    
    print "I got nothin'."

# indefinite
def print_two_2(*args):
    
    print "args: %r" % (args,) # much more flexible    

# two arguments
def print_two_again_2(arg1, arg2, arg3):
    
    print "arg1: %r, arg2: %r, arg3: %r" % (arg1, arg2, arg3)    

# three arguments
def print_two_again_3(arg1, arg2, arg3):
    
    print "arg1: %r, arg2: %r, arg3: %r" % (arg1, arg2, arg3)
    print_two("Joe", "Frank") # call a function inside a function
```

- Run the functions.

```python
print_two("Zed", "Shaw")
print_two_again("Zed", "Shaw")
```

    arg1: 'Zed', arg2: 'Shaw'
    arg1: 'Zed', arg2: 'Shaw'

```python
print_one("First!")
print_none()
```

    arg1: 'First!'
    I got nothin'.

```python
print_two_2("Zed", "Shaw", "A", "B")
```

    args: ('Zed', 'Shaw', 'A', 'B')
 
```python
print_two_again_2("Zed", "Shaw", "C")
```

    arg1: 'Zed', arg2: 'Shaw', arg3: 'C'

```python
print_two_again_3("Zed", "Shaw", "C")
```

    arg1: 'Zed', arg2: 'Shaw', arg3: 'C'
    arg1: 'Joe', arg2: 'Frank'
    

# Exercise 19, Functions and Variables

- Give different names to functions and arguments not to get confuse.

```python
def cheese_and_crackers(cheese_count, boxes_of_crackers):
    
    print "You have %d cheeses!" % cheese_count
    print "You have %d boxes of crackers!" % boxes_of_crackers
    print "Man that's enough for a party!"
    print "Get a blanket. \n"
```

```python
print "1.We can just give the function numbers directly:"
cheese_and_crackers(20, 30)
```

    1.We can just give the function numbers directly:
    You have 20 cheeses!
    You have 30 boxes of crackers!
    Man that's enough for a party!
    Get a blanket. 

```python
print "2.Or, we can use variables from our script:"
amount_of_cheese = 10
amount_of_crackers = 50
cheese_and_crackers(amount_of_cheese, amount_of_crackers)
```

    2.Or, we can use variables from our script:
    You have 10 cheeses!
    You have 50 boxes of crackers!
    Man that's enough for a party!
    Get a blanket. 

```python
print "3.We can even do math inside too:"
cheese_and_crackers(10 + 20, 5 + 6)
```

    3.We can even do math inside too:
    You have 30 cheeses!
    You have 11 boxes of crackers!
    Man that's enough for a party!
    Get a blanket. 
 
```python
print "4.And we can combine the two, variables and math:"
cheese_and_crackers(amount_of_cheese + 100, amount_of_crackers + 1000)
```

    4.And we can combine the two, variables and math:
    You have 110 cheeses!
    You have 1050 boxes of crackers!
    Man that's enough for a party!
    Get a blanket. 

```python
print "5.Make a GUI."
print "Enter the amount of cheese:",
amount_of_cheese = int(raw_input())
amount_of_crackers = int(raw_input("Enter the amount of crackers: "))
cheese_and_crackers(amount_of_cheese, amount_of_crackers)
```

    5.Make a GUI.
    Enter the amount of cheese:2
    Enter the amount of crackers: 5
     You have 2 cheeses!
    You have 5 boxes of crackers!
    Man that's enough for a party!
    Get a blanket. 

# Exercise 20, Functions and Files

<sub>seek, move, file</sub>

```python
# %load ex20.py
from sys import argv

script, input_file = argv
# python ex20.py test.txt

def print_all(f): # f is the file
    
    print f.read() # read the file, reach the end
    
def rewind(f):
    
    f.seek(0) # move back to the initial position in the file
# 'seek' actively move in the file
    
def print_a_line(line_count, f):
    
    print line_count, f.readline() # print a line # and this line number in the file
    
    
current_file = open(input_file)

print "First, let's print the whole file:\n"

print_all(current_file) # launch function, f = current_file

print "-" * 25

print "Now let's rewind, kind of like a tape."

rewind(current_file) # launch function, f = current_file

print "-" * 25

print "Let's print three lines:"

current_line = 1 # load variable
print_a_line(current_line, current_file) # launch function
# set 'current_line' to 1

current_line = current_line + 1
# current_line += 1
print_a_line(current_line, current_file)
# 'current_line' grows to 2...

# current_line = current_line + 1
current_line += 1
print_a_line(current_line, current_file)
```

```python
%run ex20.py new2.txt
```

    First, let's print the whole file:
    
    Good morning.
    How are you?
    I wish you a good day.
    -------------------------
    Now let's rewind, kind of like a tape.
    -------------------------
    Let's print three lines:
    1 Good morning.
    
    2 How are you?
    
    3 I wish you a good day.
    

# Exercise 21, Functions Can Return Something or not...

<sub>integer, float, int, coerce, digit, string, raw</sub>

- `%r` for raw.
- `%d` for digit.
- `%s` for string.
- `int()` with `%d` = integer.
- `int()` with `%r` or `%s` = integer.
- `float()` with `%d` = integer.
- `float()`  with `%r` or `%s` = float.
- `%r` is a safer choice; see below.

```python
a = 10 # a digit
b = 10.1

print "%r" % a
print "%s" % a
print "%d" % a
print "%r" % b
print "%s" % b
print "%d" % b
```

    10
    10
    10
    10.1
    10.1
    10

```python
a = "10" # a string or str(10)

print "%r" % a
print "%s" % a
print "%d" % a
```

    '10'
    10

    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-34-71a6226dbd27> in <module>()
          2 print "%r" % a
          3 print "%s" % a
    ----> 4 print "%d" % a
    
    TypeError: %d format: a number is required, not str

```python
b = "10.1" # a string or str(10)

print "%r" % b
print "%s" % b
print "%d" % b
```

    '10.1'
    10.1
    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-33-18d4f3068fee> in <module>()
          2 print "%r" % b
          3 print "%s" % b
    ----> 4 print "%d" % b
  
    TypeError: %d format: a number is required, not str

```python
a = "10" # a string or str(10)
b = "10.1" # a string or str(10)

print "%r" * 1 % a
print "%s" * 1 % a
print "%r" * 1 % b
print "%s" * 1 % b
```

	'10'
	10
	'10.1'
	10.1
	
```python
a = "10" # a string or str(10)
b = "10.1" # a string or str(10)

print "%r" * 2 % a
print "%s" * 2 % a
print "%r" * 2 % b
print "%s" * 2 % b
```

    
    ---------------------------------------------------------------------------


    TypeError                                 Traceback (most recent call last)

    <ipython-input-34-18d4f3068fee> in <module>()
          1 a = "10"
          2 b = "10.1"
    ----> 3 print "%r" * 2 % a
          4 print "%s" * 2 % a
          5 print "%r" * 2 % b
  
    TypeError: not enough arguments for format string

```python
a = 10
b = 10.1
a = int(a)
b = int(b)
print "%r" % a
print "%s" % a
print "%d" % a
print "%r" % b
print "%s" % b
print "%d" % b
```

    10
    10
    10
    10
    10
    10

```python
a = 10
b = 10.1
a = float(a)
b = float(b)

print "%r" % a
print "%s" % a
print "%d" % a
print "%r" % b
print "%s" % b
print "%d" % b
```

    10.0
    10.0
    10
    10.1
    10.1
    10

```python
a = 1
b = 2.1

print a * b
print int(a) * int(b)
print float(a) * float(b)
print str(a) * 10
print str(b) * 10
print str(a) * str(b)
```

    2.1
    2
    2.1
    1111111111
    2.12.12.12.12.12.12.12.12.12.1
    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-52-57a5dd7c13d0> in <module>()
          7 print str(a) * 10
          8 print str(b) * 10
    ----> 9 print str(a) * str(b)

    TypeError: can't multiply sequence by non-int of type 'str'

```python
def add(a, b):
    
    print "ADDING %s + %s" % (a, b)
    return a + b  

def substract(a, b):
    
    print "SUBTRACTING %d - %d" % (a, b) # show the arguments
    return a - b # compute the arguments

def multiply(a, b):
    
    print "MULTIPLYING %d * %d" % (a, b)
    return a * b    

def divide(a, b):
    
    print "DIVIDING %d / %d" % (a, b)
    return a / b
```


```python
print "Let's do some math with just functions!"

aa = int(raw_input("Enter a (integer): ")) # to enter an integer
bb = float(raw_input("Enter b (float): ")) # to enter a float
age = add(aa, bb) # launch function add()
```

    Let's do some math with just functions!
    Enter a (integer): 1
    Enter b (float): 2.2
    ADDING 1 + 2.2

```python
print add(aa, bb)
```

    ADDING 1 + 2.2
    3.2
 
```python
height = substract(78, 4) # launch function substract()
weight = multiply(90, 2) # launch function multiply()
iq = divide(100, 2) # launch function divide()

print height
print weight
print iq
```

    SUBTRACTING 78 - 4
    MULTIPLYING 90 * 2
    DIVIDING 100 / 2
    74
    180
    50

```python
# Use the variable, previously loaded
print "Age: %d, Height: %d, Weight: %d, IQ: %d" % (age, height, weight, iq)
```

    Age: 3, Height: 74, Weight: 180, IQ: 50

```python
# A puzzle for the extra credit, type it in anyway.
print "Here is a puzzle."

what = add(age, substract(height, multiply(weight, divide(iq, 2)))) # launch functions one by one!!!

# Insert variable 'what' in the text
print "That becomes: ", what, "Can you do it by hand?"
```

    Here is a puzzle.
    DIVIDING 50 / 2
    MULTIPLYING 180 * 25
    SUBTRACTING 74 - 4500
    ADDING 3.2 + -4426
    That becomes:  -4422.8 Can you do it by hand?

# Exercise 23, Read Some Code

- Go to [GitHub](http://github.com/zedshaw/lamson):
- In the 'lamson' directory, take a script.
- Go through the script.
- Find projects on collaborative sites or depositories:
    - [bitbucket.org](https://bitbucket.org/).
    - [github.com](https://github.com/).
    - [launchpad.net](https://launchpad.net/).
    - [sourceforge.net](https://sourceforge.net/).

# Exercise 24, More Practice

- `\'` for an aposthrophy.
- `\t` for a tab.
- `\\` for a backslash.
- `\n` for a new line.


```python
print "Let's practice everything."

print 'You\'d need to know \'bout escapes with \\ that do \nnewlines and \ttabs.'
```

    Let's practice everything.
    You'd need to know 'bout escapes with \ that do 
    newlines and 	tabs.

```python
poem = """
\tThe lovely world
with logic so firmly planted
connot discern \n the needs of love
nor comprehend passion from intuition
and requires an explanation
\n\t\twhere there is none.
"""

print "----------------"
print poem
print "----------------"
```

    ----------------
    
    	The lovely world
    with logic so firmly planted
    connot discern 
     the needs of love
    nor comprehend passion from intuition
    and requires an explanation
    
    		where there is none.
    
    ----------------
 
```python
# variable 'five'
five = 10 -2 + 3 - 6

# use of variable 'five'
print "This should be five: %s" % five
```

    This should be five: 5
 
```python
# function with one argument
def secret_formula(started):
    
    jelly_beans = started * 500 # load variable with another
    jars = jelly_beans / 1000
    crates = jars / 100
    return jelly_beans, jars, crates


# variable; warning, this variable is modified further down
start_point = 10000

# redefine the results of a function (rename a variable)
# from this point, 'jelly_beans' becomes 'beans'
# and must be called so in any line of code
beans, jars, crates = secret_formula(start_point)

print "With a starting point of: %d" % start_point
# we apply 'bean'
print "We's have %d beans, %d jars, and %d crates." % (beans, jars, crates)

# modified variable is loaded into the code from this point
start_point = start_point / 10

print "We can also do that this way:"
# we apply the modified variable 'start_point'
print "We's have %d beans, %d jars, and %d crates." % secret_formula(start_point)
```

    With a starting point of: 10000
    We's have 5000000 beans, 5000 jars, and 50 crates.
    We can also do that this way:
    We's have 500000 beans, 500 jars, and 5 crates.
    

# Exercise 25, Even More Practice

<sub>import, module, package, script, library</sub>

- For this exercice, consult the manual.
- First, run python ex25.py to find out any errors.
- Second, use the python engine to run pieces of codes from this file and not just trigger the whole code from this file
- Check out file `25_1.txt`.

```python
# %load ex25.py
def break_words(stuff):
    
    """This function will break up words for us."""
    words = stuff.split(' ') # the method splits the characters each time it finds a 'space'
    return words # you must specify in python where to load the result (into 'words')
    
def sort_words(words):
    
    """Sorts the words."""
    return sorted(words) # the python function sorts the separated words

def print_first_word(words):
    
    """Prints the first word after popping in off."""
    word = words.pop(0) # the method returns the first word in the index (position 0)
    print word

def print_last_word(words):
    
    """Prints the last word after popping it off."""
    word = words.pop(-1) # the method returns the last word in the index (position -1)
    print word

def sort_sentence(sentence):
    
    """Takes in a full sentence and returns the sorted words."""
    words = break_words(sentence) # launch a function
    return sort_words(words) # launch another function with the result of the first function

def print_first_and_last(sentence):
    
    """Prints the first and last words of the sentence."""
    words = break_words(sentence)
    print_first_word(words)
    print_last_word(words)
    
def print_first_and_last_sorted(sentence):
    
    """Sorts the words then prints the first and last one."""
    words = sort_sentence(sentence)
    print_first_word(words)
    print_last_word(words)
```

```python
%run ex25.py
```

- In the next script, you `import` the above script (ex25.py) as an external module (even though the script was previously run in IPython, and we want to simulate a script importing another script) and use its function as methods.

```python
import ex25

sentence = "All good things come to those who wait."

words = ex25.break_words(sentence)
words
```

    ['All', 'good', 'things', 'come', 'to', 'those', 'who', 'wait.']

```python
sorted_words = ex25.sort_words(words)
sorted_words
```

    ['All', 'come', 'good', 'things', 'those', 'to', 'wait.', 'who']

```python
ex25.print_first_word(words)
ex25.print_last_word(words)
words
```

    All
    wait.
    ['good', 'things', 'come', 'to', 'those', 'who']




```python
ex25.print_first_word(sorted_words)
ex25.print_last_word(sorted_words)
sorted_words
```

    All
    who
    ['come', 'good', 'things', 'those', 'to', 'wait.']

```python
sorted_words = ex25.sort_sentence(sentence)
sorted_words
```

    ['All', 'come', 'good', 'things', 'those', 'to', 'wait.', 'who']

```python
ex25.print_first_and_last(sentence)
ex25.print_first_and_last_sorted(sentence)
```

    All
    wait.
    All
    who

# Exercise 32, Loops and Lists

<sub>for, loop, list</sub>

```python
the_count = [1,2,3,4,5]
fruits = ['apples', 'oranges', 'pears', 'apricots']
change = [1, 'pennies', 2, 'dimes', 3, 'quarters']

# this first kind of for-loop goes through a list
for number in the_count:
    print "\tThis is count %d" % number
```

    	This is count 1
    	This is count 2
    	This is count 3
    	This is count 4
    	This is count 5

```python
# same as above
for fruit in fruits:
    print "A fruit of type: %s" % fruit
```

    A fruit of type: apples
    A fruit of type: oranges
    A fruit of type: pears
    A fruit of type: apricots

- We can go though mixed lists too. Notice we have to use `%r` since we don't know what's in it.

```python
for i in change:
    print "\tI got %r" % i
```

    	I got 1
    	I got 'pennies'
    	I got 2
    	I got 'dimes'
    	I got 3
    	I got 'quarters'

- We can also build lists. First, start with an empty one.

```python
elements = []

# then use the range function to do 0 to 5 counts
# 0 means 1st, the 6th is excluded; 0,1,2,3,4,5
for i in range(0, 6):
    print "Adding %d to the list." % i
    # append is a function that lists understand
    elements.append(i) # elements is a variable to which we add numbers
```

    Adding 0 to the list.
    Adding 1 to the list.
    Adding 2 to the list.
    Adding 3 to the list.
    Adding 4 to the list.
    Adding 5 to the list.

- We can print them out.

```python
for i in elements:
    print "\tElement was: %d" % i  
```

    	Element was: 0
    	Element was: 1
    	Element was: 2
    	Element was: 3
    	Element was: 4
    	Element was: 5
 
```python
print "Test the range function..."
print "range(5):", range(5)
print "range(6):", range(6)
print "range(1, 5):", range(1, 5)
print "range(2, 5):", range(2, 5)
print "range(0, 10, 2):", range(0, 10, 2)
```

    Test the range function...
    range(5): [0, 1, 2, 3, 4]
    range(6): [0, 1, 2, 3, 4, 5]
    range(1, 5): [1, 2, 3, 4]
    range(2, 5): [2, 3, 4]
    range(0, 10, 2): [0, 2, 4, 6, 8]

- Two-dimentional lists (above 2 dimension, it can become memory-intensive to compute!).

<sub>2d, tabular, lists in list, list of lists</sub>

```python
the_count_two = [[1,2,3],[4,5,6]]

# this first kind of for-loop goes through a list
# this list is not numerical, use %r or %s
for number in the_count_two:
    print "\tThis is count %r" % number
```

	This is count [1, 2, 3]
 	This is count [4, 5, 6]

# Exercise 33, While Loops

<sub>while, loop</sub>

```python
i = 0
numbers = []

while i < 6:
    print "At the top i is %d" % i
    numbers.append(i)
    
    i += 1
    print "Number now: ", numbers
    print "At the botton i is %d" % i


print "The numbers: "
```

    At the top i is 0
    Number now:  [0]
    At the botton i is 1
    At the top i is 1
    Number now:  [0, 1]
    At the botton i is 2
    At the top i is 2
    Number now:  [0, 1, 2]
    At the botton i is 3
    At the top i is 3
    Number now:  [0, 1, 2, 3]
    At the botton i is 4
    At the top i is 4
    Number now:  [0, 1, 2, 3, 4]
    At the botton i is 5
    At the top i is 5
    Number now:  [0, 1, 2, 3, 4, 5]
    At the botton i is 6
    The numbers: 

```python
for num in numbers:
    print num    
```

    0
    1
    2
    3
    4
    5
 
- Make it a function.

```python
def breaking_list(max_of, increm):
    
    i = 0
    numbers = []

    while i < max_of:
        print "At the top i is %d" % i
        numbers.append(i)
    
        i += increm
        print "Number now: ", numbers
        print "At the botton i is %d" % i

    print "The numbers: "

    for num in numbers:
        print num
        
print "Enter an integer, a maximum, higher than 1."
max_integer = int(raw_input("> "))
print "Enter an integer, an increment, equal or more than 1"
increment = int(raw_input("> "))
print "The maximum is %d and the increment is %d" % (max_integer, increment)

breaking_list(max_integer, increment)
```

    Enter an integer, a maximum, higher than 1.
    > 5
    Enter an integer, an increment, equal or more than 1
    > 2
    The maximum is 5 and the increment is 2
    At the top i is 0
    Number now:  [0]
    At the botton i is 2
    At the top i is 2
    Number now:  [0, 2]
    At the botton i is 4
    At the top i is 4
    Number now:  [0, 2, 4]
    At the botton i is 6
    The numbers: 
    0
    2
    4

- Change the function, replace with a for-loops. 

```python
def breaking_list2(max_of, increm):
    
    i = 0
    numbers = []

    for i in range(0, max_of, increm):
        print "At the top i is %d" % i
        numbers.append(i)
    
        i += increm
        print "Number now: ", numbers
        print "At the botton i is %d" % i

    print "The numbers: "

    for num in numbers:
        print num

max_integer2 = max_integer + 2
increment2 = increment + 1
breaking_list2(max_integer2, increment2)
```

    At the top i is 0
    Number now:  [0]
    At the botton i is 3
    At the top i is 3
    Number now:  [0, 3]
    At the botton i is 6
    At the top i is 6
    Number now:  [0, 3, 6]
    At the botton i is 9
    The numbers: 
    0
    3
    6

# Exercise 34, Accessing Elements of Lists

<sub>list, list of lists, lists in list, exit, program</sub>

- Let's build a scenario; functions leading to other functions.
- `def gold_room():`
- `def bear_room():`
- `def cthulhu_room():`
- `def dead(why):`
- `def start():`
- `start()` to launch the chain reaction.

```python
from sys import exit

def gold_room():
    
    print "This room is full of gold. How much do you take?"
    
    choice = raw_input("Write any number from 0 to 100> ") # variable
    if "0" in choice or "1" in choice: # could be 0, 1, 10, 11:19, 20, 21, 30, 31, 40, 41, 50, 51, etc.
        how_much = int(choice) # variable
    else:
        dead("Man, learn to type a number.") # launch function dead
        
    if how_much < 50:
        print "Nice, you're not greedy, you win!"
        exit(0) # launch system function exit
    else:
        dead("You greedy bastard!") # launch function dead

def bear_room():
    
    print "There is bear here."
    print "The bear has a bunch of honey."
    print "The fat bear is in front of another door."
    print "How are you going to move the bear?"
    bear_moved = False # variable

    while True: # infinite loop, run until it finds a right answer
        choice = raw_input("Write 'take honey', 'taunt bear' or 'open door'> ") # variable
        
        if choice == "take honey": # variable check
            dead("The bear looks at you then slaps your face off.") # launch function dead
        elif choice == "taunt bear" and not bear_moved: # double variables check
            print "The bear has moved from the door. You can go thought it now."
            bear_moved = True # change the variable
        elif choice == "taunt bear" and bear_moved:
            dead("The bear gets pissed off and chews your leg off.")
        elif choice == "open door" and bear_moved: # variable check
            gold_room() # launch function gold_room
        else:
            print "I got no idea what that means."
            
def cthulhu_room():
    
    print "Here you see the great evil Cthulhu."
    print "He, it, whatever stares at you and you go insane."
    print "Do you flee your life or eat your head?"
    
    choice = raw_input("Write 'flee' or 'head'> ") # variable
    
    if "flee" in choice: # variable check
        start() # launch function start
    elif "head" in choice:
        dead("Well that was tasty!")
    else:
        cthulhu_room() # launch function

def dead(why):
    
    print why, "Good job!"
    exit(0) # launch system function exit
    # exit(0) is neutral
    # exit(1) is an error, could be a useful warning
    # exit(2) or others like exit(100) are other warnings, or different messages

def start():
    
    print "You are in a dark room."
    print "There is a door to your right and left."
    print "Which one do you take: left or right?"
    
    choice = raw_input("Write 'left' or 'right'> ") # variable
    
    if choice == "left": # variable check, exact
        bear_room() # launch function bear_room
    elif choice == "right": # variable check, exact
        cthulhu_room()
    else:
        dead("You stumble around the room until you starve.")

start() # launch the chain reaction
```

    You are in a dark room.
    There is a door to your right and left.
    Which one do you take: left or right?
    Write 'left' or 'right'> left
    There is bear here.
    The bear has a bunch of honey.
    The fat bear is in front of another door.
    How are you going to move the bear?
    Write 'take honey', 'taunt bear' or 'open door'> taunt bear
    The bear has moved from the door. You can go thought it now.
    Write 'take honey', 'taunt bear' or 'open door'> open door
    This room is full of gold. How much do you take?
    Write any number from 0 to 100> 63
    Man, learn to type a number. Good job!
 
    An exception has occurred, use %tb to see the full traceback.

    SystemExit: 0

- There are multiple scenarios to try...

# Exercise 38, Doing Things to Lists

<sub>list, index, add, remove, delete, extract</sub>

```python
ten_things = "Apples Oranges Crows Telephones Light Sugar"

print "ten_things:", ten_things,", not a list"

print "Wait there are not 10 things is that list. Let's fix that."
```

    ten_things: Apples Oranges Crows Telephones Light Sugar , not a list
    Wait there are not 10 things is that list. Let's fix that.

```python
stuff = ten_things.split(' ') # variable ten_things, method split

print "stuff:", stuff,", a list"
```

    stuff: ['Apples', 'Oranges', 'Crows', 'Telephones', 'Light', 'Sugar'] , a list

```python
more_stuff = ["Day", "Night", "Song", "Frisbee", "Corn", "Banana", "Girl", "Boy"] # list variable

print "more_stuff:", more_stuff,", a list"
```

    more_stuff: ['Day', 'Night', 'Song', 'Frisbee', 'Corn', 'Banana', 'Girl', 'Boy'] , a list

- Most of the time, a for-loop is better than a while-loop.
- A while-loop is better when there is a test, a condition.

```python
while len(stuff) != 10:
    next_one = more_stuff.pop() # load a variable with another variable, method pop, pop means extracting 1 item from a list variable, the last item in the list
    print "Adding: ", next_one # show the content
    stuff.append(next_one) # variable stuff add 1-item list variable; the loop will go as long as stuff has less than 10 items  
    print "stuff:", stuff
    print "There are %d items now." % len(stuff) # length of stuff or the number of items in it

print "There we go: ", stuff
```

    Adding:  Boy
    stuff: ['Apples', 'Oranges', 'Crows', 'Telephones', 'Light', 'Sugar', 'Boy']
    There are 7 items now.
    Adding:  Girl
    stuff: ['Apples', 'Oranges', 'Crows', 'Telephones', 'Light', 'Sugar', 'Boy', 'Girl']
    There are 8 items now.
    Adding:  Banana
    stuff: ['Apples', 'Oranges', 'Crows', 'Telephones', 'Light', 'Sugar', 'Boy', 'Girl', 'Banana']
    There are 9 items now.
    Adding:  Corn
    stuff: ['Apples', 'Oranges', 'Crows', 'Telephones', 'Light', 'Sugar', 'Boy', 'Girl', 'Banana', 'Corn']
    There are 10 items now.
    There we go:  ['Apples', 'Oranges', 'Crows', 'Telephones', 'Light', 'Sugar', 'Boy', 'Girl', 'Banana', 'Corn']
 
```python
print "Let's do some things with stuff."

# print and pop choosen items according to the index
# could also be random index values!!!
# could reorder the list before (ascending, descending) 
print stuff[1] # the 2nd item
print stuff[2] # the 3rd item
print stuff[-1] # the last item
print stuff[-2]
print stuff.pop() # pop the last item
print stuff.pop(0) # pop the first item
print stuff.pop(1) # pop the 2nd item
print stuff.pop(-1) # pop the last item
print ' '.join(stuff) # var.split(' ') vs ' '.join(var), concatenate the list
print '#'.join(stuff[3:5]) # add a character at position 3 and 4 (4th, 5th, excluding the last) 
```

    Let's do some things with stuff.
    Oranges
    Crows
    Corn
    Banana
    Corn
    Apples
    Crows
    Banana
    Oranges Telephones Light Sugar Boy Girl
    Sugar#Boy
    

# Exercise 39, Dictionaries, Oh Lovely Dictionaries

<sub>dictionary</sub>

```python
things = ['a','b','c','d'] # list

print things
print things[1]
```

    ['a', 'b', 'c', 'd']
    b

- Change an element.

```python
things[1] = 'z'
print things
```

    ['a', 'z', 'c', 'd']
    

- A dictionary has keys associated with values. 
- Order does not matter. 
- If you supply the key, you will get the value.


```python
stuff = {'name' : 'Zed','age' : '39','height' : 8 * 12 + 2} # a dictionary

print stuff
print stuff['name']
print stuff['age']
print stuff['height']
```

    {'age': '39', 'name': 'Zed', 'height': 98}
    Zed
    39
    98
    

- Add an element.


```python
stuff['city'] = "San Francisco"
print stuff['city']
print stuff
```

    San Francisco
    {'city': 'San Francisco', 'age': '39', 'name': 'Zed', 'height': 98}
    

- Add and remove an element.


```python
stuff['color'] = "blue"
print stuff

del stuff['color']
print stuff
```

    {'color': 'blue', 'city': 'San Francisco', 'age': '39', 'name': 'Zed', 'height': 98}
    {'city': 'San Francisco', 'age': '39', 'name': 'Zed', 'height': 98}
    

- If the value does not exist when you call it, it will turn out an error. Instead, write it this way: `print "%r" % stuff.get('color',None)`. 
- If it's not existant, it will return 'None' or a value by default

```python
print stuff['state']
```
    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    <ipython-input-69-f211ffe8fe02> in <module>()
    ----> 1 print stuff['state']
    

    KeyError: 'state'

```python
print "%r" % stuff.get('color', None)
```

    None

- Change an element.

```python
print stuff['age']

stuff['age'] = 400
print stuff['age']
```

    39
    400

- Extract with the index.

```python
stuff[1] = "Wow"
stuff[2] = "Neato"
print stuff[1]
print stuff[2]

print stuff # new items won't be in order
```

    Wow
    Neato
    {'city': 'San Francisco', 2: 'Neato', 'name': 'Zed', 1: 'Wow', 'age': 400, 'height': 98}

- Delete an element (according to the index).

```python
del stuff[1]
del stuff[2]

print stuff
```

    {'city': 'San Francisco', 'name': 'Zed', 'age': 400, 'height': 98}

- Create a mapping of state to abbreviation.


```python
states = {
    'Oregon': 'OR',
    'Florida': 'FL',
    'California': 'CA',
    'New York': 'NY',
    'Michigan': 'MI'
}
```

- Create a basic set of states and some cities in them.

```python
cities = {
    'CA': 'San Francisco',
    'MI': 'Detroit',
    'FL': 'Jacksonville'
}
```

- Add some key:value to dictionary cities.

```python
cities['NY'] = 'New York'
cities['OR'] = 'Portland'
```

- Print out some cities.

```python
print "Dictionary 'cities': ", cities
print '-' * 10
print "NY State has: ", cities['NY'] # call the key
print "OR State has: ", cities['OR'] # get the value
```

    Dictionary 'cities':  {'FL': 'Jacksonville', 'CA': 'San Francisco', 'MI': 'Detroit', 'OR': 'Portland', 'NY': 'New York'}
    ----------
    NY State has:  New York
    OR State has:  Portland

- Print some states.

```python
print "Dictionary 'states': ", states
print '-' * 10
print "Michigan's abbreviation is: ", states['Michigan']
print "Florida's abbrebiation is: ", states['Florida']
```

    Dictionary 'states':  {'California': 'CA', 'Michigan': 'MI', 'New York': 'NY', 'Florida': 'FL', 'Oregon': 'OR'}
    ----------
    Michigan's abbreviation is:  MI
    Florida's abbrebiation is:  FL

- Print a dictionary in dictionary.

```python
print "Michigan has: ", cities[states['Michigan']]
# is like states['Michigan'], then cities['MI']
print "florida has: ", cities[states['Florida']]
```

    Michigan has:  Detroit
    florida has:  Jacksonville

- Print every state abbreviation.

```python
print "Enumerate Dictionary 'states', key:value..."
for state, abbrev in states.items():
    print "%s is abbreviated %s" % (state, abbrev)
# state = 1st item = key, abbrev = 2nd item = value
```

    Enumerate Dictionary 'states', key:value...
    California is abbreviated CA
    Michigan is abbreviated MI
    New York is abbreviated NY
    Florida is abbreviated FL
    Oregon is abbreviated OR

- Print every city in state.

```python
print "Enumerate Dictionary 'cities', key:value..."
for abbrev, city in cities.items():
    print "%s has the city %s" % (abbrev, city)   
```

    Enumerate Dictionary 'cities', key:value...
    FL has the city Jacksonville
    CA has the city San Francisco
    MI has the city Detroit
    OR has the city Portland
    NY has the city New York

- Now do both at the same time.

```python
print "Enumerate both dictionaries..."
for state, abbrev in states.items():
    print "%s state is abbreviated %s and has city %s" % (state, abbrev, cities[abbrev])
# state California gives abbrev CA, inside cities gives San Francisco   
```

    Enumerate both dictionaries...
    California state is abbreviated CA and has city San Francisco
    Michigan state is abbreviated MI and has city Detroit
    New York state is abbreviated NY and has city New York
    Florida state is abbreviated FL and has city Jacksonville
    Oregon state is abbreviated OR and has city Portland

- `get()` seek a key, whether it exists or not.

```python
state = states.get('Texas') # extract

if not state:
    print "Sorry, no Texas."
```

    Sorry, no Texas.

- Get a city with a default value.

```python
city = cities.get('TX', 'Does Not Exist')
print "The city for the state 'TX' is: %s" % city
```

    The city for the state 'TX' is: Does Not Exist

- Let's step up the above operations.
- Module `hashmap.py` works through a dictionary. 
- Module `ex39_test.py` contains dictionaries (just like the above).
- In Python, we would run module `ex39_test.py`. 
- The module would begin by importing module `hashmap.py` to use its methods and perform operations.
- Consult the manual.

# Exercise 40, Modules, Classes, and Objects

```python
mystuff = {'apple': 'I AM APPLES'}

print mystuff['apple'] # get X from Y
```

    I AM APPLES
 
- You can import a file with functions and variables from a another module.
- You can access the functions (methods) and variables from this other module.
- Both files must be in the same directory, otherwise, specify the path as well.

```python
# %load ex40.py
def apple():
    
    print "I AM APPLES!"

# this is just a variable
tangerine = "Living reflection of a dream"

apple()
```

```python
%run ex40.py
```

    I AM APPLES!

```python
import ex40

ex40.apple()

print ex40.tangerine
```

    I AM APPLES!
    Living reflection of a dream

```python
mystuff['new'] = ex40.tangerine

print mystuff['new']
```

    Living reflection of a dream

```python
import ex40

thing = ex40

thing.apple()
print thing.tangerine
```

    I AM APPLES!
    I AM APPLES!
    Living reflection of a dream

- Use a class instead of an imported module.
- Remember: class method = class function.

```python
class Song(object):

    
    def __init__(self, lyrics): # instantiation and shortcut for a creating a variable
        self.lyrics = lyrics # the variable could be equal to a text, a number or a variable

    def sing_me_a_song(self): # create a class function
        for line in self.lyrics:
            print line

            
# instance            
happy_bday = Song(["Happy birthday to you",
                   "I don't want to get sued",
                   "So I'll stop right there"])

# instance
bulls_on_parade = Song(["They rally around tha family",
                        "With pockets full of shells"])

# instance
au_clair = Song(["Au clair de la lune",
                 "Mon ami Pierrot",
                 "Prete-moi ta plume",
                 "Pour ecrire un mot"])

# not an instance!!!
frere_jacques = ["Frere Jacques (bis)",
                 "Dormez-vous (bis)",
                 "Sonnez les matines (bis)",
                 "Ding-din-don (bis)"]

# instance
frere = Song(["Frere Jacques (bis)",
              "Dormez-vous (bis)",
              "Sonnez les matines (bis)",
              "Ding-din-don (bis)"])


# not a class function
def chante_moi(paroles): # create a function
    
    for ligne in paroles:
        print ligne
```

- Invoke an instance.

```python
happy_bday.sing_me_a_song()
```

    Happy birthday to you
    I don't want to get sued
    So I'll stop right there
    
- Again.

```python
bulls_on_parade.sing_me_a_song()
```

    They rally around tha family
    With pockets full of shells
    

Write `instance.class function`/`instance.class method`

```python
au_clair.sing_me_a_song()
```

    Au clair de la lune
    Mon ami Pierrot
    Prete-moi ta plume
    Pour ecrire un mot
    
- Write the method the other around: `Class.class_function()`/`Class.class_method()`.

```python
#au_clair.sing_me_a_song()
Song.sing_me_a_song(au_clair)
```

    Au clair de la lune
    Mon ami Pierrot
    Prete-moi ta plume
    Pour ecrire un mot

- This function is independent.
- `frere_jacques.chante_moi()` can't be!!!

```python
chante_moi(frere_jacques)
```

    Frere Jacques (bis)
    Dormez-vous (bis)
    Sonnez les matines (bis)
    Ding-din-don (bis)
    
- It looks like `Class.class_function()`/`Class.class_method()`

```python
Song.sing_me_a_song(frere)
```

    Frere Jacques (bis)
    Dormez-vous (bis)
    Sonnez les matines (bis)
    Ding-din-don (bis)
    

# Exercise 41, Learning to Speak Object-Oriented

- Object-oriented programming (oop).
- The script below (`ex41.py`) imports a word list from a text file (`ex41_words.txt`).
- The script is a drill for learning oop.

```python
import random
import sys

## WORD_URL = "http://learncodethehardway.org/words.txt" # read a file http://learncodethehardway.org/words.txt
WORD_TXT = "ex41_words.txt"
WORDS = []

# dictionary {"Python": "English"}
PHRASES = {
    "class %%%(%%%):":
        "Make a class named %%% that is-a %%%.",
    "class %%%(object):\n\tdef __init__(self, ***):":
        "class %%% has-a __init__ that takes self and *** parameters.",
    "class %%%(object):\n\tdef ***(self, @@@):":
        "class %%% has-a function named *** that takes self and @@@ parameters.",
    "*** = %%%()":
        "Set *** to an instance of class %%%.",
    "***.***(@@@)":
        "From *** get the *** function, and call it with parameters self, @@@.",
    "***.*** = '***'":
        "From *** get the *** attribute and set it to '***'."
}

# do they want to drill phrases first
if len(sys.argv) == 2 and sys.argv[1] == "English":
    PHRASE_FIRST = True
else:
    PHRASE_FIRST = False
    
# load up the words from the website
## for word in urlopen(WORD_URL).readlines():
for word in open(WORD_TXT, "r").readlines():
    WORDS.append(word.strip())
    
def convert(snippet, phrase): # 'list comprehension', reseach on the Internet
    
    class_names = [w.capitalize() for w in
                    random.sample(WORDS, snippet.count("%%%"))]
    other_names = random.sample(WORDS, snippet.count("***"))
    results = []
    param_names = []
    
    for i in range(0, snippet.count("@@@")):
        param_count = random.randint(1,3)
        param_names.append(', '.join(random.sample(WORDS, param_count)))
        
    for sentence in snippet, phrase:
        result = sentence[:]
    
        # fake class names
        for word in class_names:
            result = result.replace("%%%", word, 1)
    
        # fake other names
        for word in other_names:
            result = result.replace("***", word, 1)
    
        # fake parameter lists
        for word in param_names:
            result = result.replace("@@@", word, 1)
    
        results.append(result)
    
    return results
        
# keep going until until they hit CTRL-D
try:
    while True:
        snippets = PHRASES.keys()
        random.shuffle(snippets)
        
        for snippet in snippets:
            phrase = PHRASES[snippet]
            question, answer = convert(snippet, phrase)
            if PHRASE_FIRST:
                question, answer = answer, question
            
            print question
            
            raw_input("> ")
            print "ANSWER: %s\n\n" % answer
except EOFError:
    print "\nBye"
```

    alarm.deer(disgust, brass)
    > deer is a Class alarm function that takes arguments digust and brass
    ANSWER: From alarm get the deer function, and call it with parameters self, disgust, brass.
    
    class Building(Blood):
    > etc
    ANSWER: Make a class named Building that is-a Blood.
    
    bucket = Berry()

- Sample of the original word list, 10 out of 503:

	    text
	    account
	    achiever
	    actor
	    addition
	    adjustment
	    advertisement
	    advice
	    aftermath
	    agreement
	    airplane

- Same script, but the list of word comes  from the Internet.
- A note on the script:
	- The use of constant variable such as WORD_URL (such variable should not be modified).
	- A constant variable can be anything from a number, a string to a dictionary.
	- The use of `try/except` pair to check for errors. It is similar to the pair `if/else`.
	- Therea are several types of errors. `EOFError` is just one type. Consult other (or online) manuals to find out about all the types of errors.

```python
import random
from urllib import urlopen
import sys

WORD_URL = "http://learncodethehardway.org/words.txt" # read a file
WORDS = []

# dictionary {"Python": "English"}
PHRASES = {
    "class %%%(%%%):":
        "Make a class named %%% that is-a %%%.",
    "class %%%(object):\n\tdef __init__(self, ***)":
        "class %%% has-a __init__ that takes self and *** parameters.",
    "class %%%(object):\n\tdef ***(self, @@@)":
        "class %%% has-a function named *** that takes self and @@@ parameters.",
    "*** = %%%()":
        "Set *** to an instance of class %%%.",
    "***.***(@@@)":
        "From *** get the *** function, and call it with parameters self, @@@.",
    "***.*** = '***'":
        "From *** get the *** attribute and set it to '***'."
}

# do they want to drill phrases first
if len(sys.argv) == 2 and sys.argv[1] == "English":
    PHRASE_FIRST = True
else:
    PHRASE_FIRST = False
    
# load up the words from the website
for word in urlopen(WORD_URL).readlines():
    WORDS.append(word.strip())
    
def convert(snippet, phrase): # 'list comprehension', reseach on the Internet
    
    class_names = [w.capitalize() for w in
                    random.sample(WORDS, snippet.count("%%%"))]
    other_names = random.sample(WORDS, snippet.count("***"))
    results = []
    param_names = []
    
    for i in range(0, snippet.count("@@@")):
        param_count = random.randint(1,3)
        param_names.append(', '.join(random.sample(WORDS, param_count)))
        
    for sentence in snippet, phrase:
        result = sentence[:]
    
        # fake class names
        for word in class_names:
            result = result.replace("%%%", word, 1)
    
        # fake other names
        for word in other_names:
            result = result.replace("***", word, 1)
    
        # fake parameter lists
        for word in param_names:
            result = result.replace("@@@", word, 1)
    
        results.append(result)
    
    return results
    
# keep going until until they hit CTRL-D
try:
    while True:
        snippets = PHRASES.keys()
        random.shuffle(snippets)
        
        for snippet in snippets:
            phrase = PHRASES[snippet]
            question, answer = convert(snippet, phrase)
            if PHRASE_FIRST:
                question, answer = answer, question
            
            print question
            
            raw_input("> ")
            print "ANSWER: %s\n\n" % answer
except EOFError:
    print "\nBye"
```

# Exercise 42, Is-A, Has-A, Objects, and Classes

- This exercise explains Exercise 41.
- Inheritance:
	- is-a.
	    - object.
	    - instance of an object.
	    - object of object.
	- has-a.
	    - attribute.
	    - not attribute.
	    - object.

- Animal is-a object.

```python
class Animal(object):
    
    
    pass
```

- Dog is-a Animal, Animal is-a object.

```python
class Dog(Animal):
    

    def __init__(self, name):
        
    ## Cat has-a name
        self.name = name
```

- Cat is-a Animal, Animal is-a object.

```python
class Cat(Animal):
    

    def __init__(self, name):
    ## Cat has-a name
        self.name = name
  
```

- Person is-a object.

```python
class Person(object):
    
    
    def __init__(self, name):
        
    ## Person has-a name
        self.name = name
    
    ## Person has-a pet of some kind, but the pet is specifies elsewhere...
        self.pet = None
```

- Employee is-a Person, Person is-a object.

```python
class Employee(Person):
    
      
    def __init__(self, name, salary):
        
    ## Employee has-a name, because Person has-a name
    ## super:
        super(Employee, self).__init__(name)
    ## Employee has-a salary
        self.salary = salary
      
```

- Fish is-a object.

```python
class Fish(object):
    
    
    ## no attributes like has-a name
    pass
```

- Salmon is-a Fish, Fish is-a object.

```python
class Salmon(Fish):
    
    
    ## no attributes like has-a name
    pass
```

- Halibut is-a Fish, Fish is-a object.

```python
class Halibut(Fish):
    
    
    ## no attributes like has-a name
    pass
    
```

- rover is-a instance of name, Dog has-a name.

```python
rover = Dog("Rover")
```

- satan is-a instance of name, Cat has-a name.

```python
satan = Cat("Satan")
```

- mary is-a instance of name, Person has-a name.

```python
mary = Person("Mary")
```

- mary has-a Cat, Cat has-a name, satan, is-a Cat.

```python
mary.pet = satan
```

- frank is-a instance of name, salary, Employee has-a name, salary.

```python
frank = Employee("Frank", 120000)
```

- frank has-a Dog, Dog has-a name, rover, is-a Dog.

```python
frank.pet = rover
```

- flipper is-a instance of Fish, Fish is-a object, both has-a not attributes.

```python
flipper = Fish()
```

- crouse is-a instance of Salmon, Salmon is-a Fish; both has-a not attribute.

```python
crouse = Salmon()
```

- harry is-a instance of Halibut, Halibut is-a Fish; both has-a not attribute.

```python
harry = Halibut()
```

- Wrap-up.

```
object
    class Fish(object)
        class Salmon(Fish)
            crouse = Salmon()
        class Halibut(Fish)
            harry = Halibut()
        flipper = Fish()
    class Animal(object)
        class Dog(Animal)
            rover = Dog("Rover") has-a name
        class Cat(Animal)
            satan = Cat("Satan") has-a name
    class Person(object)
        mary.pet = satan has-a name, pet
        class Employee(Person)
            frank = Employee ("Frank", 120000) has-a name, salary
            frank.pet = rover has-a pet
```

- The concept of inheritance, and those of implicit inheritance, overridden inheritance, multiple inheritance, composition, alteration, super objects (or 'reinheritance') are explained in Exercise 44.

# Exercise 43, Gothons from Planet Percal #25

This Exercise is the first to prepare the final project (Exercise 52, the last chapter). Let's create a game, from A to Z. First, start by planning. This methodology is valuable for planning any kind of project or program.

Methodology

1- Write about the problem:

"Aliens have invaded a space ship and our hero has to go through a maze of rooms defeating them so he can escape into an escape pod to the planet below. The game will be more like a Zork or Adventure type game with text outputs and funny ways to die. The game will involve an engine that runs a map full of rooms or scenes. Each room will print its own description when the player enters it and then tell the engine what room to run next out of the map."

2- Describe each scene:

- Death
    - This is when the player dies and should be something funny.
- Central Corridor
    - This is the starting point and has a Gothon already standing there they have to defeat with a joke before continuing.
- Laser Weapon Armory
    - This is where the hero gets a neutron bomb to blow up the ship before getting to the escape pod. It has a keypad the hero has to guess the number for.
- The Bridge
    - Another battle scene with a Gothon where the hero places the bomb.
- Escape Pod
    - Where the hero escapes but only after guessing the right escape pod. 


3- Draw a map, write more descriptions.


4- Extract key concepts:


- 1 concept = 1 class.
- Research them, deepen things.
- Nouns = concepts = classes:
    - Alien
    - Player
    - Ship
    - Maze
    - Room
    - Scene
    - Gothon
    - Escape Pod
    - Planet
    - Map
    - Engine
    - Death
    - Central Corridor
    - Laser Weapon Armory
    - The Bridge
- Verbs = functions.

This is par the PEP: classes should be in an explicit noun startin with a uppercased letter such as `class Central Corridor()`. Functions should be verbs such as `def play():`.

5- Create a class Hierarchy and object Map

- Make a class Hierarchy:
- Map
- Engine
- Scene
    - Death
    - Central Corridor
    - Laser Weapon Armory
    - The Bridge
    - Escape Pod
  
PEP: I know from the description I'm going to need a way to 'run' the engine, 'get the next scene' from the map, get the 'opening scene', and 'enter' a scene. I'll add those like this:

- Map
  - next_scene
  - opening_scene
- Engine
  - play
- Scene
  - enter
  - Death
  - Central Corridor
  - Laser Weapon Armory
  - The Bridge
  - Escape Pod

All the scenes under another scene will inherit it; except 'enter': override it later.

6- Code the Classes and a Test to Run Them:

- Turn:

```
- Map
    - next_scene (verb)
    - opening scene (verb)
- Engine
    - play (verb)
- Scene
    - enter (verb)
    - Death
    - Central Corridor
    - Laser Weapon Armory
    - The Bridge
    - Escape Pod
```

- Into:

```
class Map(object): 
    def __init__(self, start_scene):
    def next_scene(self, start_scene):    
    def opening_scene(self):

class Engine(object): 
    def __init__(self, scene_map):
    def play(self):

class Scene(object):
    def enter(self):

    class CentralCorridor(Scene):
        def enter(self):
    class LaserWeaponArmory(Scene):
        def enter(self):
    class TheBridge(Scene):
        def enter(self):
    class EscapePod(Scene):
        def enter(self):
    class Death(Scene):
        def enter(self):

a_map = Map('central_corridor')
a_game = Engine(a_map)
a_game.play()
```

- Into:

```
class Scene(object):

    def enter(self):
        pass


class Engine(object):

    def __init__(self, scene_map):
        pass
    def play(self):
        pass
        
        
class Death(Scene):

    def enter(self):
        pass


class CentralCorridor(Scene):

    def enter(self):
        pass
        

    def enter(self):
        pass
 
        
class TheBridge(Scene):
    def enter(self):
        pass


class EscapePod(Scene):

    def enter(self):
        pass


class Map(object):

    def __init__(self, start_scene):
        pass
    def next_scene(self, scene_name):
        pass
    def opening_scene(self):
        pass


a_map = Map('central_corridor')
a_game = Engine(a_map)
a_game.play()
```

- Start coding (first code skeleton).

```python
class Scene(object):
    
    
    def enter(self):
        
        pass

class Engine(object):
    
    
    def __init__(self, scene_map):
        
        pass
    
    def play(self):
        
        pass

    
class Death(Scene):
    
    
    def enter(self):
        
        pass

    
class CentralCorridor(Scene):
    
    
    def enter(self):
        
        pass

    
class LaserWeaponArmory(Scene):
    
    
    def enter(self):
        
        pass


class TheBridge(Scene):
    
    
    def enter(self):
        
        pass


class EscapePod(Scene):
    
    
    def enter(self):
        
        pass


class Map(object):
    
    
    def __init__(self, start_scene):
        
        pass
    
    def next_scene(self, scene_name):
        
        pass
    
    def opening_scene(self):
        
        pass


a_map = Map('central_corridor')
a_game = Engine(a_map)
a_game.play()
```

- Improve the code.

```python
# import two functions from two libraries
from sys import exit
from random import randint

# class to generate child classes
class Scene(object):
    
    def enter(self):
        
        print "This scene is not yet configured. Subclass it and implement enter()."
        exit(1)

        
class Engine(object):

    def __init__(self, scene_map):
        
        self.scene_map = scene_map
    
    def play(self):
        
        current_scene = self.scene_map.opening_scene() # instance of class Engine(object), __init__(self, scene_map) with method/function opening_scene(self) from class Map(object) below
        
        last_scene = self.scene_map.next_scene('finished') # instance of class Engine(object), __init__(self, scene_map) with method/function next_scene(self, scene_name) from class Map(object) below
        
        while current_scene != last_scene:
            
            next_scene_name = current_scene.enter() # function/method from class Scene(object) above
            
            current_scene = self.scene_map.next_scene(next_scene_name) # instance of class Engine(object), __init__(self, scene_map) with method/function next_scene(self, scene_name) from class Map(object)
                
        current_scene.enter() # use newly-created current_scene with function/method from class Scene(object) above

        
class Death(Scene):

    quips = ["You died.  You kinda suck at this.", "Your mom would be proud...if she were smarter.", "Such a louser.", "I have a small puppy that's better at this."] # a list (variable) where a random method will extract an element
    
    def enter(self):
        
        print Death.quips[randint(0, len(self.quips)-1)] # use class Death(object)'s variable and run a randint method; randint(1st random element from a number of elements contain in the list)
        exit(1)


class CentralCorridor(Scene):

    def enter(self): # the following will print whenever you call CentralCorridor.enter() function/method elsewhere
        
        print "The Gothons of Planet Percal #25 have invaded your ship and destroyed"
        print "your entire crew.  You are the last surviving member and your last"
        print "mission is to get the neutron destruct bomb from the Weapons Armory,"
        print "put it in the bridge, and blow the ship up after getting into an "
        print "escape pod."
        print "\n"
        print "You're running down the central corridor to the Weapons Armory when"
        print "a Gothon jumps out, red scaly skin, dark grimy teeth, and evil clown costume"
        print "flowing around his hate filled body.  He's blocking the door to the"
        print "Armory and about to pull a weapon to blast you."

        action = raw_input("shoot!/dodge!/tell a joke> ") 
            
        if action == "shoot!":
            print "Quick on the draw you yank out your blaster and fire it at the Gothon."
            print "His clown costume is flowing and moving around his body, which throws"
            print "off your aim.  Your laser hits his costume but misses him entirely.  This"
            print "completely ruins his brand new costume his mother bought him, which"
            print "makes him fly into an insane rage and blast you repeatedly in the face until"
            print "you are dead.  Then he eats you."
            return 'death' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        elif action == "dodge!":
            print "Like a world class boxer you dodge, weave, slip and slide right"
            print "as the Gothon's blaster cranks a laser past your head."
            print "In the middle of your artful dodge your foot slips and you"
            print "bang your head on the metal wall and pass out."
            print "You wake up shortly after only to die as the Gothon stomps on"
            print "your head and eats you."
            return 'death' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        elif action == "tell a joke":
            print "Lucky for you they made you learn Gothon insults in the academy."
            print "You tell the one Gothon joke you know:"
            print "Lbhe zbgure vf fb sng, jura fur fvgf nebhaq gur ubhfr, fur fvgf nebhaq gur ubhfr."
            print "The Gothon stops, tries not to laugh, then busts out laughing and can't move."
            print "While he's laughing you run up and shoot him square in the head"
            print "putting him down, then jump through the Weapon Armory door."
            return 'laser_weapon_armory' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        else:
            print "DOES NOT COMPUTE!"
            return 'central_corridor' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        
class LaserWeaponArmory(Scene):

    def enter(self): # the following will print whenever you call CentralCorridor.enter() function/method elsewhere
        
        print "You do a dive roll into the Weapon Armory, crouch and scan the room"
        print "for more Gothons that might be hiding.  It's dead quiet, too quiet."
        print "You stand up and run to the far side of the room and find the"
        print "neutron bomb in its container.  There's a keypad lock on the box"
        print "and you need the code to get the bomb out.  If you get the code"
        print "wrong 10 times then the lock closes forever and you can't"
        print "get the bomb.  The code is 3 digits."
        code = "%d%d%d" %(1,2,3) #% (randint(1,9), randint(1,9), randint(1,9))
        guess = raw_input("[keypad]> ")
        guesses = 0
        
        while guess != code and guesses < 10:
            print "BZZZZEDDD!"
            guesses += 1
            guess = raw_input("[keypad]> ")

        if guess == code:
            print "The container clicks open and the seal breaks, letting gas out."
            print "You grab the neutron bomb and run as fast as you can to the"
            print "bridge where you must place it in the right spot."
            return 'the_bridge' # input for class Map(object)'s dictionary of key:value; extract a function from another class
        else:
            print "The lock buzzes one last time and then you hear a sickening"
            print "melting sound as the mechanism is fused together."
            print "You decide to sit there, and finally the Gothons blow up the"
            print "ship from their ship and you die."
            return 'death' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        
class TheBridge(Scene):

    def enter(self): # the following will print whenever you call CentralCorridor.enter() function/method elsewhere
        
        print "You burst onto the Bridge with the netron destruct bomb"
        print "under your arm and surprise 5 Gothons who are trying to"
        print "take control of the ship.  Each of them has an even uglier"
        print "clown costume than the last.  They haven't pulled their"
        print "weapons out yet, as they see the active bomb under your"
        print "arm and don't want to set it off."

        action = raw_input("throw the bomb/slowly place the bomb> ")

        if action == "throw the bomb":
            print "In a panic you throw the bomb at the group of Gothons"
            print "and make a leap for the door.  Right as you drop it a"
            print "Gothon shoots you right in the back killing you."
            print "As you die you see another Gothon frantically try to disarm"
            print "the bomb. You die knowing they will probably blow up when"
            print "it goes off."
            return 'death'

        elif action == "slowly place the bomb":
            print "You point your blaster at the bomb under your arm"
            print "and the Gothons put their hands up and start to sweat."
            print "You inch backward to the door, open it, and then carefully"
            print "place the bomb on the floor, pointing your blaster at it."
            print "You then jump back through the door, punch the close button"
            print "and blast the lock so the Gothons can't get out."
            print "Now that the bomb is placed you run to the escape pod to"
            print "get off this tin can."
            return 'escape_pod'
        else:
            print "DOES NOT COMPUTE!"
            return "the_bridge" # input for class Map(object)'s dictionary of key:value; extract a function from another class    

        
class EscapePod(Scene):

    def enter(self): # the following will print whenever you call CentralCorridor.enter() function/method elsewhere
        
        print "You rush through the ship desperately trying to make it to"
        print "the escape pod before the whole ship explodes.  It seems like"
        print "hardly any Gothons are on the ship, so your run is clear of"
        print "interference.  You get to the chamber with the escape pods, and"
        print "now need to pick one to take.  Some of them could be damaged"
        print "but you don't have time to look.  There's 5 pods, which one"
        print "do you take?"

        good_pod = 1#randint(1,5)
        guess = raw_input("[pod #]> ")

        if int(guess) != good_pod:
            print "You jump into pod %s and hit the eject button." % guess
            print "The pod escapes out into the void of space, then"
            print "implodes as the hull ruptures, crushing your body"
            print "into jam jelly."
            return 'death' # input for class Map(object)'s dictionary of key:value; extract a function from another class
        else:
            print "You jump into pod %s and hit the eject button." % guess
            print "The pod easily slides out into space heading to"
            print "the planet below.  As it flies to the planet, you look"
            print "back and see your ship implode then explode like a"
            print "bright star, taking out the Gothon ship at the same"
            print "time.  You won!"
            return 'finished' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        
class Finished(Scene):

    def enter(self):
        
        print "You won! Good job."
        return 'finished' # input for class Map(object)'s dictionary of key:value; extract a function from another class

    
class Map(object):

    scenes = {
        'central_corridor': CentralCorridor(),
        'laser_weapon_armory': LaserWeaponArmory(),
        'the_bridge': TheBridge(),
        'escape_pod': EscapePod(),
        'death': Death(),
        'finished': Finished(),
    }
    
    def __init__(self, start_scene):
        
        self.start_scene = start_scene
        
    def next_scene(self, scene_name):
        
        val = Map.scenes.get(scene_name)
        return val
        
    def opening_scene(self):
        
        return self.next_scene(self.start_scene)

    
a_map = Map('central_corridor')
a_game = Engine(a_map)
a_game.play()
```

- Improve...


```python
# import two functions from two libraries
from sys import exit
from random import randint
import time
import math

# class to generate child classes
class Scene(object):

    def enter(self):
        
        print "This scene is not yet configured. Subclass it and implement enter()."
        exit(1)

        
class Engine(object):

    def __init__(self, scene_map, hero):
        
        self.scene_map = scene_map
        self.hero = hero
    
    def play(self):
        
        current_scene = self.scene_map.opening_scene() # instance of class Engine(object), __init__(self, scene_map) with method/function opening_scene(self) from class Map(object) below
        
        last_scene = self.scene_map.next_scene('finished') # instance of class Engine(object), __init__(self, scene_map) with method/function next_scene(self, scene_name) from class Map(object) below
        
        while current_scene != last_scene: # True:
            print "\n----------"
            next_scene_name = current_scene.enter(self.hero) # function/method from class Scene(object) above
            
            current_scene = self.scene_map.next_scene(next_scene_name) # instance of class Engine(object), __init__(self, scene_map) with method/function next_scene(self, scene_name) from class Map(object)
                
        current_scene.enter() # use newly-created current_scene with function/method from class Scene(object) above

        
class Death(Scene):

    quips = ["Death1", "Death2", "Death3", "Death4"] # a list (variable) where a random method will extract an element
    
    def enter(self, hero):
        
        print Death.quips[randint(0, len(self.quips)-1)] # use class Death(object)'s variable and run a randint method; randint(1st random element from a number of elements contain in the list)
        exit(1)

        
class CentralCorridor(Scene):

    def enter(self, hero): # the following will print whenever you call CentralCorridor.enter() function/method elsewhere
        
        print "Enter. Select."
        action = raw_input("Pick one: a/b/c> ").upper() 
            
        if action == "A":
            print "Ouch!"
            return 'death' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        elif action == "B":
            print "Aye!"
            return 'death' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        elif action == "C":
            print "Good."
            return 'laser_weapon_armory' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        else:
            print "DOES NOT COMPUTE!"
            return 'central_corridor' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        
class LaserWeaponArmory(Scene):

    def enter(self, hero): # the following will print whenever you call CentralCorridor.enter() function/method elsewhere
        
        print "Pick a 3-digit combinaison."
        code = "%d%d%d" %(1,2,3) #% (randint(1,9), randint(1,9), randint(1,9))
        print code
        guess = raw_input("[keypad]> ")
        guesses = 0
        
        while guess != code and guesses < 10:
            print "BZZZZEDDD!"
            guesses += 1
            guess = raw_input("[keypad]> ")

        if guess == code:
            print "Click! Go!"
            return 'the_bridge' # input for class Map(object)'s dictionary of key:value; extract a function from another class
        else:
            print "Boom!"
            return 'death' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        
class TheBridge(Scene):

    def enter(self, hero): # the following will print whenever you call CentralCorridor.enter() function/method elsewhere
        
        print "Bridge enigma."

        action = raw_input("true/false> ").upper()

        if action == "TRUE" or action == "T":
            print "It goes off."
            return 'death'

        elif action == "FALSE" or action == "F":
            print "Escape."
            return 'escape_pod'
        else:
            print "DOES NOT COMPUTE!"
            return "the_bridge" # input for class Map(object)'s dictionary of key:value; extract a function from another class    

        
class EscapePod(Scene):

    def enter(self, hero): # the following will print whenever you call CentralCorridor.enter() function/method elsewhere
        
        print "You rush!"

        good_pod = 1 #randint(1,5)
        guess = raw_input("[Pick a pod #]> ")

        if int(guess) != good_pod:
            print "Oups!"
            return 'death' # input for class Map(object)'s dictionary of key:value; extract a function from another class
        else:
            print "Good choice!"
            return 'finished' # input for class Map(object)'s dictionary of key:value; extract a function from another class

        
class Win(Scene):

    def enter(self, hero):
        print "You won! Good job."
        return 'finished' # input for class Map(object)'s dictionary of key:value; extract a function from another class
        # exit(0)

        
class Final(Scene):

    def enter(self, hero)
    
        monster = Monster("Gothon")
        print "%s, You now came across the final boss %s! Let's fight!!!" % (hero.name, monster.name)
        a_combat = Combat()
        next_stage = a_combat.combat(hero, monster)
        return next_stage

    
class Combat(object):
    
    def combat(self, hero, monster): #combat between two roles
        
        round = 1
        while True:
            print '='*30
            print 'round %d' % round
            print '='*30
            print "Your HP: %d" % hero.hp
            print "%s's HP: %d" % (monster.name, monster.hp)
            print 'Which action do you want to take?'
            print '-'*10
            print '1) attack - Attack the enemy'
            print '2) defend - Defend from being attacked, also will recover a bit'

            try:
                action = int(raw_input('> '))
            except ValueError:
                print "Please enter a number!!"
                continue

            # defending should be done before attacking
            if action == 2:
                hero.defend()

            # action of monster, 1/5 possibility it will defends
            monster_action = randint(1, 6)
            if monster_action == 5:
                monster.defend()

            if action == 1:
                hero.attack(monster)
            elif action == 2:
                pass
            else:
                print "No such action!"

            if monster_action < 5:
                monster.attack(hero)

            # whether win or die
            if hero.hp <= 0:
                return 'death'

            if monster.hp <= 0:
                return 'win'

            hero.rest()
            monster.rest()

            round += 1
        
        
class Map(object):

    scenes = {
        'central_corridor': CentralCorridor(),
        'laser_weapon_armory': LaserWeaponArmory(),
        'the_bridge': TheBridge(),
        'escape_pod': EscapePod(),
        'death': Death(),
        'final_fight': Final(),
        'win': Win(),
        'finished': Finished(),
    }
    
    def __init__(self, start_scene):
        
        self.start_scene = start_scene
        
    def next_scene(self, scene_name):
        
        val = Map.scenes.get(scene_name)
        return val
        
    def opening_scene(self):
        
        return self.next_scene(self.start_scene)

    
class human(object):
    
    defending = 0

    def __init__(self, name):
        
        self.name = name

    def attack(self, target): # attack the target
        
        percent = 0
        time.sleep(1)
        if target.defending == 1:
            percent = float(self.power) / 10.0 + randint(0, 10)
            target.hp = math.floor(target.hp - percent)
        else:
            percent = float(self.power) / 5.0 + randint(0, 10)
            target.hp = math.floor(target.hp - percent)
        print "%s attack %s. %s's HP decreased by %d points." % (self.name, target.name, target.name, percent)

    def defend(self): # be in the defending state
        
        self.defending = 1
        print "%s is trying to defend." % self.name

    def rest(self): # recover a bit after each round
        
        if self.defending == 1:
            percent = self.rate * 10 + randint(0, 10)
        else:
            percent = self.rate * 2 + randint(0, 10)
        self.hp += percent
        print "%s's HP increased by %d after rest." % (self.name, percent)
        self.defending = 0

        
class Hero(Human): # class for hero

    hp = 1000
    power = 200
    rate = 5

    
class Monster(Human): # class for monster
    
    hp = 5000
    power = 250
    rate = 5

    
a_map = Map('central_corridor')
a_hero = Hero('Joe')
a_game = Engine(a_map)
a_game.play()
```
## Wrap up

1. Draw a mindmap.
2. Draw a flowchart.
3. List all variables, data, other objects and add comments.
4. Build the modules (classes) and embed the primal code.
5. Refine.
6. Use a visualizing software.

# Exercise 44, Inheritance vs Composition

From the manual.

## When to Use Inheritance or Composition

The question of 'inheritance versus composition' comes down to an attempt to solve the problem of reusable code. 

You don't want to have duplicated code all over your software, since that's not clean and efficient. 

- Inheritance: solves this problem by creating a mechanism for you to have implied features in base classes.
- Composition: solves this by giving you modules and the ability to call functions in other classes.

If both solutions solve the problem of reuse, then which one is appropriate in which situations? The answer is incredibly subjective, but I'll give you my three guidelines for when to do which:

1. Avoid multiple Inheritance at all costs, as it's too complex to be reliable. If you're stuck with it, then be prepared to know the class hierarchy and spend time finding where everything is coming from.
2. Use Composition to package code into modules that are used in many different unrelated places and situations.
3. Use Inheritance only when there are clearly related reusable pieces of code that fit under a single common concept or if you have to because of something you're using.

The thing to remember about object-oriented programming is that it is entirely a social convention programmers have created to package and share code. In that case, find out how they use things and then just adapt to the situation.

## Function Style

<sub>pep</sub>

Function = Method.

A class does things: name it as if it's a command you are giving to the class. Same as `pop` is saying 'pop this off the list'.

Keep functions small and simple (PEP).

Class Style

- Use the camel case: `SuperGoldFactory`.
- Minimize what `__init__` does. It should be simple to use.
- Other class functions use the underscore format: `my_awesome_hair`.
- Be consistent in how you organize your function arguments. Function 1 takes `(dog, cat, user)`, function 2 should take `(dog, cat, user)`. Unless there is a good reason.
- Variable should be self-contained. Limit importing from modules or globals.
- Always have a class `Name(object)` on top of all.

Code Style

- Give your code vertical space to read.
- Read you code out loud to test it. Change the difficult passages to improve readibility.
- Imitate other coders: find you style.
- Respect others's style; be a team player.

Good Comments

- Describe why you are doing doing what you are doing.
- Write for the others.
- Write sentences.
- Avoid clutering the code though. Short sentences, to the point.
- Review your comments.

## Composition

In this code I'm not using the name Parent, since there is not a parent-child is-a relationship. This is a has-a relationship, where Child has-a Other that it uses to get its work done. 

```python
class Other(object):

    def implicit(self):
        
        print "OTHER implicit()"

    def override(self):
        
        print "OTHER override()"

    def altered(self):
        
        print "OTHER altered()"

        
class Child(object):

    def __init__(self):
        
        self.other = Other() # initialize this class with Other(), when an instance is created, it will inherit the class member variables, class functions...

    def implicit(self):
        
        self.other.implicit() # call the other class function 

    def override(self):
        
        print "CHILD override()"

    def altered(self):
        
        print "CHILD, BEFORE OTHER altered()"
        self.other.altered() # call the other class function
        print "CHILD, AFTER OTHER altered()"

        
son = Child() # instance

son.implicit()
son.override()
son.altered()
```

## Implicit Inheritance

Actions on the child imply an action on the parent.

The use of pass under the `class Child:` is how you tell Python that you want an empty block. This creates a class named `Child` but says that there's nothing new to define in it. Instead it will inherit all of its behavior from `Parent`.

If you put functions in a base class (i.e., `Parent`) then all subclasses (i.e., `Child`) will automatically get those features. Very handy for repetitive code you need in many classes.

```python
class Parent(object):

    def implicit(self):
        
        print "PARENT implicit()"

        
class Child(Parent):
    
    pass


dad = Parent()
son = Child()
```

## Inherit from both Classes

Python has to look-up the possible function in the class hierarchy for both `Child` and `BadStuff`, but it needs to do this in a consistent order. To do this Python uses "method resolution order" (MRO) and an algorithm called C3 to get it straight.

Because the MRO is complex and a well-defined algorithm is used, Python can't leave it to you to get the MRO right. Instead, Python gives you the `super()` function, which handles all of this for you in the places that you need the altering type of actions as I did in Child.altered. With `super()` you don't have to worry about getting this right, and Python will find the right function for you.

```python
class SuperFun(Child, BadStuff):
    
    pass
```

## Override Explicitly

Actions on the child override the action on the parent.

As you can see, it runs the `Parent.override` function because that variable (dad) is a Parent. But it also runs  `Child.override` messages because son is an instance of `Child` and `Child` overrides that function by defining its own version.

```python
class Parent(object):

    def override(self):
        print "PARENT override()"

        
class Child(Parent):

    def override(self):
        
        print "CHILD override()"

        
dad = Parent()
son = Child()

dad.override()
son.override()
```

## Alter Before or After

Actions on the child alter the action on the parent.

`son.altered()` overrides Parent.altered the `Child.altered` version runs, and line 9 executes like you'd expect. In this case I want to do a before and after, I want to use super to get the `Parent.altered` version. I call `super(Child, self).altered()`, which is aware of inheritance and will get the `Parent` class for you. You should be able to read this as "call super with arguments `Child` and `self`, then call the function altered on whatever it returns." At this point, the `Parent.altered` version of the function runs, and that prints out the Parent message. Finally, this returns from the `Parent.altered` and the `Child.altered` function continues to print out the after message.

```python
class Parent(object):

    def altered(self):
        
        print "PARENT altered()"

class Child(Parent):
   
    def altered(self):
        
        print "CHILD, BEFORE PARENT altered()"
        super(Child, self).altered()
        print "CHILD, AFTER PARENT altered()"

        
dad = Parent()
son = Child()

dad.altered()
son.altered()
```

## Super

With `super`, `Child` reinherit from the `Parent`.

The most common use of `super()` is actually in `__init__` functions in base classes. Then additional class functions.

```python
class Child(Parent):

    def __init__(self, stuff):
        
        self.stuff = stuff
        super(Child, self).__init__()
```

## All Three Combined

```python
class Parent(object):
    
    def override(self):
        
        print "PARENT override()"

    def implicit(self):
        
        print "PARENT implicit()"

    def altered(self):
        
        print "PARENT altered()"

        
class Child(Parent):
   
    def override(self):
        
        print "CHILD override()"

    def altered(self):
        
        print "CHILD, BEFORE PARENT altered()"
        super(Child, self).altered()
        print "CHILD, AFTER PARENT altered()"

        
dad = Parent()
son = Child()

dad.implicit()
son.implicit()

dad.override()
son.override()

dad.altered()
son.altered()
```

# Exercise 45, You Make a Game

Use an existing project, Exercise 43 for example, and adapt it. This is a first draft for a project...

**1**

Storyboarding tool.

Create a program that would question the user on its data and advise him on what would be the best graphics to use. Frame by frame, the user could build a presentation knowing slide 1 should be a histogram, slide 2 a scatter plot, etc. 

**2**

- Map
    - next_graph
    - opening comment (verb)
- Engine
    - choose (verb)
- Graph
    - proceed (verb)
    1. CC pie
    2. IC bar
    3. TSC column, line
    4. FDC column, line
    5. CorC bar, dot

- opening comment
- general comment
- storytelling
- pie
    - compare data, y, n
    - y, stacked bar chart
    - n, pie chart with a maximum of 6 items
- bar
    - simple series of data or items: h deviation bar chart (tornado), divide A from B (winners from losers, good markets from bad markets): h deviation bar chart (tornado), mix of two components (portfolio A items vs portfolio B items):sliding h bar chart, high-low spreads:range h bar chart, correlation x1 and x2 with y (two products, two markets... with): paired bar chart, compare aspects (with or without discount, red or blue paint):group h bar chart, components of the total: subdivided h bar chart...
- column
    - p.37, 42
- line
    - p.39, 44-45
- surface
    - p. 40
- dot
    - p.49

**3**

- Create module `3graph_story` (proof of concept).
- The module presents a story in 3 graphs, according to 3 sets of data.

```
class Map(object):
    def __init__(self,start):
    def next(self, start):
    def opening(self):
    
class Engine(object):
    def __init__(self,graph_map):
    def choose(self):
    
class Graph(object):
    def proceed(self):
    
    class 1CC(Graph):
        def enter(self)
            pie
    class 2IC(Graph):
        def enter(self):
            bar
    class 3TSC(Graph):
        def enter(self):
            column
            line
    class 4FDC(Graph):
        def enter(self):
            column
            line
    class 5CorC(Graph):
        def enter(self):
            bar
            dot
```

And so on. Consult the manual to find out more

# Exercise 46, A Project Skeleton

- The 'skeleton' directory (see below) or the directory framework will have all the basics you need to get a new project up and running. 
- It will have your project layout, automated tests, modules, and install scripts.

```
\:.
├───bin
│   ├───__init__.py
│   └───__init__.pyc
├───docs
├───NAME
│   ├───__init__.py
│   └───__init__.pyc
├───tests
│   ├───__init__.py
│   └───__init__.pyc
└───setup.py   
```

- `\:.` is the project parent directory or simply 'the' directory (its name is the project's name).
- The directory is the place to be when launching scripts.
- `bin` is the main sub-directory. It contains the main script (`python bin/main.py`) for launching other scripts in the project; and launching tests as well. These script are often located in other sub-directories.
- A sub-directory must be executable to import a module from it or execute a script in it: add an empty script called `__init__.py`.
- When a script is executed, it is compiled. Another script, with the extension `.pyc`, appears. Same as for `__init__.pyc`, as the sub-directory was executed (when a script import a script from another sub-directory for example).
- `tests` contains files to perform nose tests and unittests.
- `setup.py` is for documenting and distributing the project (when the project is compiled to be launched as a whole or frozen to be distributed).
- You can add a `readme` file below (usually a text or markdown document).
- The `docs` sub-directory contains all the project's documentation. It is more elaborate than the 'readme' file: manuals, explanations, logs, wikis, etc.
- There can be other sub-directories for static such as images, web languages, etc.
- Repeat this directory structure for every project.
- To clean up the directory, in the bash:

```bash
find . -name "*.pyc" -print #display
find . -name "*.pyc" -exec rn{}\; 1 remove

grep -r "NAME" * #search within files
```

- In Linux, before running any script, be sure to set the path to the project directory. 
- Bash:

```bash
export PYTHONPATH=.
export PYTHONPATH=$PYTHONPATH:$PWD

unset PYTHONPATH # to remove
```

- In Windows, set the path in the environment variables. Otherwise, Python won't find the scripts.
- PowerShell:

```bash
$env:PYTHONPATH = "$env:PYTHONPATH;."
```

- Or, on top of the Python code, below the shebang lnes, and before any other imports, add:

```python
import sys
sys.path # to view
sys.path.append('.') # to set
```

- Consult the manual to find out more.

# Exercise 47, Automated Testing

## Miscellaneous notes

- The project directory is 'ex47'.
- Test if you migrated the files correctly. In the bash:

```bash
grep -r NAME *  # no traces of 'NAME', from 'skeleton'
find . -name "*.pyc" -exec rm {} \; # no trace of 'name'
```

- When you launch a script, you launch it from the parent directory with `python bin/app.py`.
- In directory 'ex47', run tests with `python tests/BLAH_tests.py`. 
- Consult the manual about testing. This is not covered in this notebook. 
- Testing must be done in the shell or in the bash. Make sure you're running the tests with nosetests not with just Python. 
- The important functions here are `assert_equal` which makes sure that variables you have set or paths you have built in a Room are actually what you think they are. If you get the wrong result, then nosetests will print out an error message so you can go figure it out.
- In a script, when you import from another sub-directory, code:

```python
from ex47.game import Room
```

- When the imported script is in the same sub-directory, code:

```python
from bin import Room
```

- Consult the manual to find out more.

# Exercise 50, Your First Website

## An overview

- Web framework for web projects.
- Django (the real deal, but complicated), Flask (modest), Pyramid (scalable), etc.
- Or the simple, yet powerful enough, web.py.
- Exercises, from 50 to 52, are done with web.p
