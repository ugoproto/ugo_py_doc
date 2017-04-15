---

[TOC]

---

**Foreword**

Notes. Python 2. Consult the [Hitchicker's Guide to Python](http://docs.python-guide.org/en/latest/).

---

## 1, `mistune` Converts Documents

<sub>convert, conversion, document, file</sub>

mistune is a markdown parser, turn into HTML markdown

The `mistune` module is a markdown parser that turns markdown file into HTML. Run this script to see the html result in the terminal. For more on converting documents, check Pandoc. Install `mistune` with pip.

```python
import mistune

text_block = 'The `mistune` module converts .md to .html.'
  
html_block = mistune.markdown(text_block) # convert to html

print html_block
```

Or run this command  to produce a .html document:

```bash
python mistune_pgm.py > mistune_html.html
```

## 2, `logging` Collects Data

- Logging is a library recording what users pass in the code.
- It creates log files (text documents); it collects data.
- First, it is a good tool for gathering data.
- Second, it could also be a good tool for debugging; we can monitor what is inputed in the variables.

We have a starting script.

```python
def get_location(monster, door, player):
    """Takes 3 arguments; string type.
	Asks to enter 3 inputs.
	Uses the 3 inputs in a sentence to print a sentence.
	"""
    
    print "The %s behind the %s door was slayed by %s." % (monster, door, player)


monsterr = raw_input("Enter a monster type: ")
doorr = raw_input("Enter a door color: ")
playerr = raw_input("Enter the player's name: ")

get_location(monsterr, doorr, playerr)
```

We run the script, the console displays 3 input messages, we input strings (Blob, blue, Al), and the script prints the results.

```python
The Blob behind the blue door was slayed by Al.
```

Now, we add the `logging` library.

```python
import logging


logging.basicConfig(filename='game.log', level=logging.DEBUG) # invisible to the user


def get_location(monster, door, player):
    """
    Takes 3 arguments; string type.
    Asks to enter 3 inputs.
    Uses the 3 inputs in a sentence to print a sentence.
    """

    print "The %s behind the %s door was slayed by %s" % (monster, door, player)


monsterr = raw_input("Enter a monster type: ")
doorr = raw_input("Enter a door color: ")
playerr = raw_input("Enter the player's name: ")
    
get_location(monsterr, doorr, playerr)

logging.info('monsterr: {}; doorr: {}; playerr {}'.format(
    monsterr, doorr, playerr)) # invisible to the user
```

The user does not see the difference. But anytime someone runs the script, inputs are save to a log file: game.log.txt.

We open the file.

```text
INFO:root:monsterr: Blob; doorr: blue; playerr Al
INFO:root:monsterr: Puik; doorr: red; playerr Felicia
```

In the `logging.basicConfig` function, we select `level=logging.DEBUG`.

There are 6 log levels (higher to lower): `CRITICAL`, `ERROR`, `WARNING`, `INFO`, `DEBUG`, `NOTSET`.

- `INFO`, `DEBUG` are information about the running of an app.
- `WARNING` is for keeping track of questionable or exceptional things happening.
- `ERROR`, `CRITICAL` are for when things go wrong.

## 3, `PIL` Manipulates Images

The `PIL` package stands for 'Python Image library' or Pillow. Pillow adds image processing capabilities. The library supports many file formats and provides powerful image processing and graphics capabilities. Given these images:

| ballons.jpg | ribbons.jpg |
|-----|-----|
| ![](img/image_balloons.jpg) | ![](img/image_ribbons.jpg) |

```python
import PIL

ballons = Image.open('ballons.jpg')
ribbons = Image.open('ribbons.jpg')

# pixels; left, top, right, bottom (clockwise)
box = (22, 324, 826, 846)
ballons.crop(box).show()

ballons.rotate(90).show()

ballons.rotate(45).show() # won't work

ballons.rotate(45, expand = True).show() # instead

ballons.rotate(90).save('balloon2,jpg') # to the same directory
ballons.rotate(90).save('path/balloon2,jpg') # to another directory
```