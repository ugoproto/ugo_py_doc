# Python Nice to Have

**Foreword**

Notes.

-----

[TOC]

-----

## Mistune

<sub>convert, conversion, document, file</sub>

The `mistune` module converts .md to .html. Run this script to see the html result in the terminal. For more on converting documents, check Pandoc.

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

## Image Manipulation

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