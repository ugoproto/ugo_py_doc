---

**Foreword**

Code snippets and excerpts from the course. Python 2. From Codecademy. 

---

# UNIT 1, Python Syntax

## Python Syntax

Python is an easy to learn programming language. You can use it to create web apps, games, even a search engine!


```python
print "Welcome to Python!"
print("Welcome")
print 5 + 3
print(5 + 5)
print "What " + str(3)
print "What",5
```

    Welcome to Python!
    Welcome
    8
    10
    What 3
    What 5
    


```python
a = 30
print "What " + str(a)

b = "A list \t*A  \\ \" \' "
print b

c = 10 + 20
print c
```

    What 30
    A list 	*A  \ " ' 
    30
    


```python
print "1 : %r" % (a) # read#
print "2 : %s" % (a) # string#
print "? : %d" % (a) # digit
print "3 : %r" % (b)
print "4 : %s" % (b)
# print "? : %d" % (b) !!!
```

    1 : 30
    2 : 30
    ? : 30
    3 : 'A list \t*A  \\ " \' '
    4 : A list 	*A  \ " ' 
    

Creating web apps, games, and search engines all involve storing and working with different types of data. They do so using variables. A variable stores a piece of data, and gives it a specific name.


```python
my_variable = 10
```

You just stored a number in a variable. Numbers are one data type we use in programming. A second data type is called a boolean. A boolean is like a light switch. It can only have two values. Just like a light switch can only be on or off, a boolean can only be `True` or `False`.


```python
my_int = 7
my_float = 1.23
my_bool = True
```

Say `my_int = 7`. You can change the value of a variable by "reassigning" it.


```python
my_int = 7

my_int = 3

print my_int
```

    3
    

In Python, whitespace is used to structure code. Whitespace is important, so you have to be careful with how you use it.


```python
def spam():
    eggs = 12
    return eggs
        
print spam()
```

    12
    

You'll get this error whenever your whitespace is off.

The interpreter runs your code line by line, and checks for any errors.

You probably saw us use the # sign a few times in earlier exercises. The # sign is for comments. A comment is a line of text that Python won't try to run as code. It's just for humans to read.

Comments make your program easier to understand. When you look back at your code or others want to collaborate with you, they can read your comments and easily figure out what your code does.

The `#` sign will only comment out a single line. While you could write a multi-line comment, starting each line with `#`, that can be a pain.

Instead, for multi-line comments, you can include the whole block in a set of triple quotation marks:


```python
"""
Sipping from your cup 'til it runneth over,
Holy Grail.
"""
```




    "\nSipping from your cup 'til it runneth over,\nHoly Grail.\n"



Great! Now let's do some math. You can add, subtract, multiply, divide numbers.


```python
addition = 72 + 23
subtraction = 108 - 204
multiplication = 108 * 0.5
division = 108 / 9

count_to = 72 + 56

print count_to
```

    128
    

All that math can be done on a calculator, so why use Python? Because you can combine math with other data types (e.g. booleans) and commands to create useful programs. Calculators just stick to numbers.

Create a new variable called eight and set it to 8, or the result of 2 to the power to 3 (`2 ^ 3` oe `2 ** 3`).


```python
eggs = 10 ** 2

print eggs
```

    100
    

Our final operator is modulo. Modulo returns the remainder from a division. So, if you type `3 % 2`, it will return 1, because 2 goes into 3 evenly once, with 1 left over.


```python
spam = 5 % 4

print spam
```

    1
    

## Tip Calculator

Now let's apply the concepts from the previous section to a real world example. You've finished eating at a restaurant, and received this bill:

- Cost of meal: $44.50
- Restaurant tax: 6.75%
- Tip: 15%


```python
meal = 44.50
tax = 6.75/100 
tip = 0.15

meal = meal + meal * tax
total = meal + meal * tip

print("%.2f") % total
```

    54.63
    

## Quiz 1

OK

# UNIT 2, Strings and Console Output

## Strings & Console Output

Another useful data type is the string. A string can contain letters, numbers, and symbols.


```python
name = "Ryan"
age = "19"
food = "cheese"
```

Let's get a little practice in with strings.


```python
caesar = "Graham"
praline = "John"
viking = "Teresa"

print caesar
print praline
print viking
```

    Graham
    John
    Teresa
    


```python
'There's a snake in my boot!'
```


      File "<ipython-input-16-13621f01b99c>", line 1
        'There's a snake in my boot!'
               ^
    SyntaxError: invalid syntax
    


This code breaks because Python thinks the apostrophe in 'There's' ends the string. We can use the backslash to fix the problem, like this:


```python
'There\'s a snake in my boot!'
'This isn\'t flying, this is falling with style!'
```




    "This isn't flying, this is falling with style!"



Each character in a string is assigned a number. This number is called the index. Check out the diagram in the editor.


```python
c = "cats"[0]
n = "Ryan"[3]

"""
The string "PYTHON" has six characters,
numbered 0 to 5, as shown below:

+---+---+---+---+---+---+
| P | Y | T | H | O | N |
+---+---+---+---+---+---+
  0   1   2   3   4   5

So if you wanted "Y", you could just type
"PYTHON"[1] (always start counting from 0!)
"""
fifth_letter = "MONTY"[4]

print fifth_letter
```

    Y
    

Now that we know how to store strings, let's see how we can change them using string methods. String methods let you perform specific tasks for strings. We'll focus on four string methods:

- `len()`
- `lower()`
- `upper()`
- `str()`

<sub>length, string</sub>


```python
parrot = "Norwegian Blue"

print len(parrot) # length, number of characters, including blanks
print parrot.lower() # to lowercases
print parrot.upper() # to uppercases

pi = 3.14

print str(pi) # number of character in the string
```

    14
    norwegian blue
    NORWEGIAN BLUE
    3.14
    

`len(string)` and `str(object)`, but dot notation (such as "String".upper()) for the rest.

Methods that use dot notation only work with strings.

On the other hand, `len()` and `str()` can work on other data types.

The area where we've been writing our code is called the editor. The console is where the results of your code is shown. `print` simply displays your code in the console.


```python
print "Monty Python"

the_machine_goes = "Ping!"
print the_machine_goes
```

    Monty Python
    Ping!
    

Now let's combine the two! The `+` operator between strings will 'add' them together, one after the other. Notice that there are spaces inside the quotation marks after Life and of so that we can make the combined string look like 3 words. Combining strings together like this is called concatenation. Let's try concatenating a few strings together now!


```python
print "Life " + "of " + "Brian"
print "Spam and eggs"
```

    Life of Brian
    Spam and eggs
    

Sometimes you need to combine a string with something that isn't a string. In order to do that, you have to convert the non-string into a string. he `str()` method converts non-strings into strings. In the above example, you convert the number 2 into a string and then you concatenate the strings together.


```python
print "The value of pi is around " + str(3.14)
```

    The value of pi is around 3.14
    

When you want to print a variable with a string, the `%` operator after a string is used to combine a string with variables. The `%` operator will replace a `%s` in the string with the string variable that comes after it.


```python
string_1 = "Camelot"
string_2 = "place"

print "Let's not go to %s. 'Tis a silly %s." % (string_1, string_2)

name = raw_input("What is your name?")
quest = raw_input("What is your quest?")
color = raw_input("What is your favorite color?")

print "Ah, so your name is %s, your quest is %s, " \
    "and your favorite color is %s." % (name, quest, color)
```

    Let's not go to Camelot. 'Tis a silly place.
    What is your name?Al
    What is your quest?Graal
    What is your favorite color?red
    Ah, so your name is Al, your quest is Graal, and your favorite color is red.
    

## Date and Time

A lot of times you want to keep track of when something happened. We can do so in Python using `datetime`. Here we'll use datetime to print the date and time in a nice format.


```python
from datetime import datetime # all functions from datetime are imported

now = datetime.now()

print now
print now.year
print now.month
print now.day

print '%s/%s/%s' % (now.month, now.day, now.year)
print '%s:%s:%s' % (now.hour, now.minute, now.second)

print '%s/%s/%s %s:%s:%s' % (now.month, now.day, now.year, now.hour, now.minute, now.second)
```

    2016-10-18 14:02:03.661000
    2016
    10
    18
    10/18/2016
    14:2:3
    10/18/2016 14:2:3
    

## Quiz 2


```python
time = datetime.now()
print time.day

time = datetime.now() #13:08:09
print str(time.hour) + ":" + str(time.minute) + ":" + str(time.second)

now = datetime.now() #2013-01-04 19:22:43

print '%s/%s/%s %s:%s:%s' % (now.day, now.month, now.year, now.hour, now.minute, now.second)

day = 04
```

    18
    14:2:11
    18/10/2016 14:2:11
    

## Project Python Mad Libs

<sub>concatenate, variable</sub>

Python can be used for a variety of different tasks. In this project, we'll use Python to write a Mad Libs story! Mad Libs are stories with blank spaces that a reader can fill in with their own words. The result is usually a funny (or strange) story.

Mad Libs require:

- Words from the reader (for the blank spaces)
- A story to plug the words into

For this project, we'll provide you with the story (feel free to modify it), but it will be up to you to build a program that does the following:

- Prompt the user for input
- Print the entire Mad Libs story with the user's input in the right places   


```python
"""
Python can be used for a variety of different tasks. In this project, we'll use Python to write a Mad Libs story! Mad Libs are stories with blank spaces that a reader can fill in with their own words. The result is usually a funny (or strange) story.
"""

print "The program is running."

name = raw_input("Input a name? ")

adj_one = raw_input("Input an adjective? ")
adj_two = raw_input("Input another adjective? ")
adj_three = raw_input("Input a last adjective? ")

verb_one = raw_input("Input a verb? ")
verb_two = raw_input("Input another verb? ")
verb_three = raw_input("Input a last verb? ")

noun_one = raw_input("Input a noun? ")
noun_two = raw_input("Input another noun? ")
noun_three = raw_input("Input another noun? ")
noun_four = raw_input("Input a last noun? ")

animal = raw_input("Input an animal? ")
food = raw_input("Input a food? ")
fruit = raw_input("Input a fruit? ")
number = raw_input("Input a number? ")
superhero = raw_input("Input a superhero? ")
country = raw_input("Input a country? ")
dessert = raw_input("Input a dessert? ")
year = raw_input("Input a year? ")
print ""
```

    The program is running.
    Input a name? Al
    Input an adjective? small
    Input another adjective? great
    Input a last adjective? yellow
    Input a verb? dig
    Input another verb? walk
    Input a last verb? eat
    Input a noun? spoon
    Input another noun? lamp
    Input another noun? table
    Input a last noun? pen
    Input an animal? dog
    Input a food? pasta
    Input a fruit? apple
    Input a number? 10
    Input a superhero? spiderman
    Input a country? mexico
    Input a dessert? apple pie
    Input a year? 2016
    
    

The template for the story.


```python
STORY = "This morning I woke up and felt %s because %s was going to finally %s over the big %s %s. On the other side of the %s were many %ss protesting to keep %s in stores. The crowd began to %s to the rythym of the %s, which made all of the %ss very %s. %s tried to %s into the sewers and found %s rats. Needing help, %s quickly called %s. %s appeared and saved %s by flying to %s and dropping %s into a puddle of %s. %s then fell asleep and woke up in the year %s, in a world where %ss ruled the world."

print STORY % (adj_one, name, verb_one, adj_two, noun_one, noun_two, animal, food, verb_two, noun_three, fruit, adj_three, name, verb_three, number, name, superhero, superhero, name, country, name, dessert, name, year, noun_four)
```

    This morning I woke up and felt small because Al was going to finally dig over the big great spoon. On the other side of the lamp were many dogs protesting to keep pasta in stores. The crowd began to walk to the rythym of the table, which made all of the apples very yellow. Al tried to eat into the sewers and found 10 rats. Needing help, Al quickly called spiderman. spiderman appeared and saved Al by flying to mexico and dropping Al into a puddle of apple pie. Al then fell asleep and woke up in the year 2016, in a world where pens ruled the world.
    

# UNIT 3, Conditionals and Control Flow

## Conditionals & Control Flow

Control flow gives us this ability to choose among outcomes based off what else is happening in the program.


```python
def clinic():
    
    print "You've just entered the clinic!"
    print "Do you take the door on the left or the right?"
    answer = raw_input("Type left or right and hit 'Enter'.").lower()
    if answer == "left" or answer == "l":
        print "This is the Verbal Abuse Room, you heap of parrot droppings!"
    elif answer == "right" or answer == "r":
        print "Of course this is the Argument Room, I've told you that already!"
    else:
        print "You didn't pick left or right! Try again."
        clinic() # launch the function back

clinic()
```

    You've just entered the clinic!
    Do you take the door on the left or the right?
    Type left or right and hit 'Enter'.left
    This is the Verbal Abuse Room, you heap of parrot droppings!
    

Comparators. There are six:

- Equal to: `==`
- Not equal to: `!=`
- Less than: `<`
- Less than or equal to: `<=`
- Greater than: `>`
- Greater than or equal to: `>=`

Note that `==` compares whether two things are equal, and `=` assigns a value to a variable.


```python
bool_one = 1 + 2
bool_two = 3
bool_one == bool_two # true
```




    True



Boolean operators compare statements and result in boolean values. There are three boolean operators:

- `and`, which checks if both the statements are True;
- `or`, which checks if at least one of the statements is True;
- `not`, which gives the opposite of the statement.


```python
bool_one = 1 > 2 and 2 > 3 # false
bool_two = False and True # false
bool_one = True or False # true
bool_two = 2 == 2 or 2 == 3 # true
bool_one = not 40 != 41 # true
```

`if` is a conditional statement.


```python
answer = "Left"

if answer == "Left":
    print "This is the Verbal Abuse Room, you heap of parrot droppings!"

def using_control_once():
    
    if "A"=="A":
        return "Success #1"

def using_control_again():
    
    if 1!=2:
        return "Success #2"

print using_control_once()
print using_control_again()
```

    This is the Verbal Abuse Room, you heap of parrot droppings!
    Success #1
    Success #2
    

The `else` statement complements the `if` statement.


```python
answer = "'This but a scratch!"

def black_knight():
    
    if answer == "'Tis but a scratch!":
        return True
    else:             
        return False  # Make sure this returns False

def french_soldier():
    
    if answer == "Go away, or I shall taunt you a second time!":
        return True
    else:             
        return False  # Make sure this returns False
        
print black_knight()
print french_soldier()
```

    False
    False
    

`elif` is short for 'else if'. It means exactly what it sounds like: "otherwise, if the following expression is true, do this!"


```python
def greater_less_equal_5(answer):
    
    if answer > 5:
        return 1
    elif answer < 5:          
        return -1
    else:
        return 0
        
print greater_less_equal_5(4)
print greater_less_equal_5(5)
print greater_less_equal_5(6)


def the_flying_circus():
    
    if 1 != 0 and 3 > 2:
        return True
    elif 0 == 0 or 2 == 2:
        return False
    else:
        return True

print the_flying_circus()
```

    -1
    0
    1
    True
    

## PygLatin

Now let's take what we've learned so far and write a Pig Latin translator. Pig Latin is a language game, where you move the first letter of the word to the end and add "ay." So "Python" becomes "ythonpay." 


```python
print 'Welcome to the Pig Latin Translator!'

original = raw_input("Enter a word:")
if len(original) > 0 and original.isalpha():
    print original
else:
    print "empty"


pyg = 'ay'

original = raw_input('Enter a word: ')

if len(original) > 0 and original.isalpha():
    word = original.lower()
    first = word[0]
    new_word = word + first + pyg
    new_word = new_word[1:len(new_word)]
    print new_word
else:
    print 'empty'
```

    Welcome to the Pig Latin Translator!
    Enter a word:translator
    translator
    Enter a word: radiator
    adiatorray
    

## Quiz 3

Takeaway: there no limits to the number of `elif`.

## Project Area Calculator

Python is especially useful for doing math and can be used to automate many calculations. In this project, you'll create a calculator than can compute the area of a given shape, as selected by the user. The calculator will be able to determine the area of the following shapes:

- Circle
- Triangle

The program should do the following:

- Prompt the user to select a shape
- Depending on the shape the user selects, calculate the area of that shape
- Print the area of that shape to the user

Python is especially useful for doing math and can be used to automate many calculations.


```python
from math import pi
from time import sleep
from datetime import datetime

now = datetime.now() # from datetime
print "The calculator is starting up at: \n"+str(now)

print "\nCurently: %s/%s/%s %s:%s" %(now.month, now.day, now.year, now.hour, now.minute)

sleep(1) # pause 1 sec

hint = "Don't forget to include the correct units!"


from math import pi
from time import sleep

def question():
    
        option = raw_input("Enter C for Circle or T for Triangle: ")
        if option.upper() == 'C' or option.upper() == 'CIRCLE':
            print circle()
        elif option.upper() == 'T' or option.upper() == 'TRIANGLE':
            print triangle()
        else:
            print "Please answer with a C or T", question() #!!!!!!

def circle():
    
    radius = float(raw_input("Enter radius: "))

    areac = pi * (radius ** 2)
    print "The pie is baking..."
    sleep(1)
    return(str("%.2f" % areac)) # !!!!!
  
def triangle():
    
    base = float(raw_input("Enter base: "))
    height = float(raw_input("Enter height: "))
    areat = base * height / 2
    print "Uni Bi Tri..."
    sleep(1)
    return(str("%.2f" % areat)) # !!!!!

question()
```

    The calculator is starting up at: 
    2016-10-18 14:05:19.204000
    
    Curently: 10/18/2016 14:5
    Enter C for Circle or T for Triangle: T
    Enter base: 10
    Enter height: 5
    Uni Bi Tri...
    25.00
    

# UNIT 4, Functions

## Functions

You might have considered the situation where you would like to reuse a piece of code, just with a few different values. Instead of rewriting the whole code, it's much cleaner to define a function, which can then be used repeatedly.


```python
def tax(billa):
    
    billb = float(billa) * 1.08
    return billb

def tip(billc):
    
    billd = float(billc) * 1.15
    return billd
    
meal_cost = 100.00
meal_with_tax = tax(meal_cost)
print("With tax: %.2f" % meal_with_tax) # !!!!!
meal_with_tip = tip(meal_with_tax)
print("With tip: %.2f" % meal_with_tip)

# The header, the comment, the body:
def spam():
    
    """print the string "Eggs!" to the console."""
    print "Eggs!"
```

    With tax: 108.00
    With tip: 124.20
    

After defining a function, it must be called to be implemented.


```python
def square(n):
    
    """Returns the square of a number."""
    squared = n ** 2
    return("%d squared is %d." % (n, squared))
    
print square(10)
```

    10 squared is 100.
    

Functions can be much more powerful than that. For example, a function can call another function.


```python
n = 1

def one_good_turn(n):
    
    return n + 1
    
def deserves_another(m):
    
    return one_good_turn(m) + 2 # calling a function already defined
```

Again.


```python
def cube(number):
    
    return number ** 3

def by_three(number):
    
    if number % 3 == 0:    
        return cube(number)
    else:
        return False
    
by_three(3)
```




    27



Import modules to use custom functions.


```python
import math

print math.sqrt(25)
```

    5.0
    

However, we only really needed the sqrt function, and it can be frustrating to have to keep typing `math.sqrt()`. It's possible to import only certain variables or functions from a given module (like `pi` above). Pulling in just a single function from a module is called a function import, and it's done with the from keyword.


```python
from math import sqrt # module 'math', function 'sqrt'
from math import pi # module 'math', variable 'pi'
```

Universal `import` can handle all of the variables and functions in a module to avoid to constantly type `math`.


```python
from math import *
```

Universal `import` may look great on the surface, but they're not a good idea for one very important reason: they fill your program with a ton of variable and function names without the safety of those names still being associated with the module(s) they came from.

<sub>dir(), dir</sub>


```python
import math

everything = dir(math)
print everything
```

    ['__doc__', '__name__', '__package__', 'acos', 'acosh', 'asin', 'asinh', 'atan', 'atan2', 'atanh', 'ceil', 'copysign', 'cos', 'cosh', 'degrees', 'e', 'erf', 'erfc', 'exp', 'expm1', 'fabs', 'factorial', 'floor', 'fmod', 'frexp', 'fsum', 'gamma', 'hypot', 'isinf', 'isnan', 'ldexp', 'lgamma', 'log', 'log10', 'log1p', 'modf', 'pi', 'pow', 'radians', 'sin', 'sinh', 'sqrt', 'tan', 'tanh', 'trunc']
    

For these reasons, it's best to stick with either `import module` and type `module.name` or just import specific variables and functions from various modules as needed.

Let's look at some of the functions that are built in to Python (no modules required!).


```python
def distance_from_zero(arg):
    
    return abs(arg)

def biggest_number(arg1, arg2):
    
    return min(arg1, arg2)

def smallest_number(*args):
    
    return min(args)

print distance_from_zero(-10)
```


```python
print biggest_number(-10, -5)
```

    -10
    


```python
print biggest_number(-10, -5, 5, 10) # test
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    <ipython-input-24-40abbc687778> in <module>()
    ----> 1 print biggest_number(-10, -5, 5, 10) # test
    

    TypeError: biggest_number() takes exactly 2 arguments (4 given)



```python
print smallest_number(1, 2)
print smallest_number(3, 4, 5, 6, 7)
print smallest_number(-10, -5, 5, 10)
```

    1
    3
    -10
    


```python
maximum = max(-5, 3, 5, 10)
print maximum

minimum = min(-3, -5)
print minimum

absolute = abs(-42)
print absolute

print type(42) # <type 'int'>
print type(4.2) # <type 'float'>
print type('spam') # <type 'str'>
```

    10
    -5
    42
    <type 'int'>
    <type 'float'>
    <type 'str'>
    

## Taking a Vacation


```python
def hotel_cost(nights):
    
    return 140 * nights

def plane_ride_cost(city):
    
    if city == "Charlotte":
        return 183
    elif city == "Tampa":
        return 220
    elif city == "Pittsburgh":
        return 222
    elif city == "Los Angeles":
        return 475

def rental_car_cost(days):
    
    cost = days * 40
    if days >= 7:
        cost -= 50
    elif days >= 3 and days<7:
        cost -= 20
    else:
        cost
    return cost

def trip_cost(city, days, spending_money):
    
    return rental_car_cost(days) + hotel_cost(days)+plane_ride_cost(city) + spending_money

print trip_cost("Los Angeles", 5, 600)
```

    1955
    

## Quiz 4

OK

## Project Number Guess

Wanna play a game? In this project, we'll build a program that rolls a pair of dice and asks the user to guess a number. Based on the user's guess, the program should determine a winner. If the user's guess is greater than the total value of the dice roll, they win! Otherwise, the computer wins.

The program should do the following:

- Randomly roll a pair of dice
- Add the values of the roll
- Ask the user to guess a number
- Compare the user's guess to the total value
- Decide a winner (the user or the program)
- Inform the user who the winner is


```python
from random import randint
from time import sleep

def get_user_guess():
    
    user_guess = int(raw_input("Guess a number: "))
    return user_guess

def roll_dice(number_of_sides):
    
    first_roll = randint(1, number_of_sides)
    second_roll = randint(1, number_of_sides)
    max_value = number_of_sides * 2
    print "The maximum value is: "+str(max_value)
    sleep(1)
    user_guess = get_user_guess()
    if user_guess > max_value:
        print "Your guess is higher than the max allowed ("+str(max_value)+"). Please, take another guess."
        return # exit the if block is condition met
    else:
        print "Rolling..."
        sleep(1)
        print "First roll is: %d" % (first_roll)
        sleep(1)
        print "Second roll is: %d" % (second_roll)
        total_roll = first_roll + second_roll
        print "Result..."
        sleep(1)
        if user_guess > total_roll:
            print "You win since your guess, "+str(user_guess)+", is greater than the total roll, "+str(total_roll)
            return # exit
        else:
            print "You lose!"
            return # exit

roll_dice(6)
```

    The maximum value is: 12
    Guess a number: 5
    Rolling...
    First roll is: 1
    Second roll is: 2
    Result...
    You win since your guess, 5, is greater than the total roll, 3
    

# UNIT 5, Lists & Dictionaries

## Lists and Dictionaries

Lists are a datatype you can use to store a collection of different pieces of information as a sequence under a single variable name. (Datatypes you've already learned about include strings, numbers, and booleans.)


```python
zoo_animals = ["pangolin", "cassowary", "sloth", "kangourou"];

# You can access an individual item on the list by its index. An index is like an address that identifies the item's place in the list. The index appears directly after the list name, in between brackets, like this: list_name[index].

if len(zoo_animals) > 3:
    print "The first animal at the zoo is the " + zoo_animals[0]
    print "The second animal at the zoo is the " + zoo_animals[1]
    print "The third animal at the zoo is the " + zoo_animals[2]
    print "The fourth animal at the zoo is the " + zoo_animals[3]
```

    The first animal at the zoo is the pangolin
    The second animal at the zoo is the cassowary
    The third animal at the zoo is the sloth
    The fourth animal at the zoo is the kangourou
    


```python
numbers = [5, 6, 7, 8]

print "Adding the numbers at indices 0 and 2..."
print numbers[0] + numbers[2]
print "Adding the numbers at indices 1 and 3..."
print numbers[1] + numbers[3]
```

    Adding the numbers at indices 0 and 2...
    12
    Adding the numbers at indices 1 and 3...
    14
    

A list doesn't have to have a fixed length. You can add items to the end of a list any time you like!


```python
suitcase = []

suitcase.append("sunglasses")
suitcase.append("calculator")
suitcase.append("screen")
suitcase.append("mouse")

list_length = len(suitcase) # Set this to the length of suitcase

print list_length

print "There are %d items in the suitcase." % (list_length)
print suitcase
```

    4
    There are 4 items in the suitcase.
    ['sunglasses', 'calculator', 'screen', 'mouse']
    


```python
suitcase = ["sunglasses", "hat", "passport", "laptop", "suit", "shoes"]

first  = suitcase[0:2] # The first and second items (index zero and one)
middle = suitcase[2:4] # Third and fourth items (index two and three)
last = suitcase[4:6] # The last two items (index four and five)
```

You can slice a string exactly like a list! In fact, you can think of strings as lists of characters: each character is a sequential item in the list, starting from index 0.


```python
animals = "catdogfrog"

cat  = animals[:3] # The first three characters of animals
dog  = animals[3:6] # The fourth through sixth characters
frog = animals[6:] # From the seventh character to the end
```

Sometimes you need to search for an item in a list.


```python
animals = ["aardvark", "badger", "duck", "emu", "fennec fox"]

duck_index = animals.index("duck") # Use index() to find "duck"

print duck_index

animals.insert(duck_index,"cobra")

print animals # Observe what prints after the insert  operation
```

    2
    ['aardvark', 'badger', 'cobra', 'duck', 'emu', 'fennec fox']
    

If you want to do something with every item in the list, you can use a for loop.


```python
my_list = [1,9,3,8,5,7]

for number in my_list:
    print 2 * number
```

    2
    18
    6
    16
    10
    14
    

If your list is a jumbled mess, you may need to `sort()` it.


```python
start_list = [5, 3, 1, 2, 4]
square_list = []

for var in start_list:
    square_list.append(var ** 2)

square_list.sort()

print square_list
```

    [1, 4, 9, 16, 25]
    

A dictionary is similar to a list, but you access values by looking up a key instead of an index. A key can be any string or number. Dictionaries are great for things like phone books (pairing a name with a phone number), login pages (pairing an e-mail address with a username), and more!


```python
residents = {'Puffin' : 104, 'Sloth' : 105, 'Burmese Python' : 106}

print residents['Puffin'] # Prints Puffin's room number
print residents['Sloth']
print residents['Burmese Python']
```

    104
    105
    106
    

An empty pair of curly braces `{}` is an empty dictionary, just like an empty pair of `[]` is an empty list.

Like Lists, Dictionaries are 'mutable'. This means they can be changed after they are created. One advantage of this is that we can add new key-value pairs to the dictionary after it is created.

The length `len()` of a dictionary is the number of key-value pairs it has. Each pair counts only once, even if the value is a list.


```python
menu = {} # Empty dictionary

menu['Chicken Alfredo'] = 14.50 # Adding new key-value pair

print menu['Chicken Alfredo']

menu['General Tao'] = 12.00
menu['Pad Thai'] = 10.50
menu['Poutine'] = 9.00

print "There are " + str(len(menu)) + " items on the menu."
print menu

for key, value in menu.iteritems(): # !!!!!
    print key, value

for key, value in menu.iteritems(): # !!!!!
    print key

for key, value in menu.iteritems(): # !!!!!
    print value
```

    14.5
    There are 4 items on the menu.
    {'Chicken Alfredo': 14.5, 'General Tao': 12.0, 'Poutine': 9.0, 'Pad Thai': 10.5}
    Chicken Alfredo 14.5
    General Tao 12.0
    Poutine 9.0
    Pad Thai 10.5
    Chicken Alfredo
    General Tao
    Poutine
    Pad Thai
    14.5
    12.0
    9.0
    10.5
    

Because dictionaries are mutable, they can be changed in many ways. Items can be removed from a dictionary with the `del()` command.


```python
# key - animal_name : value - location 

zoo_animals = {
'Unicorn' : 'Cotton Candy House',
'Sloth' : 'Rainforest Exhibit',
'Bengal Tiger' : 'Jungle House',
'Atlantic Puffin' : 'Arctic Exhibit',
'Rockhopper Penguin' : 'Arctic Exhibit'
}
```

A dictionary (or list) declaration may break across multiple lines

Removing the 'Unicorn' entry. (Unicorns are incredibly expensive.)


```python
zoo_animals = {
'Unicorn' : 'Cotton Candy House',
'Sloth' : 'Rainforest Exhibit',
'Bengal Tiger' : 'Jungle House',
'Atlantic Puffin' : 'Arctic Exhibit',
'Rockhopper Penguin' : 'Arctic Exhibit'
}

del zoo_animals['Unicorn']
del zoo_animals['Sloth']
del zoo_animals['Bengal Tiger']
zoo_animals['Rockhopper Penguin'] = 'Cotton Candy House'

print zoo_animals
```

    {'Atlantic Puffin': 'Arctic Exhibit', 'Rockhopper Penguin': 'Cotton Candy House'}
    

Sometimes you need to remove something from a list.


```python
backpack = ['xylophone', 'dagger', 'tent', 'bread loaf']

backpack.remove('dagger')
```

We can create a dictionary that holds many types of values.

<sub>extract, sort, remove</sub>


```python
inventory = {
    'gold' : 500,
    'pouch' : ['flint', 'twine', 'gemstone'], # Assigned a new list to 'pouch' key
    'backpack' : ['xylophone','dagger', 'bedroll','bread loaf']
}

print inventory

# Adding a key 'burlap bag' and assigning a list to it
inventory['burlap bag'] = ['apple', 'small ruby', 'three-toed sloth']

print inventory
```

    {'backpack': ['xylophone', 'dagger', 'bedroll', 'bread loaf'], 'pouch': ['flint', 'twine', 'gemstone'], 'gold': 500}
    {'backpack': ['xylophone', 'dagger', 'bedroll', 'bread loaf'], 'pouch': ['flint', 'twine', 'gemstone'], 'burlap bag': ['apple', 'small ruby', 'three-toed sloth'], 'gold': 500}
    


```python
# Sorting the list found under the key 'pouch'
inventory['pouch'].sort() 

print inventory
```

    {'backpack': ['xylophone', 'dagger', 'bedroll', 'bread loaf'], 'pouch': ['flint', 'gemstone', 'twine'], 'burlap bag': ['apple', 'small ruby', 'three-toed sloth'], 'gold': 500}
    


```python
inventory['pocket'] = ['seashell', 'strange berry', 'lint']

print inventory
```

    {'pocket': ['seashell', 'strange berry', 'lint'], 'backpack': ['xylophone', 'dagger', 'bedroll', 'bread loaf'], 'pouch': ['flint', 'gemstone', 'twine'], 'burlap bag': ['apple', 'small ruby', 'three-toed sloth'], 'gold': 500}
    


```python
inventory['backpack'].sort()

print inventory
```

    {'pocket': ['seashell', 'strange berry', 'lint'], 'backpack': ['bedroll', 'bread loaf', 'dagger', 'xylophone'], 'pouch': ['flint', 'gemstone', 'twine'], 'burlap bag': ['apple', 'small ruby', 'three-toed sloth'], 'gold': 500}
    


```python
inventory['backpack'].remove('dagger')

print inventory
```

    {'pocket': ['seashell', 'strange berry', 'lint'], 'backpack': ['bedroll', 'bread loaf', 'xylophone'], 'pouch': ['flint', 'gemstone', 'twine'], 'burlap bag': ['apple', 'small ruby', 'three-toed sloth'], 'gold': 500}
    


```python
inventory['gold'] += 50

print inventory
```

    {'pocket': ['seashell', 'strange berry', 'lint'], 'backpack': ['bedroll', 'bread loaf', 'xylophone'], 'pouch': ['flint', 'gemstone', 'twine'], 'burlap bag': ['apple', 'small ruby', 'three-toed sloth'], 'gold': 550}
    

## A Day at the Supermarket

`for` loops allow us to iterate through all of the elements in a list from the left-most (or zeroth element) to the right-most element.


```python
names = ["Adam", "Alex", "Mariah", "Martine", "Columbus"]

for items in names:
    print items
```

    Adam
    Alex
    Mariah
    Martine
    Columbus
    

You can also use a for loop on a dictionary to loop through its keys.


```python
webster = {
    "Aardvark" : "A star of a popular children's cartoon show.",
    "Baa" : "The sound a goat makes.",
    "Carpet": "Goes on the floor.",
    "Dab": "A small amount."
}

for item in webster:
    print webster[item]
```

    A star of a popular children's cartoon show.
    Goes on the floor.
    A small amount.
    The sound a goat makes.
    

While looping, you may want to perform different actions depending on the particular item in the list.


```python
a = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]

for item in a:
    if item % 2 == 0:
        print item
```

    0
    2
    4
    6
    8
    10
    12
    

Functions can also take lists as inputs and perform various operations on those lists.


```python
def count_small(numbers):
    
    total = 0
    for n in numbers:
        if n < 10:
            total = total + 1
    return total

lost = [4, 8, 15, 16, 23, 42]
small = count_small(lost)

print small
```

    2
    

You can loop through strings the same way you loop through lists!


```python
for letter in "Codecademy":
    print letter
    
word = "Programming is fun!"

for letter in word:
    # Only print out the letter i
    if letter == "i":
        print letter
```

    C
    o
    d
    e
    c
    a
    d
    e
    m
    y
    i
    i
    

You are now the proud owner of your very own Codecademy brand supermarket. For paperwork and accounting purposes, let's record the total value of your inventory.


```python
prices = {
    "banana" : 4,
    "apple" : 2,
    "orange" : 1.5,
    "pear" : 3
    }

stock = {
    "banana" : 6,
    "apple" : 0,
    "orange" : 32,
    "pear" : 15
    }

total = 0

for item in prices:
    print item # print key
    print "price: %s" % prices[item] # print value
    print "stock: %s" % stock[item]
    print prices[item]*stock[item]
    total += prices[item]*stock[item]

print total
```

    orange
    price: 1.5
    stock: 32
    48.0
    pear
    price: 3
    stock: 15
    45
    banana
    price: 4
    stock: 6
    24
    apple
    price: 2
    stock: 0
    0
    117.0
    

In order for customers to order online, we are going to have to make a consumer interface.


```python
shopping_list = ["banana", "orange", "apple"]

stock = {
    "banana" : 6,
    "apple" : 0,
    "orange" : 32,
    "pear" : 15
}
    
prices = {
    "banana" : 4,
    "apple" : 2,
    "orange" : 1.5,
    "pear" : 3
}

def compute_bill(food):
    
    total = 0
    for item in food:
        if stock[item] > 0:
            total += prices[item] # you only pick one from the stock!
            stock[item] = stock[item] - 1 # the stock goes down by 1
    print total
    return food

print compute_bill(shopping_list)
```

    5.5
    ['banana', 'orange', 'apple']
    

## Quiz 5

OK

## Project Rock, Paper, Scissors

In this project, we'll build Rock-Paper-Scissors!

The program should do the following:

- Prompt the user to select either Rock, Paper, or Scissors
- Instruct the computer to randomly select either Rock, Paper, or Scissors
- Compare the user's choice and the computer's choice
- Determine a winner (the user or the computer)
- Inform the user who the winner is


```python
from random import randint
from time import sleep

options = ["R", "P", "S"]
LOSE = "You lost!" # constant, uppercase
WIN = "You win!"

def decide_winner(user_choice, computer_choice):
    
    print("You picked: "+str(user_choice))
    print "Computer selecting..."
    
    sleep(1)
    
    print("Computer picks: "+str(computer_choice))
    
    user_choice_index = options.index(user_choice)
    computer_choice_index = options.index(computer_choice) # !!!!!
    
    if user_choice_index == computer_choice_index:
        print "Tie!"
    elif user_choice_index == 0 and computer_choice_index == 2:
        print WIN
    elif user_choice_index == 1 and computer_choice_index == 0:
        print WIN
    elif user_choice_index == 2 and computer_choice_index == 1:
        print WIN
    elif user_choice_index > 2:
        print "Invalid choice!!!"
    else:
        print LOSE

def play_RPS():
    
    print "Let's pay Rock-Paper-Scissors"
    
    user_choice = raw_input("Select R for Rock, P for Paper, or S for Scissors: ")
    
    sleep(1)
    
    user_choice = user_choice.upper()
    # computer_choice = options[randint(0,2)] 
    # pull out an element from a list, the 1st (0) out of 3 (2)
    
    computer_choice = options[randint(0,len(options)-1)] 
    # This will ensure that if we ever add more options to the game, we won't have to change this line of code.
    
    decide_winner(user_choice, computer_choice)

play_RPS()
```

    Let's pay Rock-Paper-Scissors
    Select R for Rock, P for Paper, or S for Scissors: r
    You picked: R
    Computer selecting...
    Computer picks: S
    You win!
    

# UNIT 6, Student Becomes the Teacher

## Student Becomes the Teacher

Make a gradebook for all of your students.

First, create 3 dictionaries.

Second, add names, marks...


```python
lloyd = {
    "name" : "Lloyd",
    "homework" : [90.0, 97.0, 75.0, 92.0],
    "quizzes" : [88.0, 40.0, 94.0],
    "tests" : [75.0, 90.0]
}

alice = {
    "name": "Alice",
    "homework" : [100.0, 92.0, 98.0, 100.0],
    "quizzes" : [82.0, 83.0, 91.0],
    "tests" : [89.0, 97.0]
}

tyler = {
    "name" : "Tyler",
    "homework" : [0.0, 87.0, 75.0, 22.0],
    "quizzes" : [0.0, 75.0, 78.0],
    "tests" : [100.0, 100.0]
}
```

Third, make a list.


```python
students= [lloyd, alice, tyler]

cases = ["homework", "quizzes", "tests"]

w_calc = [0.10, 0.30, 0.60]

all_average = 0.0
```

Four, print out.


```python
print "\nStudents' Grades".upper()

print ""

for student in students:
    print student["name"].upper()
    print "Homework"
    print student["homework"]
    print "Quizzes"
    print student["quizzes"]
    print "Tests"
    print student["tests"]
    print ""
```

    
    STUDENTS' GRADES
    
    LLOYD
    Homework
    [90.0, 97.0, 75.0, 92.0]
    Quizzes
    [88.0, 40.0, 94.0]
    Tests
    [75.0, 90.0]
    
    ALICE
    Homework
    [100.0, 92.0, 98.0, 100.0]
    Quizzes
    [82.0, 83.0, 91.0]
    Tests
    [89.0, 97.0]
    
    TYLER
    Homework
    [0.0, 87.0, 75.0, 22.0]
    Quizzes
    [0.0, 75.0, 78.0]
    Tests
    [100.0, 100.0]
    
    

Compute averages.


```python
def average(numbers):
    
    total = sum(numbers)
    temp = float(total) / len(numbers)
    return temp

print "Students' Averages".upper()

print ""

for c in cases:
    cc = c.upper()
    print cc
    for student in students:
        numbers = student[c]
        calc = round(average(numbers),1)
        print student["name"]
        print calc
    print ""
```

    STUDENTS' AVERAGES
    
    HOMEWORK
    Lloyd
    88.5
    Alice
    97.5
    Tyler
    46.0
    
    QUIZZES
    Lloyd
    74.0
    Alice
    85.3
    Tyler
    51.0
    
    TESTS
    Lloyd
    82.5
    Alice
    93.0
    Tyler
    100.0
    
    

Compute weighted averages.


```python
def w_average(marks):
    
    #w_calc = [0.10, 0.30, 0.60]
    s_calc = 0
    w = 0
    while w < len(w_calc):
        s_calc += w_calc[w] * marks[w]
        w += 1
    return s_calc

def get_letter_grade(score):
    
    if score >= 90:
        return "A"
    elif score >= 80:
        return "B"
    elif score >= 70:
        return "C"
    elif score >= 60:
        return "D"
    else:
        return "F"

def get_class_average(ind):
    class_total = round(ind / len(students), 1)
    return class_total

print "Students' Weighted Average".upper()

print " Ponderation [Homeworks, Quizzes, Tests]: ["+str(float(w_calc[0])*100)+", "+str(float(w_calc[1])*100)+", "+str(float(w_calc[2])*100)+"]"

print ""

for student in students:
    print(student["name"] + "'s marks are:").upper()
    l_calc = []
    for c in cases:    
        numbers = student[c]
        calc = round(average(numbers),1)
        l_calc.append(calc)
    print l_calc
    print("For a weighted average of:")
    ind_average = round(w_average(l_calc),1)
    print ind_average
    print("Standing for a:")
    print get_letter_grade(ind_average)
    all_average += ind_average
    print ""

print("Finally, The class average is:").upper()
print get_class_average(all_average)
```

    STUDENTS' WEIGHTED AVERAGE
     Ponderation [Homeworks, Quizzes, Tests]: [10.0, 30.0, 60.0]
    
    LLOYD'S MARKS ARE:
    [88.5, 74.0, 82.5]
    For a weighted average of:
    80.5
    Standing for a:
    B
    
    ALICE'S MARKS ARE:
    [97.5, 85.3, 93.0]
    For a weighted average of:
    91.1
    Standing for a:
    A
    
    TYLER'S MARKS ARE:
    [46.0, 51.0, 100.0]
    For a weighted average of:
    79.9
    Standing for a:
    C
    
    FINALLY, THE CLASS AVERAGE IS:
    83.8
    

# UNIT 7, Lists and Functions

## Lists and Functions

What you can do with a list: extract, add, append, remove, pop out, delete.


```python
n = [1, 3, 5]
print n[1]

n[1] = n [1] * 5
print n

# Add elements
n.append(4)
print n

# Remove elements
n.pop(0)
print n
```

    3
    [1, 15, 5]
    [1, 15, 5, 4]
    [15, 5, 4]
    

What you can do with functions.

Multiply, divide.


```python
number = 5

def my_function(x):
    
    return x * 3

# Print my_function(5)
print my_function(number)
```

    15
    

Add, substract.


```python
m = 5
n = 13

def add_function(x,y):
    
    return x + y

print add_function(m, n)
```

    18
    

Concatenate.


```python
n = "Hello"

def string_function(s):
    
    return s + " world"

print string_function(n)
```

    Hello world
    

Show all.


```python
n = [3, 5, 7]

def list_function(x):
    
    return x

print list_function(n)
```

    [3, 5, 7]
    

Show some.


```python
def list_function(x):
    
    return x[1]

n = [3, 5, 7]

print list_function(n)
```

    5
    

Extract and modify.


```python
def list_function(x):
    
    x[1] = x[1] + 3
    return x

n = [3, 5, 7]

print list_function(n)
```

    [3, 8, 7]
    

Add elements.


```python
n = [3, 5, 7]

def list_extender(lst):
    
    lst.append(9)
    return lst

print list_extender(n)
```

    [3, 5, 7, 9]
    

Remove elements.


```python
n = [3, 5, 7]

def list_shorter(lst):
    
    lst.remove(5)
    return lst

print list_shorter(n)
```

    [3, 7]
    

Pop out the 2nd element.


```python
n = [3, 5, 7]

def list_extract(lst):
    
    lst.pop(1)
    return lst

print list_extract(n)
```

    [3, 7]
    

Loop through each element.


```python
n = [3, 5, 7]

def print_list(x):
    
    for i in range(0, len(x)):
        print x[i]

print print_list(n)
```

    3
    5
    7
    None
    

Loop, transform each element.


```python
n = [3, 5, 7]

def double_list(x):
    
    for i in range(0, len(x)):
        x[i] = x[i] * 2
    return x

print double_list(n)
```

    [6, 10, 14]
    

Loop, transform each element.


```python
def my_function(x):
    
    for i in range(0, len(x)):
        x[i] = x[i] * 2
    return x

print my_function(range(3))

print range(6) # => [0,1,2,3,4,5]
print range(1,6) # => [1,2,3,4,5]
print range(1,6,3) # => [1,4]
```

    [0, 2, 4]
    [0, 1, 2, 3, 4, 5]
    [1, 2, 3, 4, 5]
    [1, 4]
    

Loop, fill the variable with `+=` (or `-=`, `*=`, `/=`)


```python
n = [3, 5, 7]

def total(numbers):
    
    result = 0 # empty variable
    for item in numbers:
        result += item
    return result
```

Empty variable, loop, fill the variable.


```python
n = ["Michael", "Lieberman"]

def join_strings(words):
    
    result = ""
    for item in words:
        result = result + item
    return result

print join_strings(n)
```

    MichaelLieberman
    

Join (not add up) the list. You want this to `print [1, 2, 3, 4, 5, 6]`.


```python
m = [1, 2, 3]
n = [4, 5, 6]

def join_lists(x,y):
    return x + y

print join_lists(m, n)
```

    [1, 2, 3, 4, 5, 6]
    

List of lists. Several loops.


```python
n = [
    [1, 2, 3],
    [4, 5, 6, 7, 8, 9]
]

def flatten(lists):
    
    results = []
    for lst in lists:
        for num in range(len(lst)):
            results.append(lst[num])
    return results

print flatten(n)
```

    [1, 2, 3, 4, 5, 6, 7, 8, 9]
    

Use `range(len(lst))`.

<sub>range, length</sub>


```python
print range(6) # => [0,1,2,3,4,5]
```

    [0, 1, 2, 3, 4, 5]
    

## Battleship!

This first script is incomplete (work in progress).
The next script is functional.


```python
from random import randint

board = []

for x in range(5):  # 0, 1, 2, 3, 4 (stop before 5)
    board.append(["O"] * 5) # print 5 rows of 5 'O'

def print_board(board):
    
    for row in board:
        # print row # print ['O', 'O', 'O', 'O', 'O'] on 5 rows
        print " ".join(row) # print O O O O O 

print "Let's play Battleship!"

def random_row(board): # hide the ship at r-c
    
    return randint(0,len(board) - 1)

def random_col(board):
    
    return randint(0,len(board) - 1)

print random_row(board)
print random_col(board)

guess_row = int(raw_input("Guess Row (1 to 5):")) # involve the player
guess_col = int(raw_input("Guess Col (1 to 5):"))

print ship_col # print ship position
print ship_row

if (guess_row == ship_row) and (guess_col == ship_col):
    print "Congratulations! You sank my battleship!"
    guess_row=guess_row-1
    guess_col=guess_col-1
    board[guess_row][guess_col]="S"
    print print_board(board)
else:
    #print "You missed my battleship!"
    if guess_row not in range(5) or guess_row == 0 or guess_col not in range(5) or guess_col == 0: # condition for wrong entries
        print "Oops, that's not even in the ocean."
    elif board[guess_row][guess_col] == "X":
        print "You guessed that one already."
    else:
        print "You missed my battleship!"

guess_row = guess_row - 1 # transform the numbers, 1 becomes 0...
guess_col = guess_col - 1

board[guess_row][guess_col] = "X" # replace the 'O'
print print_board(board)
```

    Let's play Battleship!
    4
    0
    Guess Row (1 to 5):1
    Guess Col (1 to 5):2
    


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-87-efd1e0de637a> in <module>()
         24 guess_col = int(raw_input("Guess Col (1 to 5):"))
         25 
    ---> 26 print ship_col # print ship position
         27 print ship_row
         28 
    

    NameError: name 'ship_col' is not defined


## Battleship FINAL!


```python
from random import randint

board = []

for x in range(5):
    board.append(["O"] * 5)

def print_board(board):
    
    for row in board:
        print " ".join(row)

print "\nLet's play Battleship! You have 4 strikes to sink by ship.\n"
print_board(board)

def random_row(board):
    
    return randint(0, len(board) - 1)

def random_col(board):
    
    return randint(0, len(board) - 1)

ship_row = random_row(board)
ship_col = random_col(board)
#ship_row = 1 to test and fix to (1,1)
#ship_col = 1

for turn in range(5):
    turn += 1
    if turn == 5:
        print "\nGame Over"
        print "The ship was here => I\n"
        board[ship_row - 1][ship_col - 1] = "I"
        print_board(board)
        break
    else:
        print "\nTurn", turn

        guess_row = int(raw_input("Guess Row (1 to 5): "))
        guess_col = int(raw_input("Guess Col (1 to 5): "))

        if (guess_row == ship_row) and (guess_col == ship_col):
            print "\nCongratulations! You sank my battleship!\n"

            guess_row = guess_row - 1
            guess_col = guess_col - 1
            board[guess_row][guess_col] = "S"

            print_board(board)
            print "\nGame Over"
            break

        elif (guess_row < 1 or guess_row > 5) or (guess_col < 1 or guess_col > 5):
            print "\nOops, that's not even in the ocean.\n"

        elif board[guess_row - 1][guess_col - 1] == "X":
            print "\nYou guessed that one already.\n"
            print_board(board)
            
        else:
            print "\nYou missed my battleship!\n"
            board[guess_row - 1][guess_col - 1] = "X"
            print_board(board)
```

    
    Let's play Battleship! You have 4 strikes to sink by ship.
    
    O O O O O
    O O O O O
    O O O O O
    O O O O O
    O O O O O
    
    Turn 1
    Guess Row (1 to 5): 1
    Guess Col (1 to 5): 2
    
    You missed my battleship!
    
    O X O O O
    O O O O O
    O O O O O
    O O O O O
    O O O O O
    
    Turn 2
    Guess Row (1 to 5): 2
    Guess Col (1 to 5): 2
    
    You missed my battleship!
    
    O X O O O
    O X O O O
    O O O O O
    O O O O O
    O O O O O
    
    Turn 3
    Guess Row (1 to 5): 3
    Guess Col (1 to 5): 5
    
    You missed my battleship!
    
    O X O O O
    O X O O O
    O O O O X
    O O O O O
    O O O O O
    
    Turn 4
    Guess Row (1 to 5): 4
    Guess Col (1 to 5): 3
    
    Congratulations! You sank my battleship!
    
    O X O O O
    O X O O O
    O O O O X
    O O S O O
    O O O O O
    
    Game Over
    

Joining.

<sub>join, split</sub>


```python
letters = ['a', 'b', 'c', 'd']

print " ".join(letters) # a b c d
print "---".join(letters) # #---b---c---d
```

    a b c d
    a---b---c---d
    

Randomizing.

<sub>random, rand</sub>


```python
from random import randint

coin = randint(0, 1) # randint(low, high)
dice = randint(1, 6)
```

## Quiz 7

Takeaway.


```python
my_list = [1, 3, 5, 7]

my_list.pop(3) # remove the 4th
my_list.remove(3) # remove the '3'

range(0, len(my_list)) # every list item
range(0, len(my_list), 2) # every other list item
```




    [0]



# UNIT 8, Loops

## Loops

A `while` loop is a sort of `if`.


```python
count = 0

if count <= 9: # 
    print "Hello, I am an if statement and count is", count
```

    Hello, I am an if statement and count is 0
    


```python
while count <= 9: # similar to if: executes as long as the condition is true
    print "Hello, I am a while and count is", count
    count += 1
```

    Hello, I am a while and count is 0
    Hello, I am a while and count is 1
    Hello, I am a while and count is 2
    Hello, I am a while and count is 3
    Hello, I am a while and count is 4
    Hello, I am a while and count is 5
    Hello, I am a while and count is 6
    Hello, I am a while and count is 7
    Hello, I am a while and count is 8
    Hello, I am a while and count is 9
    

A `while` loop allows control (checkpoint, a switch, on and off).


```python
loop_condition = True

while loop_condition: # On
    print "I am a loop"
    loop_condition = False # Off
```

    I am a loop
    


```python
num = 1

while num <= 10: # the condition
    print num ** 2
    num += num ** (1/2)
    print num
```

    1
    2
    4
    3
    9
    4
    16
    5
    25
    6
    36
    7
    49
    8
    64
    9
    81
    10
    100
    11
    

A common application of a `while` loop is to check user input to see if it is valid.


```python
choice = raw_input('Enjoying the course? (y/n)')

while choice != "y" and choice != "n":
    choice = raw_input("Sorry, I didn't catch that. Enter again (case sensitive): ")
```

    Enjoying the course? (y/n)y
    

`break` means "exit the current loop". Opposite to `break` is `continue`.


```python
count = 0

while True:
    print count
    count += 1
    if count >= 10:
        break
```

    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    

`while`/`else` are like `if`/`else`; `else` is executed when `while` is false.


```python
import random

print "Lucky Numbers! 3 numbers will be generated."
print "If one of them is a '5', you lose!"

count = 0

while count < 3:
    num = random.randint(1, 6)
    print num
    if num == 5:
        print "Sorry, you lose!"
        break
    count += 1
else:
    print "You win!"
```

    Lucky Numbers! 3 numbers will be generated.
    If one of them is a '5', you lose!
    5
    Sorry, you lose!
    

Guess game.


```python
from random import randint

# Generates a number from 1 through 10 inclusive
random_number = randint(1, 10)

# print random_number
guesses_left = 3
print "Guess right!"

while guesses_left > 0:
    print "You have "+str(guesses_left)+" attempts."
    guess = raw_input("Guess a number from 1 to 10: ")
    if int(guess) == random_number:
        print "You win!"
        break
    elif guesses_left == 1:
        print "You lose."
        break
    else:
        guesses_left -= 1
        print "Try again."
```

    Guess right!
    You have 3 attempts.
    Guess a number from 1 to 10: 2
    Try again.
    You have 2 attempts.
    Guess a number from 1 to 10: 6
    Try again.
    You have 1 attempts.
    Guess a number from 1 to 10: 9
    You lose.
    

`if` loop.


```python
print "Counting..."

for i in range(20):
    print i
```

    Counting...
    0
    1
    2
    3
    4
    5
    6
    7
    8
    9
    10
    11
    12
    13
    14
    15
    16
    17
    18
    19
    

Create a list.


```python
hobbies = []

print hobbies

for i in range(3):
    hobby = raw_input("Enter a hobby: ")
    hobbies.append(hobby)

print hobbies
```

    []
    Enter a hobby: fishing
    Enter a hobby: skiing
    Enter a hobby: knitting!!!
    ['fishing', 'skiing', 'knitting!!!']
    

Run though a string, but each character will be spaced out.


```python
thing = "spam!"

for c in thing:
    print c

word = "eggs!"

for char in word:
    print char, # , print on the same line
```

    s
    p
    a
    m
    !
    e g g s !
    

Replace a character in a string. `,` print on the same line.


```python
phrase = "A bird in the hand..."

for char in phrase:
    if char == "A" or char == "a":
        print "X",
    else:
        print char,
```

    X   b i r d   i n   t h e   h X n d . . .
    

Run though a list.


```python
numbers  = [7, 9, 12, 54, 99]

print "This list contains: "

for num in numbers:
    print num

for numm in numbers:
    print numm ** 2,
```

    This list contains: 
    7
    9
    12
    54
    99
    49 81 144 2916 9801
    

Run though a dictionary.


```python
d = {'a' : 'apple', 'b' : 'berry', 'c' : 'cherry'}

for key in d:
    # key:value
    print key+" "+d[key]
    print key # key
    print d[key] # value
```

    a apple
    a
    apple
    c cherry
    c
    cherry
    b berry
    b
    berry
    

Enumerate a list (numbers and members).


```python
choices = ['pizza', 'pasta', 'salad', 'nachos']

print 'Your choices are:'
for index, item in enumerate(choices):
    print index + 1, item
```

    Your choices are:
    1 pizza
    2 pasta
    3 salad
    4 nachos
    

Multiple lists.


```python
list_a = [3, 9, 17, 15, 19]
list_b = [2, 4, 8, 10, 30, 40, 50, 60, 70, 80, 90]

for a, b in zip(list_a, list_b):
    if a > b: 
        print a
    elif a == b:
        print "-"
    else:
        print b
```

    3
    9
    17
    15
    30
    

List with concatenation.


```python
fruits = ['banana', 'apple', 'orange', 'tomata', 'pear', 'grape']

print 'You have...'

for f in fruits:
    if f == 'tomato':
        print 'A tomato is not a fruit!' # (It actually is.)
        break
    print ', a', f,
else:
    print '; A fine selection of fruits!'
```

    You have...
    , a banana , a apple , a orange , a tomata , a pear , a grape ; A fine selection of fruits!
    

Remove the `break`.


```python
fruits = ['banana', 'apple', 'orange', 'tomata', 'pear', 'grape']

print 'You have...'

for f in fruits:
    if f == 'tomato':
        print 'A tomato is not a fruit!' # (It actually is.)
    else:    
        print ', a', f,
else:
    print '; A fine selection of fruits!'
```

    You have...
    , a banana , a apple , a orange , a tomata , a pear , a grape ; A fine selection of fruits!
    

## Practice Makes Perfect

Is it even?


```python
def is_even(x):
    
    if x % 2 == 0:
        return True # if x is even
    else:
        return False

print is_even(2)
print is_even(3)
```

    True
    False
    

Or not?


```python
n = -1.0

print(n - round(n,0))

def is_int(x):
    
    if (x - round(x,0)) == 0:
        return True
    else:
        return False

print is_int(7.0)
print is_int(7.5)
print is_int(-1)
```

    0.0
    True
    False
    True
    

Summing the digits of a number.


```python
def digit_sum(n):
    
    liss = []
    n = str(n) # from integers to characters
    for char in n:
        liss.append(char) # populate liss
        total = 0
        for i in range(len(liss)):
            liss[i] = int(liss[i]) # back to integers
            total += liss[i] # sum them up
    return total

print digit_sum(1234)
print digit_sum(8888)
```

    10
    32
    

What is the factorial?


```python
def factorial(x):
    
    if x == 1 or x == 0:
        return 1
    else:
        result = 1
        while x > 0:
            # say x = 4
            # 1 * 4 = 4
            # 4 * 3 = 12
            # 12 * 2 = 24
            # 24 * 1 = 24
            result *= x
            x -= 1

    return result 

print factorial(1)
print factorial(2)
print factorial(3)
print factorial(4)
print factorial(5)
```

    1
    2
    6
    24
    120
    

Is it a prime number? (Check the web for the list of prime numbers.)


```python
def is_prime(x):
    
    if (x > 1): # to catch greater than 1
        for n in range(2,(x - 1)): # range 2 - 1 less than x
            if x % n == 0:
                print x
                return False
    else: # ro catch 0 and 1
        print x
        return False
    print x # the input
    return True # the output, will be printed when the function will be called

for ii in range(24):
    print is_prime(ii),
```

    0
    False 1
    False 2
    True 3
    True 4
    False 5
    True 6
    False 7
    True 8
    False 9
    False 10
    False 11
    True 12
    False 13
    True 14
    False 15
    False 16
    False 17
    True 18
    False 19
    True 20
    False 21
    False 22
    False 23
    True
    

Reverse a string.


```python
def reverse(text):
    
    count = len(text) - 1 # start at the end
    
    print text
    print count # 3 letters will be 0,1,2,3 or 3

    reversed_text = "" # empty string
    
    print reversed_text
    
    while count >= 0:
        reversed_text += text[count] # adding the right-most letter
        count -= 1 # decrement count
    return reversed_text
    
print reverse("make")
print reverse("codeacademy")
```

    make
    3
    
    ekam
    codeacademy
    10
    
    ymedacaedoc
    

Remove vowels in apunctuation word (could work for punctuation too).


```python
def anti_vowel(text):
    
    vowels = "aAeEiIoOuU"
    for char in text:
        for vow in vowels:
            if vow == char:
                text = text.replace(char,"")
    return text

print anti_vowel("allo")
```

    ll
    

Remove all but punctuation.


```python
def anti_vowel(text):
    
    text = text.lower()
    vowels = "abcdefghijklmnopqrstuvwxyz1234567890$-"
    
    for char in text:
        for vow in vowels:
            if vow == char:
                text = text.replace(char,"")
    for char in text:
        if char == " ":
            text = text.replace(char,"")
    return text

print anti_vowel("The plethora of object oriented approaches leads to a natural question. Which one should you use? With respect to S3 and S4 classes, the S3 class is more flexible, and the S4 class is a more structured approach. This is a nice way of saying that the S3 class approach is for unaware slobs and is a sloppy way to shoot yourself in the foot, while the S4 class is for uptight pedants. Our focus here is on S3 classes. Before we delve into the details of S3 classes we need to talk about memory environments. These can be used to great effect in S3 classes to make your codes totally incomprehensible. On the down side they help give S3 classes their flexibility. An environment can be thought of as a local scope. It has a set of variables associated with it. You can access those variables if you have the \"ID\" associated with the environment. There are a number of commands you can use to manipulate and obtain the pointers to your environments. You can also use the assign and get commands to set and get the values of variables within an environment.")
```

    .?,,.,.......""...
    

Scrabble scoring.


```python
score = {"a": 1, "c": 3, "b": 3, "e": 1, "d": 2, "g": 2, 
         "f": 4, "i": 1, "h": 4, "k": 5, "j": 8, "m": 3, 
         "l": 1, "o": 1, "n": 1, "q": 10, "p": 3, "s": 1, 
         "r": 1, "u": 1, "t": 1, "w": 4, "v": 4, "y": 4, 
         "x": 8, "z": 10}

def scrabble_score(word):
    
    word2 = word.lower()
    
    print word2+":",
    points = 0
    for letter in word2:
        if letter == str(letter):
            points += score[letter]
    return points

print scrabble_score("ab")
print scrabble_score("allo")
print scrabble_score("xylophone")
print scrabble_score("coding")
print scrabble_score("yak")
```

    ab: 4
    allo: 4
    xylophone: 24
    coding: 10
    yak: 10
    

Censor a word in a string.

<sub>length</sub>


```python
def censor(text,word_to_censor):
    
    text = text.split(' ')
    for word in range(0,len(text)):
        if text[word] == word_to_censor:
            text[word] = "*" * len(text[word]) * 2
    return " ".join(text) # join the w separated by spaces

print censor("it is two days", "two")
```

    it is ****** days
    

Count items is a list.


```python
def count(sequence, item):
    
    sequence = list(sequence)
    count = 0
    
    for i in sequence:
        if i == item:
            count += 1
    return count
    
list2 = [1,3,1,5]
list3 = ["a","b","c","a"]
list4 = ("a","b","c","a")
list5 = (1,2,3,1,1)

print count(list2,1)
print count(list3,1)
print count(list4,1)
print count(list5,1)
```

    2
    0
    0
    3
    

Extract even numbers from a list.


```python
def purify(listing):
    
    listing = list(listing)
    listing2 = []
    
    for l in listing:
        if l % 2 == 0:
            listing2.append(l)
    return listing2

case1 = [1,2,3,4]

print purify(case1)
```

    [2, 4]
    

Compute a product.


```python
def product(listing):
    
    print listing
    result = 1
    for l in listing:
        result = result * l
    return result

case1 = [1,2,3]
case2 = (5,10,15)

print product(case1)
print product(case2)
```

    [1, 2, 3]
    6
    (5, 10, 15)
    750
    

Remove duplicates from a list.


```python
def remove_duplicates(listing):
    
    print listing
    
    listing = list(listing)
    listing2 = []
    
    for l in listing:
        if l not in listing2:
            listing2.append(l)
    return listing2

case1 = [1,2,3,3,4]
case2 = (1,6,1,4,2,8,2,1,6,7,4,6)

print remove_duplicates(case1)
print remove_duplicates(case2)
```

    [1, 2, 3, 3, 4]
    [1, 2, 3, 4]
    (1, 6, 1, 4, 2, 8, 2, 1, 6, 7, 4, 6)
    [1, 6, 4, 2, 8, 7]
    

Extract the median from an unordered list of numbers.


```python
def median(listing):
    
    median_no = 0
    median_low = 0
    median_high = 0
    low = 0
    high = 0
    
    print listing
    
    listing = sorted(listing)
    
    if len(listing) % 2 == 0:
        low = len(listing)/2 - 1 # 6/2 = 3 -1 = 2 or the 3rd
        high = len(listing)/2 # 6/2 = 3 or the 4th
        median_low = float(listing[low]) # extract the 3rd of 6
        median_high = float(listing[high]) # the 4th of 6
        median_no = (median_low + median_high)/2
    else:
        median_no = listing[(len(listing))/2] # on 5, the / will yield 2.5, but coerced to the integer 2 or the 3rd
    return median_no

case1 = (7,12,3,1,6)
case2 = (7,12,3,1,6,17)

print median(case1)
print median(case2)
```

    (7, 12, 3, 1, 6)
    6
    (7, 12, 3, 1, 6, 17)
    6.5
    

## Quiz 8

Takeaway: built-in functions.


```python
x = [1, 2, 3]
y = [4, 5, 6]

zipped = zip(x, y)
# zipped = [(1, 4), (2, 5), (3, 6)]

x2, y2 = zip(*zipped)

x == list(x2) and y == list(y2)
# True
```




    True




```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']

list(enumerate(seasons))
# [(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]

list(enumerate(seasons, start=1))
# [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```




    [(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]



## Project Command Line Calendar

In this project, we'll build a basic calendar that the user will be able to interact with from the command line. The user should be able to choose to:

- View the calendar
- Add an event to the calendar
- Update an existing event
- Delete an existing event


```python
from time import sleep, strftime

his_name = raw_input("What is your first name? ")
his_name = str(his_name)
# calendar will store the dates as keys and the events as values

calendar = {}

def welcome():

    print("Welcome " + his_name +".")

    print("Calendar starting...")
    sleep(0.5)
    print("Today is: " + strftime("%A, %B %d, %Y"))
    print("It is currently: " + strftime("%H:%M:%S"))
    sleep(0.5)

def start_calendar():

    welcome()
    print("What would you like to do?")
    print(calendar)
    start = True
  
    while start:
        user_choice = raw_input("Choose between: 'A' to Add, 'U' to Update, 'V' to View, 'D' to Delete or 'X' to Exit? ").upper()
        
        if user_choice == 'V': # V
            if len(calendar.keys()) < 1:
                print("The calendar is empty")
            else:
                print(calendar)
            
        elif user_choice == 'U': # U
            if len(calendar.keys()) < 1:
                print("The calendar is empty")
            else:
                print(calendar)
                date = raw_input("What date? ")
                update = raw_input("Enter the update: ")
                # could be more control here...
                calendar[date] = update # without checking if the date is valid or if it already exists (which could override things)!
                print("Successful!")
                print(calendar)
          
        elif user_choice == 'A': # A
            event = raw_input("Enter event: ")
            date = raw_input("Enter date (MM/DD/YYYY): ")
            if (len(date) > 10 or int(date[6:]) < int(strftime("%Y"))): # could be more control...
                print("Invalid date format.")
                try_again = raw_input("Try Again? 'Y' for Yes, 'N' for No: ").upper()
                if try_again == 'Y':
                    continue #! break, continue, start is still True
                else:
                    start == False
            else:
                calendar[date] = event # without checking if the date is valid or if it already exists (which could override things)!
                print("Successful!")
                print(calendar)
         
        elif user_choice == 'D': # D
            if len(calendar.keys()) < 1:
                print("The calendar is empty.")
            else:
                print(calendar)
                event = raw_input("What event? ") # could be more option like: What date?
                for date in calendar.keys():
                    if event == calendar[date]:
                        del calendar[date] # del a[], [1], ["a"], [1:3], [5:], [:9], etc.
                        print("Deleted.")
                        print(calendar)
                    else:
                        print("Incorrect.")
            
        elif user_choice == 'X': # X
            start = False
        
        else:
            print("Invalid command.")
            break

start_calendar()
```

    What is your first name? Al
    Welcome Al.
    Calendar starting...
    Today is: Thursday, October 20, 2016
    It is currently: 13:42:02
    What would you like to do?
    {}
    Choose between: 'A' to Add, 'U' to Update, 'V' to View, 'D' to Delete or 'X' to Exit? a
    Enter event: Buy stuff
    Enter date (MM/DD/YYYY): 10/21/2016
    Successful!
    {'10/21/2016': 'Buy stuff'}
    Choose between: 'A' to Add, 'U' to Update, 'V' to View, 'D' to Delete or 'X' to Exit? A
    Enter event: Sell stuff
    Enter date (MM/DD/YYYY): 11/01/2016
    Successful!
    {'10/21/2016': 'Buy stuff', '11/01/2016': 'Sell stuff'}
    Choose between: 'A' to Add, 'U' to Update, 'V' to View, 'D' to Delete or 'X' to Exit? A
    Enter event: Rent stuff
    Enter date (MM/DD/YYYY): 01/01/2018
    Successful!
    {'10/21/2016': 'Buy stuff', '01/01/2018': 'Rent stuff', '11/01/2016': 'Sell stuff'}
    Choose between: 'A' to Add, 'U' to Update, 'V' to View, 'D' to Delete or 'X' to Exit? v
    {'10/21/2016': 'Buy stuff', '01/01/2018': 'Rent stuff', '11/01/2016': 'Sell stuff'}
    Choose between: 'A' to Add, 'U' to Update, 'V' to View, 'D' to Delete or 'X' to Exit? u
    {'10/21/2016': 'Buy stuff', '01/01/2018': 'Rent stuff', '11/01/2016': 'Sell stuff'}
    What date? 01/01/2018
    Enter the update: Lease stuff
    Successful!
    {'10/21/2016': 'Buy stuff', '01/01/2018': 'Lease stuff', '11/01/2016': 'Sell stuff'}
    Choose between: 'A' to Add, 'U' to Update, 'V' to View, 'D' to Delete or 'X' to Exit? v
    {'10/21/2016': 'Buy stuff', '01/01/2018': 'Lease stuff', '11/01/2016': 'Sell stuff'}
    Choose between: 'A' to Add, 'U' to Update, 'V' to View, 'D' to Delete or 'X' to Exit? d
    {'10/21/2016': 'Buy stuff', '01/01/2018': 'Lease stuff', '11/01/2016': 'Sell stuff'}
    What event? Buy stuff
    Deleted.
    {'01/01/2018': 'Lease stuff', '11/01/2016': 'Sell stuff'}
    Incorrect.
    Incorrect.
    Choose between: 'A' to Add, 'U' to Update, 'V' to View, 'D' to Delete or 'X' to Exit? d
    {'01/01/2018': 'Lease stuff', '11/01/2016': 'Sell stuff'}
    What event? 10/21/2016
    Incorrect.
    Incorrect.
    Choose between: 'A' to Add, 'U' to Update, 'V' to View, 'D' to Delete or 'X' to Exit? x
    

# UNIT 9, Exam Statistics

## Exam Statistics


```python
grades = [100, 100, 90, 40, 80, 100, 85, 70, 90, 65, 90, 85, 50.5]

print "Grades:", grades

def print_grades(grades): # list the grades
    
    for i in grades:
        print i, # , keep the list on the same line

print_grades(grades)

print "Let's compute some stats!"

def grades_sum(scores): # sum up the grades
    
    total = 0
    for s in scores:
        total += s
    return total
    
print grades_sum(grades)

def grades_average(grades): # average the grades
    
    sum_of_grades = grades_sum(grades)
    average = sum_of_grades / float(len(grades))
    return average

print grades_average(grades)

print "Time to conquer the variance!"

def grades_variance(scores): # compute the variance
    
    average = grades_average(scores)
    totalvariance = 0
    for score in scores:
        totalvariance += (score - average) ** 2
    tvariance = totalvariance/float(len(scores))
    return tvariance

variance = grades_variance(grades)
print variance

def grades_std_deviation(variance): # compute standard deviation
    
    stddevisation = variance ** 0.5
    return stddevisation

print grades_std_deviation(variance)
```

    Grades: [100, 100, 90, 40, 80, 100, 85, 70, 90, 65, 90, 85, 50.5]
    100 100 90 40 80 100 85 70 90 65 90 85 50.5 Let's compute some stats!
    1045.5
    80.4230769231
    Time to conquer the variance!
    334.071005917
    18.2776094147
    

# UNIT 10, Advanced Topics in Python

## Advanced Topics in Python

Iterate through a dictionary.


```python
my_dict = {
    "CodeCademy" : "Python",
    "DataCamp" : "R",
    "Code School" : "SQL"
}

print my_dict.items()
print my_dict.keys()
print my_dict.values()

for key in my_dict:
    print key, my_dict[key] # key and value
```

    [('CodeCademy', 'Python'), ('Code School', 'SQL'), ('DataCamp', 'R')]
    ['CodeCademy', 'Code School', 'DataCamp']
    ['Python', 'SQL', 'R']
    CodeCademy Python
    Code School SQL
    DataCamp R
    

Build a list.


```python
evens_to_50 = [i for i in range(51) if i % 2 == 0]

print evens_to_50
```

    [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24, 26, 28, 30, 32, 34, 36, 38, 40, 42, 44, 46, 48, 50]
    

Build lists with conditions.


```python
doubles_by_3 = [x * 2 for x in range(1,6) if (x * 2) % 3 == 0]

print doubles_by_3
```

    [6]
    


```python
even_squares = [x ** 2 for x in range(2,11) if (x ** 2) % 2 == 0]

print even_squares
```

    [4, 16, 36, 64, 100]
    


```python
cubes_by_four = [x ** 3 for x in range(1,11) if x ** 3 % 4 == 0]

print cubes_by_four
```

    [8, 64, 216, 512, 1000]
    

Lists slicing.

<sub>extract, list</sub>


```python
l = [i ** 2 for i in range(1, 11)] # Should be [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]

print l[2:9:2] # [start:end:stride]
```

    [9, 25, 49, 81]
    


```python
my_list = range(1, 11) # list of numbers 1 - 10

print my_list[::2]
```

    [1, 3, 5, 7, 9]
    


```python
my_list = range(1, 11)

backwards = my_list[::-1]

print backwards
```

    [10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
    


```python
to_one_hundred = range(101)

backwards_by_tens = to_one_hundred[::-10]

print backwards_by_tens
```

    [100, 90, 80, 70, 60, 50, 40, 30, 20, 10, 0]
    


```python
to_21 = range(1, 22)

print to_21

odds = range(1, 22, 2)

print odds

middle_third = to_21[7:14:1]

print middle_third
```

    [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21]
    [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21]
    [8, 9, 10, 11, 12, 13, 14]
    

Lambda function.


```python
my_list = range(16)

print filter(lambda x: x % 3 == 0, my_list)
```

    [0, 3, 6, 9, 12, 15]
    


```python
languages = ["HTML", "JavaScript", "Python", "Ruby"]

print filter(lambda x: x == "Python",languages)
```

    ['Python']
    


```python
squares = [x**2 for x in range(1,11)]

print filter(lambda x: (x >= 30 and x <= 70), squares)
```

    [36, 49, 64]
    

Iterating over dictionaries.


```python
movies = {
    "Monty Python and the Holy Grail": "Great",
    "Monty Python's Life of Brian": "Good",
    "Monty Python's Meaning of Life": "Okay"
}

print movies.items()
```

    [("Monty Python's Life of Brian", 'Good'), ("Monty Python's Meaning of Life", 'Okay'), ('Monty Python and the Holy Grail', 'Great')]
    

Comprehensions.


```python
threes_and_fives = [x for x in range(1,16) if (x % 3 == 0 or x % 5 == 0)]

print threes_and_fives
```

    [3, 5, 6, 9, 10, 12, 15]
    

Slicing again.

<sub>extract</sub>


```python
garbled = "!XeXgXaXsXsXeXmX XtXeXrXcXeXsX XeXhXtX XmXaX XI"

message = garbled[::-2]

print message
```

    I am the secret message!
    


```python
garbled = "IXXX aXXmX aXXXnXoXXXXXtXhXeXXXXrX sXXXXeXcXXXrXeXt mXXeXsXXXsXaXXXXXXgXeX!XX"

message = filter(lambda x: x != "X", garbled)

print message
```

    I am another secret message!
    

## Introduction to Bitwise Operators

Operators.


```python
print 5 >> 4  # Right Shift
print 5 << 1  # Left Shift
print 8 & 5   # Bitwise AND
print 9 | 4   # Bitwise OR
print 12 ^ 42 # Bitwise XOR
print </sub>88     # Bitwise NOT
```

    0
    10
    0
    13
    38
    -89
    

Base 2 or binary.


```python
print 0b1,    # 1
print 0b10,   # 2
print 0b11,   # 3
print 0b100,  # 4
print 0b101,  # 5
print 0b110,  # 6
print 0b111   # 7
print "******"
print 0b1 + 0b11 # 1 + 3 = 4
print 0b11 * 0b11 # 3 * 3 = 90
```

    1 2 3 4 5 6 7
    ******
    4
    9
    


```python
one = 0b1
two = 0b10
three = 0b11
four = 0b100
five = 0b101
six = 0b110
seven = 0b111
eight = 0b1000
nine = 0b1001
ten = 0b1010
eleven = 0b1011
twelve = 0b1100
```

Decimal to binary.


```python
print bin(1)
print bin(2)
print bin(3)
print bin(4)
print bin(5)
```

    0b1
    0b10
    0b11
    0b100
    0b101
    

Binary to decimal.


```python
print int("1",2)
print int("10",2)
print int("111",2)
print int("0b100",2)
print int(bin(5),2)
```

    1
    2
    7
    4
    5
    

Print out the decimal equivalent of the binary 11001001.


```python
print int("11001001",2)
```

    201
    

Left Bit Shift (`<<`)

```
0b000001 << 2 == 0b000100 (1 << 2 = 4)
0b000101 << 3 == 0b101000 (5 << 3 = 40)       
```

Right Bit Shift (`>>`)

```
0b0010100 >> 3 == 0b000010 (20 >> 3 = 2)
0b0000010 >> 2 == 0b000000 (2 >> 2 = 0)
```

This operation is mathematically equivalent to floor dividing and multiplying by 2 (respectively) for every time you shift, but it's often easier just to think of it as shifting all the 1s and 0s left or right by the specified number of slots.


```python
shift_right = 0b1100
shift_left = 0b1

shift_right = 0b1100 >> 2
shift_left = 0b1 << 2
print bin(shift_right)
print bin(shift_left)
```

    0b11
    0b100
    

The bitwise AND (`&`) operator compares two numbers on a bit level and returns a number where the bits of that number are turned on if the corresponding bits of both numbers are 1. For example:

```
    a:   00101010   42
	b:   00001111   15       
===================
a & b:   00001010   10
```

As you can see, the 2's bit and the 8's bit are the only bits that are on in both `a` and `b`, so `a & b` only contains those bits. Note that using the & operator can only result in a number that is less than or equal to the smaller of the two values.

- 0 & 0 = 0
- 0 & 1 = 0
- 1 & 0 = 0
- 1 & 1 = 1

For example: `0b111 (7) & 0b1010 (10) = 0b10`.


```python
print bin(0b1110&0b101)

print bin(0b100)
```

    0b100
    0b100
    

The bitwise OR (`|`) operator compares two numbers on a bit level and returns a number where the bits of that number are turned on if either of the corresponding bits of either number are 1. For example:

```
    a:  00101010  42
    b:  00001111  15       
================
a | b:  00101111  47
```

Note that the bitwise `|` operator can only create results that are greater than or equal to the larger of the two integer inputs.

- 0 | 0 = 0
- 0 | 1 = 1 
- 1 | 0 = 1
- 1 | 1 = 1

For example: `110 (6) | 1010 (10) = 1110 (14)`.


```python
print bin(0b1110|0b101)
```

    0b1111
    

The XOR (`^`) or exclusive or operator compares two numbers on a bit level and returns a number where the bits of that number are turned on if either of the corresponding bits of the two numbers are 1, but not both.

```
    a:  00101010   42
    b:  00001111   15       
================
a ^ b:  00100101   37
```

Keep in mind that if a bit is off in both numbers, it stays off in the result. Note that `XOR`-ing a number with itself will always result in 0.

- 0 ^ 0 = 0
- 0 ^ 1 = 1
- 1 ^ 0 = 1
- 1 ^ 1 = 0

For example: `111 (7) ^ 1010 (10) = 1101 (13)`.


```python
print bin(0b1110^0b101)
```

    0b1011
    

The bitwise NOT operator (`</sub>`) just flips all of the bits in a single number. What this actually means to the computer is actually very complicated, so we're not going to get into it. Just know that mathematically, this is equivalent to adding one to the number and then making it negative. 


```python
print </sub>1
print </sub>2
print </sub>3
print </sub>42
print </sub>123
```

    -2
    -3
    -4
    -43
    -124
    

A bit mask is just a variable that aids you with bitwise operations. A bit mask can help you turn specific bits on, turn others off, or just collect data from an integer about which bits are on or off.


```python
def check_bit4(input):
    
    mask = 0b1000
    desired = input & mask
    if desired > 0:
        return "on"
    else:
        return "off"
        
print check_bit4(0b1100)
```

    on
    

```
0b1000
0b1100
======
0b1000
```

You can also use masks to turn a bit in a number on using `|`. Use a bitmask and the value a in order to achieve a result where the third bit from the right of a is turned on. Be sure to print your answer as a `bin()` string!


```python
a = 0b10111011
mask = 0b100
desired = a | mask
print bin(desired)
```

    0b10111111
    

```
0b10111011
0b00000100
==========
0b10111111
```

Using the XOR (`^`) operator is very useful for flipping bits. Using `^` on a bit with the number one will return a result where that bit is flipped. In the editor is the 8 bit variable a. Use a bitmask and the value a in order to achieve a result where all of the bits in a are flipped. Be sure to print your answer as a `bin()` string!


```python
a = 0b11101110
mask = 0b11111111
desired = a ^ mask
print bin(desired)
```

    0b10001
    

```
0b11101110
0b11111111
==========
0b00010001
```

Finally, you can also use the left shift (`<<`) and right shift (`>>`) operators to slide masks into place.


```python
def flip_bit(number, n):
    
    mask = (0b1 << (n-1))
    result = number ^ mask
    return bin(result)

print flip_bit(0b111, 2)
```

    0b101
    

## Project RGB-HEX Converter

In this project, we'll use Bitwise operators to build a calculator that can convert RGB values to Hexadecimal (`hex`) values, and vice-versa.


```python
def rgb_hex():
    
    invalid_msg = "Invalid entry"
    red = int(raw_input("Enter a 'red' (R) value, from 0 to 255: "))
    if red < 0 or red > 255:
        print invalid_msg
        return # return will exit the function, w/o return, the function jumps to the next line...

    green = int(raw_input("Enter a 'green' (G) value, from 0 to 255: "))
    if green < 0 or green > 255:
        print invalid_msg
        return

    blue = int(raw_input("Enter a 'blue' (B) value, from 0 to 255: "))
    if blue < 0 or blue > 255:
        print invalid_msg
        return

    val = red << 16 + green << 8 + blue
    # A hexadecimal number can be represented with 3 bytes, a byte for each part of R, G, and B. A byte is composed of two nibbles (4 bit numbers). Hexadecimal numbers have 6 characters and each nibble represents a hex character.
    # Shifting red to the left by 16 bits will insert 16 bits that will hold the place of green (shifted 8 bits to the left) and blue (no shift).
    # Become familiar with bits by reading more here.
    print "%s" %(hex(val)[2:].upper()) # string formatting

def hex_rgb():
    
    invalid_msg = "Invalid entry"
    hex_val = raw_input("Enter a color (six hexadecimal digits): ")
    if len(hex_val) != 6:
        print "Invalid Entry"
    else:
        hex_val = int(hex_val, 16)
    two_hex_digits = 2 ** 8
    blue = hex_val % two_hex_digits
    hex_val = hex_val >> 8
    green = hex_val % two_hex_digits
    hex_val = hex_val >> 8
    red = hex_val % two_hex_digits
    print "Red: %s Green: %s Blue: %s" %(red, green,blue)

def convert():
    
    while True:
        option = str(raw_input("Enter '1' to convert RGB to HEX. Enter '2' to convert HEX to RGB. Enter 'X' to Exit:. "))
        if option == '1':
            print "RGB to Hex..."
            rgb_hex()
        elif option == '2':
            print "Hex to RGB..."
            hex_rgb()
        elif option == 'X' or option == 'x':
            break
        else:
            print "Error"

convert()
```

    Enter '1' to convert RGB to HEX. Enter '2' to convert HEX to RGB. Enter 'X' to Exit:. 1
    RGB to Hex...
    Enter a 'red' (R) value, from 0 to 255: 10
    Enter a 'green' (G) value, from 0 to 255: 10
    Enter a 'blue' (B) value, from 0 to 255: 20
    280000000000000L
    Enter '1' to convert RGB to HEX. Enter '2' to convert HEX to RGB. Enter 'X' to Exit:. x
    

# UNIT 11, Introduction to Classes

## Introduction to Classes

You can think of an object as a single data structure that contains data as well as functions; functions of objects are called methods. `Class Fruit`, `lemon instance`.


```python
class Fruit(object):
    
    
    def __init__(self, name, color, flavor, poisonous):
        
        self.name = name
        self.color = color
        self.flavor = flavor
        self.poisonous = poisonous

    def description(self):
        
        print "I'm a %s %s and I taste %s." % (self.color, self.name, self.flavor)

    def is_edible(self):
        
        if not self.poisonous:
            print "Yep! I'm edible."
        else:
            print "Don't eat me! I am super poisonous."

            
lemon = Fruit("lemon", "yellow", "sour", False)

lemon.description()

lemon.is_edible()
```

    I'm a yellow lemon and I taste sour.
    Yep! I'm edible.
    

The class keyword, the name of the class, and the class from which the new class inherits in parentheses. By convention, user-defined Python class names start with a capital letter.


```python
class Animal(object):
    
    
    pass
```

`__init__():` this function is required for classes, and it's used to initialize the objects it creates. `__init__()` always takes at least one argument, self, that refers to the object being created. You can think of `__init__()` as the function that "boots up" each object the class creates. Python will use the first parameter that `__init__()` receives to refer to the object being created; this is why it's often called self, since this parameter gives the object being created its identity.


```python
class Animal(object):
    
    
    def __init__(self, name):
        
        self.name = name
```

Start creating objects. We can access attributes of our objects using dot notation.


```python
class Animal(object):
    
    
    def __init__(self, name):
        
        self.name = name


zebra = Animal("Jeffrey") # instance of Animal

print zebra.name # instance with attributes
```

    Jeffrey
    

More...


```python
Class Animal(object):
    
    
    def __init__(self, name, age, is_hungry):
        
        self.name = name
        self.age = age
        self.is_hungry = is_hungry


zebra = Animal("Jeffrey", 2, True)
giraffe = Animal("Bruce", 1, False)
panda = Animal("Chad", 7, True)

print zebra.name, zebra.age, zebra.is_hungry
print giraffe.name, giraffe.age, giraffe.is_hungry
print panda.name, panda.age, panda.is_hungry
```


      File "<ipython-input-55-08cd00c1ed56>", line 1
        Class Animal(object):
                   ^
    SyntaxError: invalid syntax
    


Another important aspect of Python classes is scope. The scope of a variable is the context in which it's visible to the program.

It may surprise you to learn that not all variables are accessible to all parts of a Python program at all times. When dealing with classes, you can have variables that are available everywhere (global variables), variables that are only available to members of a certain class (member variables), and variables that are only available to particular instances of a class (instance variables).

Global variable, (class) member variable, class variable, instance variable

The same goes for functions: some are available everywhere, some are only available to members of a certain class, and still others are only available to particular instance objects.

Global function, class function, instance function

They all have access to the member variable is_alive, since they're all members of the Animal class.


```python
class Animal(object):
    
    
    """Makes cute animals."""
    
    is_alive = True
    
    def __init__(self, name, age):
        
        self.name = name
        self.age = age


zebra = Animal("Jeffrey", 2)
giraffe = Animal("Bruce", 1)
panda = Animal("Chad", 7)

print zebra.name, zebra.age, zebra.is_alive
print giraffe.name, giraffe.age, giraffe.is_alive
print panda.name, panda.age, panda.is_alive
```

    Jeffrey 2 True
    Bruce 1 True
    Chad 7 True
    

When a class has its own functions, those functions are called methods.


```python
class Animal(object):
    
    
    """Makes cute animals."""
    
    is_alive = True

    def __init__(self, name, age):
        
        self.name = name
        self.age = age

    def description(self):
        
        print self.name
        print self.age


hippo = Animal("Yan", 10)

hippo.description() # will call the class function and print
```

    Yan
    10
    

A class can have any number of member variables.


```python
class Animal(object):
    
    
    """Makes cute animals."""
    
    is_alive = True
    health = "good"

    def __init__(self, name, age):
        
        self.name = name
        self.age = age

    def description(self):
        
        print self.name
        print self.age

        
hippo = Animal("Yan", 10)
sloth = Animal("George", 1)
ocelot = Animal("Holly", 2)

print hippo.health # will call the class variable
print sloth.health
print ocelot.health
```

    good
    good
    good
    

Kind of classes and objects you might find in commercial software: here we have a basic `ShoppingCart` class for creating shopping cart objects for website customers; though basic, it's similar to what you'd see in a real program.


```python
class ShoppingCart(object):
    
    
    items_in_cart = {} # try it with an empty or not dictionary
    items_in_cart = {"cereal":1}

    def __init__(self, customer_name):
        
        self.customer_name = customer_name

    def add_item(self, product, price):
        
        """Add product to the cart."""
        
        if not product in self.items_in_cart: # check the dictionary
            self.items_in_cart[product] = price
            print product + " added."
        else:
            print product + " is already in the cart."

    def remove_item(self, product):
        
        """Remove product from the cart."""
        
        if product in self.items_in_cart: # check the dictionary
            del self.items_in_cart[product]
            print product + " removed."
        else:
            print product + " is not in the cart."


my_cart = ShoppingCart("Jean") # instance
my_cart.add_item("cereal",1) # class function
```

    cereal is already in the cart.
    

Inheritance is a tricky concept, so let's go through it step by step. Inheritance is the process by which one class takes on the attributes and methods of another, and it's used to express an is-a relationship. For example, a Panda is a bear, so a Panda class could inherit from a Bear class.


```python
class Customer(object):
    
    
    """Produces objects that represent customers."""
    
    def __init__(self, customer_id):
        
        self.customer_id = customer_id

    def display_cart(self):
        
        print "I'm a string that stands in for the contents of your shopping cart!"


class ReturningCustomer(Customer):
    
    
    """For customers of the repeat variety."""
    
    def display_order_history(self):
        
        print "I'm a string that stands in for your order history!"


monty_python = ReturningCustomer("ID: 12345") # class instance
monty_python.display_cart() # inherited from the 1st class
monty_python.display_order_history() # from the current class
```

    I'm a string that stands in for the contents of your shopping cart!
    I'm a string that stands in for your order history!
    

COMPLETE EXAMPLE.


```python
class Shape(object):

    
    """make shapes"""
    
    number_of_sides = 5
    
    def __init__(self, number_of_sides):
        
        self.number_of_sides = number_of_sides

        
my_shape = Shape(4) # instance


class Triangle(Shape):
    

    number_of_3sides = 3
    # number_of_sides = 3 # would override the above

    
    def __init__(self, angle1, angle2, angle3):
        
        self.angle1 = angle1
        self.angle2 = angle2
        self.angle3 = angle3

    def check_angles(self):
        
        if self.angle1 + self.angle2 + self.angle3 == 180:
            return True
        else:
            return False


my_triangle = Triangle(90, 30, 60) # instance

print my_triangle.number_of_sides # inherit
print my_shape.number_of_sides

print my_triangle.number_of_3sides
print my_triangle.check_angles()


class Equilateral(Triangle):
    
    
    angle = 60
    
    def __init__(self):
        
        self.angle1 = self.angle # override the above
        self.angle2 = self.angle
        self.angle3 = self.angle


my_equilateral = Equilateral() # instance

print my_equilateral.angle
print my_equilateral.angle1 # based on variable angle

print my_equilateral.number_of_sides # inherit
print my_equilateral.number_of_3sides # inherit

print my_equilateral.check_angles() # inherit; method way
print Equilateral.check_angles(my_equilateral) # function way; IDEM !!!
```

    5
    4
    3
    True
    60
    60
    5
    3
    True
    True
    

Sometimes you'll want one class that inherits from another to not only take on the methods and attributes of its parent, but to override one or more of them.


```python
class Employee(object):
    
    
    """Models real-life employees!"""
    
    def __init__(self, employee_name):
        
        self.employee_name = employee_name

    def calculate_wage(self, hours):
        
        self.hours = hours
        return hours * 20.00


class PartTimeEmployee(Employee):

    
    def calculate_wage(self, hours):
        
        self.hours = hours
        return hours * 12.00 # override what is naturally inherited
```


```python
class Employee(object):
    
    
    def __init__(self, name):
        
        self.name = name
        
    def greet(self, other):
        
        print "Hello, %s" % other.name


class CEO(Employee):
    
    def greet(self, other):
        
        print "Get back to work, %s!" % other.name # override


ceo = CEO("Emily")
emp = Employee("Steve")

emp.greet(ceo)
ceo.greet(emp)
```

    Hello, Emily
    Get back to work, Steve!
    

On the flip side, sometimes you'll be working with a derived class (or subclass) and realize that you've overwritten a method or attribute defined in that class' base class (also called a parent or superclass) that you actually need. Have no fear! You can directly access the attributes or methods of a superclass with Python's built-in super call.


```python
class Employee(object):
    
    
    """Models real-life employees!"""
    
    def __init__(self, employee_name):
        
        self.employee_name = employee_name

    def calculate_wage(self, hours):
        
        self.hours = hours
        return hours * 20.00


class PartTimeEmployee(Employee):

    
    def calculate_wage(self, hours): # override
        
        self.hours = hours
        return hours * 12.00
    
    def full_time_wage(self, hours): # super call: associate the parent's class function with child's new function withtout retyping the function
        
        return super(PartTimeEmployee, self).calculate_wage(hours)


milton = PartTimeEmployee("Jack")

print milton.full_time_wage(10)
```

    200.0
    

## More on Classes


```python
class Car(object): # create a class
    
    
    pass


my_car = Car() # create a class instance
```


```python
class Car(object):

    
    condition = "new" # create a member variables


my_car = Car()

print my_car.condition # call the member variable
```

    new
    


```python
class Car(object):

    
    condition = "new"
    
    def __init__(self, model, color, mpg): # initialize or boot up!
        
        self.model = model # assign class variables
        self.color = color
        self.mpg = mpg

        
my_car = Car("DeLorean", "silver", 88) # create an instance with its class variables

print my_car.condition

print my_car.model # call the class variables...
print my_car.color
print my_car.mpg
```

    new
    DeLorean
    silver
    88
    


```python
class Car(object):

    
    condition = "new"
    
    def __init__(self, model, color, mpg):
        
        self.model = model
        self.color = color
        self.mpg = mpg

    def display_car(self):
        
        return "This is a %s %s with %s MPG." % (self.color, self.model, str(self.mpg)) # create a class method (function)


my_car = Car("DeLorean", "silver", 88)

print my_car.condition

print my_car.model
print my_car.color
print my_car.mpg

print my_car.display_car() # call the class method
```

    new
    DeLorean
    silver
    88
    This is a silver DeLorean with 88 MPG.
    


```python
class Car(object):

    
    condition = "new"
    
    def __init__(self, model, color, mpg):
        
        self.model = model
        self.color = color
        self.mpg = mpg

    def display_car(self):
        
        return "This is a %s %s with %s MPG." % (self.color, self.model, str(self.mpg))

    def drive_car(self):
        
        self.condition = "used"


my_car = Car("DeLorean", "silver", 88)

print my_car.condition # 'new'

print my_car.model
print my_car.color
print my_car.mpg

print my_car.display_car()

my_car.drive_car()
print my_car.condition # the condition changes to 'used'
```

    new
    DeLorean
    silver
    88
    This is a silver DeLorean with 88 MPG.
    used
    


```python
class Car(object):

    
    condition = "new"
    
    def __init__(self, model, color, mpg):
        
        self.model = model
        self.color = color
        self.mpg = mpg

    def display_car(self):
        
        return "This is a %s %s with %s MPG." % (self.color, self.model, str(self.mpg))

    def drive_car(self):
        
        self.condition = "used"

        
my_car = Car("DeLorean", "silver", 88)

print my_car.condition

print my_car.model
print my_car.color
print my_car.mpg

print my_car.display_car()

my_car.drive_car()
print my_car.condition


class ElectricCar(Car):
    

    def __init__(self, model, color, mpg, battery_type): # initialize with some partial inheritance from class Car

        Car.__init__(self, model, color, mpg) # assign class variable by inheritance from class Car
        self.battery_type = battery_type # assign a new class variable


my_car = ElectricCar("Telsa", "red", 0, "molten salt") # create an instance with its class variables; OVERRIDE the above

print my_car.condition # call the class variables; OVERRIDE the above

print my_car.model # call the member variable; OVERRIDE the above
print my_car.color
print my_car.mpg

my_ride = ElectricCar("Google", "blue", 10, "electrical") # create an instance with its class variables

print my_ride.condition # call the class variables

print my_ride.model # call the member variable
print my_ride.color
print my_ride.mpg
```

    new
    DeLorean
    silver
    88
    This is a silver DeLorean with 88 MPG.
    used
    new
    Telsa
    red
    0
    new
    Google
    blue
    10
    


```python
class Car(object):

    
    condition = "new"
    
    def __init__(self, model, color, mpg):
        
        self.model = model
        self.color = color
        self.mpg = mpg

    def display_car(self):
        
        return "This is a %s %s with %s MPG." % (self.color, self.model, str(self.mpg))

    def drive_car(self):
        
        self.condition = "used"


my_car = Car("DeLorean", "silver", 88)

print my_car.condition + "!" # call the member variable; 'new'

print my_car.model
print my_car.color
print my_car.mpg

print my_car.display_car()

my_car.drive_car() # call the class method
print my_car.condition + "!!" # member variable; now 'used'

class ElectricCar(Car):


    def __init__(self, model, color, mpg, battery_type):
        
        Car.__init__(self, model, color, mpg)
        self.battery_type = battery_type

    def drive_car(self): # create a class method; OVERRIDE the above
        
        self.condition = "like new"


my_car = ElectricCar("Telsa", "red", 0, "molten salt")

print my_car.condition + "!" # 'new' again
my_car.drive_car() # call the class method
print my_car.condition + "!!" # 'like new' now

print my_car.model
print my_car.color
print my_car.mpg

my_ride = ElectricCar("Google", "blue", 10, "electrical")

print my_ride.condition + "!" # 'used' again
my_ride.drive_car()# call the class method
print my_ride.condition + "!!" # 'like new' now

print my_ride.model
print my_ride.color
print my_ride.mpg
```

    new!
    DeLorean
    silver
    88
    This is a silver DeLorean with 88 MPG.
    used!!
    new!
    like new!!
    Telsa
    red
    0
    new!
    like new!!
    Google
    blue
    10
    


```python
class Point3D(object):
    
    
    def __init__(self, x, y, z): # initialize
        
        self.x = x
        self.y = y
        self.z = z

# __repr__() method, which is short for representation; by providing a return value in this method, we can tell Python how to represent an object of our class (for instance, when using a print statement).

    def __repr__(self):
        
        return "(%d, %d, %d)" % (self.x, self.y, self.z)


my_point = Point3D(1,2,3) # instance

# Print my_point.__repr__() w/o adding variables

print my_point
```

    (1, 2, 3)
    

## Quiz 11

Python writes data to a file when you close the file!

## Project Bank Account

In this project, we'll create a Python class that can be used to create and manipulate a personal bank account.


```python
class BankAccount(object):

    
    balance = 0
  
    def __init__(self, name):
        self.name = name
  
    def __repr__(self):
        
    # The __repr__() method defines what represents the object when a user tries to print the BnkAccount object using print. Let's add to this method and make it descriptive.
        
        return "%s's account; Balance: $%.2f" % (self.name, self.balance) # $%.2f for 2 decimals, self.class attribute, self.member variable
  
    def show_balance(self):
        
        print "Balance: $%.2f\n" % (self.balance)
    
    def deposit(self, amount):
        
        if amount <= 0:
            print "No Account. Invalid\n"
            return # # return will exit the function, w/o return, the function jumps to the next line...
        else:
            print "Depositing: $%.2f" % (amount) # ?
            self.balance += amount
            self.show_balance() # calling a class function
  
    def withdraw(self, amount):
        
        if amount > self.balance:
            print "More than the balance. Invalid\n"
            return
        else:
            print "Withdrawing: $%.2f" % (amount) # ?
            self.balance -= amount
            self.show_balance()


my_account = BankAccount("Ugo") # Ugo is the argument 'name'

print my_account # launch the __repr__
my_account.show_balance() # launch the class function (method) show_balance

my_account.deposit(2000)
my_account.withdraw(3000)
my_account.withdraw(1000)

print my_account
```

    Ugo's account; Balance: $0.00
    Balance: $0.00
    
    Depositing: $2000.00
    Balance: $2000.00
    
    More than the balance. Invalid
    
    Withdrawing: $1000.00
    Balance: $1000.00
    
    Ugo's account; Balance: $1000.00
    

# UNIT 12, File Input and Output

## File Input/Output

Read information from a file on your computer, and/or write that information to another file? This process is called file I/O.


```python
my_list = [i ** 2 for i in range(1,11)]

f = open("output.txt", "w") # create a file

for item in my_list:
    f.write(str(item) + "\n") # write

f.close() # save, close
```

First.


```python
f = open("output.txt", "w") # This told Python to open output.txt in "w" mode ("w" stands for "write").
```

Read and write.


```python
my_list = [i ** 2 for i in range(1,11)]

my_file = open("output.txt", "r+") # the file must exist

for item in my_list:
    my_file.write(str(item) + "\n") # overwrite

my_file.close() # save, close
```

Read on the console.


```python
my_file = open("output.txt", "r") # the file must exist
print my_file.read()

my_file.close()
```

    1
    4
    9
    16
    25
    36
    49
    64
    81
    100
    
    

Read lines on the console.


```python
my_file = open("output.txt", "r") # the file must exist

print my_file.readline() # read line 1
print my_file.readline() # read line 2 automatically
print my_file.readline() # read line 3

my_file.close()
```

    1
    
    4
    
    9
    
    

Open the file for reading.


```python
read_file = open("output.txt", "r")
print read_file.read()
read_file.close()
```

    1
    4
    9
    16
    25
    36
    49
    64
    81
    100
    
    

Use a second file handler to open the file for writing.


```python
write_file = open("text.txt", "w")

# Write to the file
write_file.write("Not closing files is VERY BAD.")

# Try to read from the file
print write_file.read() # Not working...``

write_file.close()
```


    ---------------------------------------------------------------------------

    IOError                                   Traceback (most recent call last)

    <ipython-input-87-db256164394e> in <module>()
          5 
          6 # Try to read from the file
    ----> 7 print write_file.read() # Not working...``
          8 
          9 write_file.close()
    

    IOError: File not open for reading


Try.


```python
read_file = open("text.txt", "r")
print read_file.read()

write_file = open("text.txt", "w")
write_file.write("Not closing files is VERY BAD.")

write_file.close() # close it!

write_file = open("text.txt", "r") # reopen it in read mode
print write_file.read() # working
write_file.close()
```

    Not closing files is VERY BAD.
    Not closing files is VERY BAD.
    

And.


```python
write_file = open("text.txt", "w")
write_file.write("Not closing files is VERY BAD.") # could be a variable
write_file.close()
```


```python
read_file = open("text.txt", "r")
print read_file.read()
read_file.close()
```

    Not closing files is VERY BAD.
    


```python
write_file = open("text.txt", "w")
write_file.truncate() # delete
write_file.close()
```


```python
read_file = open("text.txt", "r")
print read_file.read()
read_file.close()
```

    
    

You may not know this, but file objects contain a special pair of built-in methods: `__enter__()` and `__exit__()`. The details aren't important, but what is important is that when a file object's `__exit__()` method is invoked, it automatically closes the file. How do we invoke this method? With with and as.


```python
with open("text.txt", "w") as textfile: # a variable
    textfile.write("Success!")
    textfile.close()
```


```python
with open("text.txt", "r") as textfile:
    print textfile.read()
    textfile.close()
```

    Success!
    

# More I/O


```python
with open("text.txt", "w") as my_file:
    my_file.write("Youpee!!!")

print my_file.closed # true

if not my_file.closed == True:
    my_file.close()

print my_file.closed # true

with open("text.txt", "r") as my_file:
    print my_file.read()

print my_file.closed # true

with open("text.txt", "r") as my_file:
    print my_file.closed # false

my_file.close()

print my_file.closed # true
```

    True
    True
    Youpee!!!
    True
    False
    True
    

## Quiz 12

OK

## Project DNA Analysis

In this project, we'll use many of the concepts you've learned throughout the Python course in order to do some DNA analysis for a crime investigation.

The scenario:

A spy deleted important files from a computer. There were a few witnesses at the scene of the crime, but no one is sure who exactly the spy was. Three possible suspects were apprehended based on surveillance video. Each suspect had a sample of DNA taken from them. The computer's keyboard was also swabbed for DNA evidence and, luckily, one small DNA sample was successfully retrieved from the computer's keyboard.

Given the three suspects' DNA and the sample DNA retreived from the keyboard, it's up to you to figure out who the spy is!

The project should have methods for each of the following:

- Given a file, read in the DNA for each suspect and save it as a string
- Take a DNA string and split it into a list of codons
- Iterate through a suspect's codon list to see how many of their codons match the sample codons
- Pick the right suspect to continue the investigation on


```python
sample = ['GTA','GGG','CAC']

def read_dna(dna_file):
    
    dna_data = "" # empty string
    
    with open(dna_file, "r") as f: # f = open(dna_file, "r"); with, as
        for line in f:
            dna_data += line
        return dna_data

def dna_codons(dna):
    
    codons = []
    for i in range(0,len(dna),3): # slice strings of 3 letters
        if i+3 < len(dna): # make sure that you don't add a string to the codon list that isn't at least 3 letters long
            codons.append(dna[i:i+3]) # append to list in appendig positions 0 (new entry), 1, 2, stopping before 3
    return codons

def match_dna(dna):
    
    matches = 0
    for codon in dna:
        if codon in sample: # if ,in
            matches += 1
    return matches

def is_criminal(dna_sample):
    
    dna_data = read_dna(dna_sample)
    codons = dna_codons(dna_data)
    num_matches = match_dna(codons)
    if num_matches >= 3:
        print((dna_sample)[:-4]).upper(),
        print(": number of matches = " + str(num_matches) + "; the investigation will proceed further more with this suspect.")
    else:
        print((dna_sample)[:-4]).upper(),
        print(": no evidence; the suspect can be freed.")

a = "suspect1.txt"
is_criminal(a)

a = "suspect2.txt"
is_criminal(a)

a = "suspect3.txt"
is_criminal(a)
```

    SUSPECT1 : no evidence; the suspect can be freed.
    SUSPECT2 : number of matches = 6; the investigation will proceed further more with this suspect.
    SUSPECT3 : no evidence; the suspect can be freed.
    

suspect1.txt

```text
ATCGAAAGCACAATCATGCATCGTGCCAGTGTGTTCGTGTCATCTAGGACGGGGCCATAGGATATATAATTCAATTAAGAATACCTTATACTACTGTCCCCTGTGGTTCGAAGGGGAACTATTTCGTGGGGCGAGCCCACACCGTCTCTTCTGCGGAAGACTTAACACGTTAGGGAGGTGGAATAGTTTCGAACGATGGTTATTAATCGTGATAACGGAACGCTGTCTGGAGGATGAGTCTGACGGTGTGTGACTCGATCAGTCACTCGCTATTCGAACTGCGCGAAAGATCCCAGCGCT
```

suspect2.txt

```text
CCGTAAGACAAATAATTCAATAAAGATGTCGTTTTGCTAGTTTACGTCAAGGTGTCACGCGCCATCTCTGAGCAGGTGGGCCGACGAGACATTATCCCTGGAGTATCAAACCCGTACAAAGGGAACATCCACACTTTGGTGAATCGAAGCGCGGCATCAGGATTTCCTTTTGGATACCTGAAACAAAGCCCATCGTGGTCCTTAGACTTGGCACACTTACACCTGCAGCGCGCGCATGTGGAATTAGAGGCCAAGTTCGATCCCTACACCGACGTACGATGCAACTGTGTGGATGTGACG
```

suspect3.txt

```text
TCGCATAAGTACAGTAGATCCTCCCCGCGCATCCTATTTATTAAGTTAATTCTACAGCAATACGATCATATGCGGATCCGCAGTGGCCGGTAGACACACCATGCACTTGATTCCGAGGCCTGTCCCGATATATGAACCCAAACTAGAGCGAGGCTGTTGACGTTTGGAGTTGAAAAAATCTATTATACCAATCGGCTTCAACGTGCTCCACGGCAGGCGCCTGACGAGAGGCCCACACCGAGGAAGTAGACTGTTGCACGTTGAGGATAGCGCTAGCTAACAAAGACGCCTGCTACAACA
```
