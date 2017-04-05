# Python Decorators

**Foreword**

Notes and code snippets. Python 3. Consult the [Hitchicker's Guide to Python](http://docs.python-guide.org/en/latest/).

-----

[TOC]

-----

## The Goal of Decorators

**Decorators vs the Decorator Pattern**

Python decorators are best equated to macros.

**Definition**

- They modify functions, and in the case of class decorators, entire classes. They provide a simpler alternative to metaclasses.
- A decorator itself is a callable that returns a callable.
- A decorator is a function that takes a function object as its argument, and returns a function object, and in the process, makes necessary modifications to the input function, possibly enhancing it.
- Useful for:
	- bookkeeping,
	- repeating insularity functionalities,
	- adding functionality of the function,
	- modifying the behavior of the function;
	- in Django, Flask or other web frameworks.

## First Thing First

**First dive**

Decorators are easy to add or remove. They are nested functions; inserted in another function.

Below, `inner()` can live inside `outer()`. When you call `outer()`, you can also call `inner()`.

```python
from functools import wraps

def outer():
	number = 5
	
	def inner():
		print(number)
		
	inner()
    
outer() # print 5
inner() # cannot be called
```

Functions are first-class objects that can be passed around:

```python
def apply(func, x, y):
	return func(x, y)

def add(x, y):
	return x + y

def sub(x, y):
	return x - y

print(apply(add, 5,5)) # call apply(), that calls add()
print(apply(sub, 2,8)) # call apply(), that calls sub()
```

Output:

```text
10
-6
```

'Predefine scope': define the environment for the function. `inner()` has only access to `outer()` and `number = 5`.

```python
def close():
	x = 5
	
	def inner():
		print(x)
	
	return inner
	
closure = close() # change the function name
closure() # call the 'new' function
```

Output:

```text
5
```

```python
def add_to_five(num):
	
	def inner():
		print(num + 5)
	
	return inner
	
fifteen = add_to_five(10)
fifteen()
```

Output: 
```text
15
```

**Take two !**

A decorator is a function that accept function as an argument and returns a function.

`f()` is an object, and it's not different from classes (`MyClass`) or variables (`a`).

```python
>>> a = 10
>>> def f():
...     pass
...
>>> class MyClass():
...     pass
...
>>> print dir()
['MyClass', '__builtins__', '__doc__', '__name__', '__package__', 'a', 'f']
```

Assign a function to a variable:

```python
def func():
   print "func()"

funcObj = func
funcObj() # inheritance from func()
```

Functions can be passed around in the same way other types of object such as strings, integers, lists, etc. 

A function can accept a function as an argument and return a new function object:

```python
def myFunction(in_function):
   def out_function():
      pass
   return out_function
```

The `myFunction` is indeed a decorator because, by definition, a decorator is a function that takes a function object as its argument, and returns a function object (!!!).

Elaborate:

```python
def myFunction(in_function):
   def out_function():
      print "Entry: ", in_function.__name__
      in_function()
      print "Exit: ", in_function.__name__
   return out_function
```

## Invoking a Decorator

Put a simple_function into the decorator (`myFunction`) as an argument, and get a `enhanced_function` as a return value from the decorator.

```python
def simple_function():
   pass
	
enhanced_function = myFunction(simple_function)
```

Apply the decorator syntax to the code above:

```python
@myFunction
def simple_function():
   pass
```

`@myFunction` is a decorator line or an annotation line. The `@` indicates the application of the decorator. A decorator is the function itself which takes a function, and returns a new function: `myFunction`.

When the compiler passes over this code, `simple_function()` is compiled. The resulting function object is passed to the `myFunction` code. It produces a function-like object that is substituted for the original `simple_function()`.

The static method:

```python
>>> class A:
...    def s(x):
...       print(x)
...    s = staticmethod(s)
... 
>>> A.s(10)
10
```

The equivalent code using a decorator looks like this:

```python
>>> class A:
...    @staticmethod
...    def s(x):
...       print(x)
...
>>> A.s(10)
10
```

For example, suppose you'd like to do something at the entry and exit points of a function (perform some kind of security, tracing, locking, etc.):

```python
@entryExit
def func1():
	print "inside func1()"

@entryExit
def func2():
	print "inside func2()"
```

Another example:

```python
>>> def wrapper(f):
...    return f
...
>>> def foo():
...    pass
...
```

Then, the wrapper can be used for rebinding `foo()` like this:

```python
>>> foo = wrapper(foo)
```

So, it's a decorator:

```python
>>> @wrapper
... def foo():
...    pass
```

With a decorator defined as below:

```python
def decorator(f):
   #process function
   return f
```

Maps the following:

```python
@decorator
def f(arg):
   return arg*arg

f(123)  # output 15129
```

Into:

```python
def f(arg):
   print arg*arg
f = decorator(f)
```

Decoration maps the following line:

```python
f(123)
```

Into:

```python
decorator(f)(123)
```

A function decorator is applied to a function definition by placing it on the line before that function definition begins:

```python
@myDecorator
def aFunction():
    print "inside aFunction"
```

The compiler passes over the code. The `aFunction()` is compiled. The resulting function object is passed to the `myDecorator` code. It produces a function-like object that is then substituted for the original `aFunction()`.

## Using Decorators

What should the decorator do? Anything!

Decorators allow you to modify code in functions or classes.

The only constraint upon the object returned by the decorator is that it can be used as a function. Any classes we use as decorators must implement `__call__`.

Expect the original function code to be used at some point:

```python
class myDecorator(object):

    def __init__(self, f):
        print "inside myDecorator.__init__()"
        f() # Prove that function definition has completed

    def __call__(self):
        print "inside myDecorator.__call__()"

@myDecorator
def aFunction():
    print "inside aFunction()"

print "Finished decorating aFunction()"

aFunction()
```

Run this code:

```python
inside myDecorator.__init__()
inside aFunction()
Finished decorating aFunction()
inside myDecorator.__call__()
```

The constructor for `myDecorator` is executed at the point of decoration of the function.

Call `f()` inside `__init__()`. The creation of `f()` is complete before the decorator is called.

The decorator constructor receives the function object being decorated. 

Capture the function object in the constructor and later use it in the `__call__()` method.

When `aFunction()` is called after it has been decorated, the `myDecorator.__call__()` method is called instead of the original code. The act of decoration replaces the original function object.

Before decorators were added:

```python
def foo():
	pass
foo = staticmethod(foo)
```

With the addition of the `@` decoration operator:

```python
@staticmethod
def foo():
	pass
```

This syntax brings the idea of "applying code to other code" (i.e.: macros).

**Slightly More Useful**

Use the code in the decorated functions:

```python
class entryExit(object):

    def __init__(self, f):
        self.f = f

    def __call__(self):
        print "Entering", self.f.__name__
        self.f()
        print "Exited", self.f.__name__

@entryExit
def func1():
    print "inside func1()"

@entryExit
def func2():
    print "inside func2()"

func1()
func2()
```
Output:

```text
Entering func1
inside func1()
Exited func1
Entering func2
inside func2()
Exited func2
```

The decorated functions now have the 'Entering' and 'Exited' trace statements around the call.

The constructor stores the argument, which is the function object. In the call, use the `__name__` attribute of the function to display that function's name. 

Then call the function itself.

**Using functions as decorators**

Replace the original function with an object of a class that has a `__call__()` method. But a function object is also callable. From the previous example, use a function instead of a class:

```python
def entryExit(f):
    def new_f():
        print "Entering", f.__name__
        f()
        print "Exited", f.__name__
    return new_f

@entryExit
def func1():
    print "inside func1()"

@entryExit
def func2():
    print "inside func2()"

func1()
func2()
print func1.__name__
```

`new_f()` is defined within the body of `entryExit()`. It is created and returned when `entryExit()` is called.  

`new_f()` is a closure; it captures the actual value of `f`.

Once `new_f()` has been defined, it is returned from `entryExit()`. The decorator mechanism can assign the result as the decorated function.

The output of `print func1.__name__` is `new_f`, because the `new_f` function has been substituted for the original function during decoration. If this is a problem, change the name of the decorator function before you return it:

```python
def entryExit(f):
    def new_f():
        print "Entering", f.__name__
        f()
        print "Exited", f.__name__
    new_f.__name__ = f.__name__
    return new_f
```

## Cases

**1 - Adding `$` to the return value from `price()` function**

```python
def dollar(fn):
    def new(*args):
        return '$' + str(fn(*args))
    return new

@dollar
def price(amount, tax_rate):
    return amount + amount*tax_rate
   
print price(100,0.1)
```

Output:

```text
$110
```

The dollar decorator function takes the `price()` function, and returns enhanced the output from the original `price()` after modifying the inner working. Note that the decorator enables us to do it without making any changes on the `price()` function itself.

A decorator works as a wrapper, modifying the behavior of the code before and after a target function execution, without the need to modify the function itself, enhancing the original functionality.

With the pound or euro as well:

```python
def pound(fn):
    def new(*args):
        return (u"\u00A3").encode('utf-8') + str(fn(*args))
        return '$' + str(fn(*args))
    return new

@pound
def price(amount, tax_rate):
    return amount + amount*tax_rate

print price(100,0.1)
```

**2 - How many times a function called?**

```python
def count(f):
    def inner(*args, **kargs):
        inner.counter += 1
        return f(*args, **kargs)
    inner.counter = 0
    return inner

@count
def my_fnc():
    pass

if __name__ == '__main__':
    my_fnc()
    my_fnc()
    my_fnc()

    print 'my_fnc.counter=',my_fnc.counter
```

Output:

```text
my_fnc.counter= 3
```

**3 - Timer**

```python
import time
def timer(f):
    def inner(*args, **kargs):
        t = time.time()
        ret = f(*args, **kargs)
        print 'timer = %s' %(time.time()-t) 
        return ret
    return inner

@timer
def my_fnc():
    pass

if __name__ == '__main__':
    my_fnc()
```

Output:

```text
timer = 5.96046447754e-06
```

## More Cases and Examples

[learnpython.org (tutorial, snippets)](http://www.learnpython.org/en/Decorators)

**Collected examples**

```python
def logme(func):
	import logging
	logging.basicConfig(level = logging.DEBUG)
	
	def inner():
		logging.debug("Called {}".format(func.__name__))
		
		return func()
	
	return inner
```

```python
def logme(func):
	import logging
	logging.basicConfig(level = logging.DEBUG)
	
	def inner(*args, **kwargs): # * for tuple, ** for dict.
		logging.debug("Called {} with args {} and kwargs {}".format(
			func.__name__, args, kwargs)) # to print the tuple and dict.
		
		return func(*args, **kwargs) # to use the tuple and dict.
	
	return inner
```

```python
def logme(func):
	import logging
	logging.basicConfig(level = logging.DEBUG)
	
	def inner(*args, **kwargs): # * for tuple, ** for dict.
		logging.debug("Called {} with args {} and kwargs {}".format(
			func.__name__, args, kwargs)) # to print the tuple and dict.
		
		return func(*args, **kwargs) # to use the tuple and dict.
	
	inner.__doc__ = func.__doc__
	inner.__name__ = func.__name__
	
	return inner
```

```python
def logme(func):
	import logging
	logging.basicConfig(level = logging.DEBUG)
	
	@wraps(func) # decorator
	def inner(*args, **kwargs): # * for tuple, ** for dict.
		logging.debug("Called {} with args {} and kwargs {}".format(
			func.__name__, args, kwargs)) # to print the tuple and dict.
		
		return func(*args, **kwargs) # to use the tuple and dict.
	
	# replace all this
	#inner.__doc__ = func.__doc__
	#inner.__name__ = func.__name__
	# with  from functools import wraps  at the top
	# functools packages
	# wraps is a decorator; see above
	
	return inner
```

```python
@logme
def sub(x, y):
	"""Returns the difference between two numbers"""
	return x - y
```
