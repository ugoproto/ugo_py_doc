<!--
---

[TOC]
-->
---

**Foreword**

Notes.

---

# Understanding Python Exception

[Python built-in exceptions](https://docs.python.org/3/library/exceptions.html)


```python
def simple_div(x,y):
    z = x / y
    return z

simple_div(2,2)
```




    1.0




```python
simple_div(0,2)
```




    0.0




```python
simple_div(2,0)
```


    ---------------------------------------------------------------------------

    ZeroDivisionError                         Traceback (most recent call last)

    <ipython-input-3-95e9e8e0b13c> in <module>
    ----> 1 simple_div(2,0)
    

    <ipython-input-1-69d8d8976ddb> in simple_div(x, y)
          1 def simple_div(x,y):
    ----> 2     z = x / y
          3     return z
          4 
          5 simple_div(2,2)


    ZeroDivisionError: division by zero


0 is divisible by any number, but returns 0.  
But a number cannot be divided by nothing (0).

This is an exception, a python exception, called in this case ZeroDivisionError.

```python
simple_div(2,'a')
``` 

...is an exception called TypeError.


```python
simple_div(2,a)
``` 

...is a NameError.

# Catching Exceptions

Let’s catch exception ZeroDivisionError.


```python
def simple_div_2(x,y):
    try:
        z = x / y
        return z
    except ZeroDivisionError:
        print("Divided by 0!")

simple_div_2(2,0)
```

    Divided by 0!



```python
try:
    print(simple_div_2(2,0))
except ZeroDivisionError:
    print("Divided by 0!")
```

    Divided by 0!
    None


Let’s catch exception TypeError.


```python
def simple_div_3(x,y):
    try:
        z = x / y
        return z
    except TypeError:
        z = -1
        return z
    
simple_div_3(2,'a')
```




    -1



Let’s catch exception NameError.


```python
try:
    print(simple_div(2,a))
except NameError:
    print(-2)
```

    -2


Let’s put it all together!


```python
def simple_div_5(x,y):
    try:
        z = x / y
        return z
    except ZeroDivisionError:
        return ("Divided by 0!")
    except TypeError:
        z = -1
        return z
```


```python
try:
    print(simple_div_5(2,2))
except NameError:
    print(-2)
```

    1.0



```python
try:
    print(simple_div_5(0,2))
except NameError:
    print(-2)
```

    0.0



```python
try:
    print(simple_div_5(2,0))
except NameError:
    print(-2)
```

    Divided by 0!



```python
try:
    print(simple_div_5(2,'a'))
except NameError:
    print(-2)
```

    -1



```python
try:
    print(simple_div_5(2,a))
except NameError:
    print(-2)
```

    -2

