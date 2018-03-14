<!--
---

[TOC]

-->
---

**Foreword**

Notes and snippets. Python 3.
With Jupyter Notebook and the `In [ ]` `Out [ ]` format.

---

  
# Notes

`list_zoo = ['bear', 'lion', 'panda', 'zebra']`

- Lists in Python store ordered collections of items or objects, we can say that they are sequence types.

## Iterable

- The program can iterate over them.
- Lists, strings, tuples, and sets are called “iterables”.

# Lists Versus tuples

`tup_course = ('physics', 'chemistry', 1997, 2000)`

- You can’t add elements to a tuple. There’s no `append()` or `extend()` method for tuples,
- You can’t remove elements from a tuple. Tuples have no `remove()` or `pop()` method,
- You can find elements in a tuple since this doesn’t change the tuple.
- You can also use the in operator to check if an element exists in the tuple.
- If you’re defining a constant set of values, use a tuple instead of a list. It will be faster and safer.

## Lists Versus sets

`set_code = set{"Perl", "Python", "Java"}`

- Just like dictionaries, sets have no order in their collection of items. Not like lists.
- Set requires the items contained in it to be hashable, lists store non-hashable items.
- Sets require your items to be unique and immutable. Duplicates are not allowed in sets, while lists allow for duplicates and are mutable.
- Use sets when you have an unordered set of UNIQUE, immutable values that are hashable.

### Frozensets

`set_cities = frozenset{"Frankfurt", "Basel","Freiburg"}`

- Frozensets are like sets except that they cannot be changed, i.e. they are immutable.

## Lists Versus dictionaries

`dict_kid = {'Name': 'Zara', 'Age': 7, 'Class': 'First'`

- A list stores an ordered collection of items, so it keeps some order. Dictionaries don’t have any order.
- Dictionaries are known to associate each key with a value, while lists just contain values.
- Use a dictionary when you have an unordered set of unique keys that map to values.

## Hashable or Not

- Hashable: float, integer, tuple, string.
- Not: dictionary, set, list.

# Snippets

## Select an element from a list


```python
# These list elements are all of the same type
zoo = ['bear', 'lion', 'panda', 'zebra']
print(zoo)
```

    ['bear', 'lion', 'panda', 'zebra']



```python
# But these list elements are not
biggerZoo = ['bear', 'lion', 'panda', 'zebra', ['chimpanzees', 'gorillas', 'orangutans', 'gibbons']]
print(biggerZoo)
```

    ['bear', 'lion', 'panda', 'zebra', ['chimpanzees', 'gorillas', 'orangutans', 'gibbons']]



```python
# Select the first list element
oneZooAnimal = biggerZoo[0]

# Print oneZooAnimal
print(oneZooAnimal)
print(biggerZoo[0])
```

    bear
    bear


## Select the last element


```python
# Pass -1 to the index operator on `biggerZoo`
monkeys = biggerZoo[-1]
print(monkeys)

# Pass -2 to the index operator on `biggerZoo`
zebra = biggerZoo[-2]
print(zebra)
```

    ['chimpanzees', 'gorillas', 'orangutans', 'gibbons']
    zebra


## Out of range error


```python
# Run this code to trigger an "Index Out Of Range" Error
print("print(biggerZoo[6])")
```

    print(biggerZoo[6])


## Slice


```python
# Print all
print(biggerZoo)

# Print a[start: ]
someZooAnimals = biggerZoo[2: ]

# Print to see what you exactly select from `biggerZoo`
print(someZooAnimals)

# Print a[ :end]
otherZooAnimals = biggerZoo[ :2]

# Print to see what you're getting back
print(otherZooAnimals)

# Print a[start:end]
print(biggerZoo[2:4])

# Print a[start:end:step]
print(biggerZoo[2::4])
print(biggerZoo[2::2])
print(biggerZoo[2::1])
```

    ['bear', 'lion', 'panda', 'zebra', ['chimpanzees', 'gorillas', 'orangutans', 'gibbons']]
    ['panda', 'zebra', ['chimpanzees', 'gorillas', 'orangutans', 'gibbons']]
    ['bear', 'lion']
    ['panda', 'zebra']
    ['panda']
    ['panda', ['chimpanzees', 'gorillas', 'orangutans', 'gibbons']]
    ['panda', 'zebra', ['chimpanzees', 'gorillas', 'orangutans', 'gibbons']]


## Random


```python
# Import `choice` from the `random` library
from random import choice

# Construct your `list` variable with a list of the first 4 letters of the alphabet
list1 = ['a','b','c','d']

# Print your random 'list' element
print(choice(list1))
print(choice(list1))

# Import `randrange` from the `random` library
from random import randrange

# Construct your `randomLetters` variable with a list of the first 4 letters of the alphabet
randomLetters = ['e','f', 'g', 'h']

# Select a random index from 'randomLetters`
randomIndex = randrange(0,len(randomLetters))

# Print your random element from `random`
print(randomLetters[randomIndex])
```

    c
    c
    g


## Convert a list to a string with `join()`


```python
# List of Strings to a String
listOfStrings = ['One', 'Two', 'Three']
strOfStrings = ''.join(listOfStrings)
print(strOfStrings)

# List Of Integers to a String
listOfNumbers = [1, 2, 3]
strOfNumbers = ''.join(str(n) for n in listOfNumbers)
print(strOfNumbers)
```

    OneTwoThree
    123


## Convert a list to a tuple with `tuple()`


```python
listOfStrings = ['One', 'Two', 'Three']
tupOfStrings = tuple(listOfStrings)
print(tupOfStrings)
```

    ('One', 'Two', 'Three')


## Convert a list to a set with `set()`


```python
listOfStrings = ['One', 'Two', 'Three']
setOfStrings = set(listOfStrings)
print(setOfStrings)
```

    {'One', 'Three', 'Two'}


## Convert a list to a dictionary with `zip()`


```python
helloWorld = ['hello','world','1','2']

# Convert to a dictionary
# 1 will be interpreted as a key and 2 as a value
helloWorldDictionary = dict(zip(helloWorld[0::2], helloWorld[1::2]))

# Print out the result
print(helloWorldDictionary)

a = [1, 2, 3, 4, 5]

# Create a list iterator object
i = iter(a)

# Zip and create a dictionary
print(dict(zip(i, i)))
```

    {'hello': 'world', '1': '2'}
    {1: 2, 3: 4}


## Size of your list with `len()`


```python
print(biggerZoo)

# Pass `justAList` to `len()`
print(len(biggerZoo))
```

    ['bear', 'lion', 'panda', 'zebra', ['chimpanzees', 'gorillas', 'orangutans', 'gibbons']]
    5

## `append()` and `extend()`


```python
# This is your list
list1 = [5, 6, 7, 8, 9]
print(list1)

# Check whether it's iterable
print(list1.__iter__)

shortList = [5, 6, 7, 8, 9]
print(shortList)

# Append [4,5] to `shortList`
shortList.append([4, 5])

# Use the print() method to show shortList
print(shortList)

longerList = [5, 6, 7, 8, 9]
print(longerList)

# Extend `longerList` with [4,5]
longerList.extend([4, 5])

# Use the print() method to see longerList
print(longerList)
```

    [5, 6, 7, 8, 9]
    <method-wrapper '__iter__' of list object at 0x7ff7a7d2dd88>
    [5, 6, 7, 8, 9]
    [5, 6, 7, 8, 9, [4, 5]]
    [5, 6, 7, 8, 9]
    [5, 6, 7, 8, 9, 4, 5]


## Concatenate lists


```python
shortList = [5, 6, 7, 8, 9]
print(shortList)

# Concatenate `shortList` with `[4,5]`
plusList = shortList + [4,5]
```

    [5, 6, 7, 8, 9]


## Sort a list


```python
zoo = ['zebra', 'bear', 'lion', 'panda']
print(zoo)

# Use sort() on the rooms list
zoo.sort() # lists only
print(zoo)

zoo = ['zebra', 'bear', 'lion', 'panda']
print(zoo)

# Now use the sorted() function on orders
print(sorted(zoo)) # lists, strings, sets, dictionaries
```

    ['zebra', 'bear', 'lion', 'panda']
    ['bear', 'lion', 'panda', 'zebra']
    ['zebra', 'bear', 'lion', 'panda']
    ['bear', 'lion', 'panda', 'zebra']


## Copy a List (3 ways):


```python
zoo = ['zebra', 'bear', 'lion', 'panda']
print(zoo)

# Copy the grocery list by slicing and store it in the `newGroceries` variable
newZoo = zoo[:]
print(newZoo)

# Import the copy library as c
import copy as c

# Create a `groceriesForFamily` variable and assign the copied grocery list to it
zooForFamily =  c.copy(zoo)
print(zooForFamily)

# Use `deepcopy()` and assign the copied list to a `groceriesForKids` variable
zooForKids= c.deepcopy(zoo)
print(zooForKids)
```

    ['zebra', 'bear', 'lion', 'panda']
    ['zebra', 'bear', 'lion', 'panda']
    ['zebra', 'bear', 'lion', 'panda']
    ['zebra', 'bear', 'lion', 'panda']


When you use the ‘simple’ copy methods, your original lists will be modified. However, if you use the `deepcopy()` method, it will be prevented.


```python
# This is your list
objectList = ['a','b',['ab','ba']]
print(objectList)

# Copy the `objectList`
copiedList = objectList[:]

# Change the first list element of `copiedList`
copiedList[0] = 'c'

# Go to the third element (the nested list) and change the second element
copiedList[2][1] = 'd'

# Print out the original list to see what happened to it
print(objectList); print(copiedList)
print("Both lists are equal.")
```

    ['a', 'b', ['ab', 'ba']]
    ['a', 'b', ['ab', 'd']]
    ['c', 'b', ['ab', 'd']]
    Both lists are equal.



```python
# 2, this is your list
objectList = ['a','b',['ab','ba']]
print(objectList)

# Copy the `objectList`
import copy as c
copiedList2 = c.deepcopy(objectList)

# Change the first list element of `copiedList`
copiedList2[0] = 'c'

# Go to the third element (the nested list) and change the second element
copiedList2[2][1] = 'd'

# Print out the original list to see what happened to it
print(objectList); print(copiedList2)
print("Both lists are different.")
```

    ['a', 'b', ['ab', 'ba']]
    ['a', 'b', ['ab', 'ba']]
    ['c', 'b', ['ab', 'd']]
    Both lists are different.


## List comprehension


```python
print([x for x in range(10)]) # 10 not included
print([x**2 for x in range(10)])
print([x for x in range(10) if x%2==0])
print([x**2 for x in range(10) if x%2==0])
```

    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
    [0, 2, 4, 6, 8]
    [0, 4, 16, 36, 64]



```python
myList = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(myList)
[(lambda x: x*x)(x) for x in myList]
print([(lambda x: x*x)(x) for x in myList])
# or
print(range(10))
f = lambda x: x*x
[f(x) for x in range(10)]
print([f(x) for x in range(10)])
```

    [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
    [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
    range(0, 10)
    [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]


## Dictionary comprehension also...


## Counting the occurrences of one item in a list


```python
# tallying
print("Count the occurrences of the number 4 in the list.")
print([1, 2, 9, 4, 5, 4, 1])
print([1, 2, 9, 4, 5, 4, 1].count(4))

print("Count the occurrences of the letter 'a' in the list")
list1 = ["d", "a", "t", "a", "c", "a", "m", "p"]
print(list)
list1.count("a")
```

    Count the occurrences of the number 4 in the list.
    [1, 2, 9, 4, 5, 4, 1]
    2
    Count the occurrences of the letter 'a' in the list
    <class 'list'>
    3

## Counting all items in a list with `count()`


```python
list2 = ["a","b","b"]
print(list2)
[[x,list2.count(x)] for x in list(list2)]
print([[x,list2.count(x)] for x in list(list2)])
# now a set; sets only contain unique items
# only the unique list items are kept
```

    ['a', 'b', 'b']
    [['a', 1], ['b', 2], ['b', 2]]


## Counting all items in a list with `Counter()` from the `collections` library


```python
# Import `Counter` from the `collections` library
from collections import Counter

# This is your list
list2 = ["a","b","b"]
print(list2)

# Pass `list` to `Counter()`
Counter(list2)
print(Counter(list2))
```

    ['a', 'b', 'b']
    Counter({'b': 2, 'a': 1})


## Split A Python List Into Evenly Sized Chunks


```python
# Your list `x`
x = [1,2,3,4,5,6,7,8,9]
print(x)

# Split `x` up in chunks of 3
y = zip(*[iter(x)]*3)
```

    [1, 2, 3, 4, 5, 6, 7, 8, 9]


`[1,2,3,4,5,6,7,8,9], [1,2,3,4,5,6,7,8,9], [1,2,3,4,5,6,7,8,9]`

- The first time, `zip()` will take one element of the list sequentially, which leaves you with:

`[1][2][3]`

- The second time, elements will be added to the three lists you just created:

`[1, 4], [2, 5], [3, 6]`

- The third and last time:

`[1, 2, 3], [4, 5, 6], [7, 8, 9]`


```python
# Use `list()` to print the result of `zip()`
print(y.__doc__)
type(y)
```

    zip(iter1 [,iter2 [...]]) --> zip object
    
    Return a zip object whose .__next__() method returns a tuple where
    the i-th element comes from the i-th iterable argument.  The .__next__()
    method continues until the shortest iterable in the argument sequence
    is exhausted and then it raises StopIteration.

    zip

```python
print(list(y))
```

    []

```python
# Method to split up your lists into chunks
def chunks(myList, chunkSize):
    """Yield successive chunkSize-sized chunks from list."""
    for i in range(0, len(myList), chunkSize):
        yield myList[i:i + chunkSize]

# Use your `chunks` function to print out chunks of the same size
import pprint # pretty print

pprint.pprint(range(10, 75))
pprint.pprint(list(chunks(range(10, 75), 10)))
```

    range(10, 75)
    [range(10, 20),
     range(20, 30),
     range(30, 40),
     range(40, 50),
     range(50, 60),
     range(60, 70),
     range(70, 75)]



```python
# Set up your list and chunk size
list1 = range(0, 50)
chunk = 5

# Split up your list into chunks
print([list1[i:i + chunk] for i in range(0, len(list1), chunk)])
```

    [range(0, 5), range(5, 10), range(10, 15), range(15, 20), range(20, 25), range(25, 30), range(30, 35), range(35, 40), range(40, 45), range(45, 50)]


## Loop over a list


```python
# This is your list
myList = [[1,2,3],[4,5,6,7],[8,9,10]]
print(myList)

# Loop over your list and print all elements that are of size 3
for x in myList:
      if len(x)==3:
        print(x) # element
```

    [[1, 2, 3], [4, 5, 6, 7], [8, 9, 10]]
    [1, 2, 3]
    [8, 9, 10]



```python
# Alternatively
print([x for x in myList if len(x)==3])
```

    [[1, 2, 3], [8, 9, 10]]



```python
# This is your list
myList = [3,4,5,6]
print(myList)

# Loop over `myList` and print tuples of all indices and values 
for i, val in enumerate(myList): # return an index and a value
     print(i, val) # indexElement, element
```

    [3, 4, 5, 6]
    0 3
    1 4
    2 5
    3 6


## Create flat lists out of lists


```python
# Your initial list of lists
listOfLists = [[1,2],[3,4],[5,6]]
print(listOfLists)

# Flatten out your original list of lists with `sum()`
print(sum(listOfLists, []))
print(sum.__doc__)

myList = [1,2,3,4,5,6]

print(sum(myList))
```

    [[1, 2], [3, 4], [5, 6]]
    [1, 2, 3, 4, 5, 6]
    Return the sum of a 'start' value (default: 0) plus an iterable of numbers
    
    When the iterable is empty, return the start value.
    This function is intended specifically for use with numeric values and may
    reject non-numeric types.
    21



```python
# Alternatively
from functools import reduce

print(reduce(lambda x,y: x+y,listOfLists)) #  iterable is reduced to a single value
```

    [1, 2, 3, 4, 5, 6]


What happens, is that `[1,2]` is added to `[3,4]` and this result is added to `[5,6]`.

`([1,2]+[3,4])+[5,6])`

Consider item for item in sublist, printing out each item from the sublist.


```python
list1 = []
print(list1)

for sublist in listOfLists:
  for item in sublist:
    list1.append(item)
    
print(list1)
```

    []
    [1, 2, 3, 4, 5, 6]



```python
# Or you can use list comprehension
print([item for sublist in listOfLists for item in sublist])
```

    [1, 2, 3, 4, 5, 6]


## Get an intersection of two Python lists


```python
list1 = [1, 6, 7, 10, 13, 28, 32, 41, 58, 63]
print(list1)

list2 = [[13, 17, 18, 21, 32], [7, 11, 13, 14, 28], [1, 5, 6, 8, 15, 16]]
print(list2)

# Intersect both lists with list comprehension
intersection = [list(filter(lambda x: x in list1, sublist)) for sublist in list2]

# Print the result of the intersection
print(intersection)
```

    [1, 6, 7, 10, 13, 28, 32, 41, 58, 63]
    [[13, 17, 18, 21, 32], [7, 11, 13, 14, 28], [1, 5, 6, 8, 15, 16]]
    [[13, 32], [7, 13, 28], [1, 6]]



```python
# An intersection of both lists, stored in `intersection`
intersection = [[x for x in sublist if x in list1] for sublist in list2]

# Print the result of the intersection
print(intersection)
```

    [[13, 32], [7, 13, 28], [1, 6]]


## Remove duplicates from a list

Check whether a variable is an iterable by applying the method `.__iter__`.


```python
# Your list with duplicate values
duplicates = [1, 2, 3, 1, 2, 5, 6, 7, 8]

# Print the unique `duplicates` list
#print(list(set(duplicates)))

# A list with small numbers 
smallNumbers = [1, 2, 3]

# Print the unique `duplicates` list without the small numbers
# detract the set elements of smallNumbers
list(set(duplicates) - set(smallNumbers))
```




    [8, 5, 6, 7]



## Create Empty Numpy Arrays

Prefer Numpy arrays over lists in Python:

- Because Numpy arrays are more compact than lists.
- Because access in reading and writing items is faster with Numpy.
- Because Numpy can be more convenient to work with, thanks to the fact that you get a lot of vector and matrix operations for free
- Because Numpy can be more efficient to work with because they are implemented more efficiently.


```python
import numpy
print(numpy.array([]))

# Make a Numpy array of four rows and two columns and filled with 0
print(numpy.zeros(shape=(4,2)))

# Make a Numpy array of 1 values of three columns
print(numpy.ones(3))

# Make an empty Numpy array
print(numpy.empty(shape=(0,0)))
```

    []
    [[ 0.  0.]
     [ 0.  0.]
     [ 0.  0.]
     [ 0.  0.]]
    [ 1.  1.  1.]
    []


## Do math with lists (wt avg)


```python
cost = [0.424, 0.4221, 0.4185, 0.4132, 0.413]
cases = [10, 20, 30, 40, 50]
```


```python
for c in range(len(cost)):
   cost[c] = (cost[c] * cases[c] / sum(cases))
cost = sum(cost)
print(cost)
```

    0.41609999999999997



```python
cost = [0.424, 0.4221, 0.4185, 0.4132, 0.413]
cases = [10, 20, 30, 40, 50]

sum(cost[c] * cases[c] / sum(cases) for c in range(len(cost)))
```




    0.41609999999999997




```python
cost = [0.424, 0.4221, 0.4185, 0.4132, 0.413]
cases = [10, 20, 30, 40, 50]

sum(cost[c] * cases[c] for c in range(len(cost))) / sum(cases)
```




    0.41609999999999997




```python
cost = [0.424, 0.4221, 0.4185, 0.4132, 0.413]
cases = [10, 20, 30, 40, 50]

# See what `zip()` does to your `cost` and `cases`
print(list(zip(cost, cases)))
# zips your lists together

# Calculate the weighted average
print(sum([x * y for x, y in zip(cost, cases)]) / sum(cases))
```

    [(0.424, 10), (0.4221, 20), (0.4185, 30), (0.4132, 40), (0.413, 50)]
    0.41609999999999997


## Do math with lists (quantiles)


```python
# Import numpy as np
import numpy as np

# Make a Numpy array
a = np.array([1,2,3,4,5])

# Return the 50th percentile of our Numpy array
p50 = np.percentile(a, 50)

#Print the result
print(p50)

print(np.percentile(a, (25, 75)))
```

    3.0
    [ 2.  4.]


## Do math with lists (`sum`)


```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]

from operator import add
list(map(add, list1, list2))
```




    [5, 7, 9]




```python
[sum(x) for x in zip(list1, list2)]
```




    [5, 7, 9]




```python
# Import numpy as np
import numpy as np

# Make your lists into Numpy arrays
vector1 = np.array([1, 2, 3])
vector2 = np.array([4, 5, 6])

# Element-wise addition
sum_vector = vector1 + vector2 

# Print the result
print(sum_vector)
```

    [5 7 9]

