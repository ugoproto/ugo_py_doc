<!--
---

[TOC]
-->
---

**Foreword**

Code snippets and excerpts from the tutorial. Python 3. From DataCamp. Some images can only be simulated with Jupyter since they are are interactive.

---

# Overview

Image data can be taken with ordinary cameras (these are often called “natural images” in the scientific literature) or with specialized instruments, such as microscopes or telescopes.

The most common way to display them is using the `imshow` function of Matplotlib.

For example, magnetic resonance imaging (MRI) and computed tomography (CT) scans measure the 3D structure inside the human body; X-ray microtomography measures the 3D structure inside materials such as glass, or metal alloys; and light-sheet microscopes measure fluorescent particles inside biological tissues.

Enable the interactive matplotlib mode.

Other applications: spatial analysis (visualization over time), maps (layers of a neighbourhood over time), etc. 


```python
%matplotlib notebook
```

When running matplotlib in the interactive notebook mode, the open figure remains the only active figure until disabled, using the power symbol on the top-right of the figure. Do that before moving on from each plot.


```python
import matplotlib.pyplot as plt
from skimage import data

astronaut = data.astronaut()
ihc = data.immunohistochemistry()
hubble = data.hubble_deep_field()

# Initialize the subplot panels side by side
fig, ax = plt.subplots(nrows=1, ncols=3)

# Show an image in each subplot
ax[0].imshow(astronaut)
ax[0].set_title('Natural image')
ax[1].imshow(ihc)
ax[1].set_title('Microscopy image')
ax[2].imshow(hubble)
ax[2].set_title('Telescope image');
```


**>>> Interactive images here! <<<**


These images are called 2-dimensional or 2D images. Some images are 3D, in that they have an additional depth dimension (z, or planes). These include magnetic resonance imaging (MRI) and serial section transmission electron microscopy (ssTEM), in which a sample is thinly sliced, like a salami, and each of the slices is imaged separately.


```python
import nibabel
```

# Interlude: Getting The Data…

Dataset source: Buchel and Friston, Cortical Interactions Evaluated with Structural Equation Modelling and fMRI (1997).


```python
import tempfile

# Create a temporary directory
d = tempfile.mkdtemp()

print(d)
```

    /tmp/tmp8xdzu1ad



```python
import os

os.chdir('/home/ugo/Documents/Notebooks/DataCamp, Matplotlib tutorial')
print(os.getcwd())
```

    /home/ugo/Documents/Notebooks/DataCamp, Matplotlib tutorial



```python
d = os.getcwd()
print(d)
```

    /home/ugo/Documents/Notebooks/DataCamp, Matplotlib tutorial



```python
# Return the tail of the path
os.path.basename('http://google.com/attention.zip')
```




    'attention.zip'



## Download the Data


```python
from urllib.request import urlretrieve

# Define URL
url = 'http://www.fil.ion.ucl.ac.uk/spm/download/data/attention/attention.zip'

# Retrieve the data
fn, info = urlretrieve(url, os.path.join(d, 'attention.zip'))
```

Extract it from the zip file to our temporary directory.


```python
import zipfile

# Extract the contents into the temporary directory we created earlier
zipfile.ZipFile(fn).extractall(path=d)

# List first 10 files
[f.filename for f in zipfile.ZipFile(fn).filelist[:10]]
```




    ['attention/',
     'attention/multi_block_regressors.mat',
     'attention/README_DATA.txt',
     'attention/factors.mat',
     'attention/functional/',
     'attention/functional/snffM00587_0201.hdr',
     'attention/functional/snffM00587_0040.img',
     'attention/functional/snffM00587_0458.hdr',
     'attention/functional/snffM00587_0185.img',
     'attention/functional/snffM00587_0018.hdr']



These are in the NIfTI file format. 
`nibabel` library provides the reader. 

Install it with either: `conda install -c conda-forge nibabel` or `pip install nibabel`.


```python
import nibabel

# Read the image 
struct = nibabel.load(os.path.join(d, 'attention/structural/nsM00587_0002.hdr'))

# Get a plain NumPy array, without all the metadata
struct_arr = struct.get_data()

# Plot the MRI data
from skimage import io

struct_arr = io.imread("https://s3.amazonaws.com/assets.datacamp.com/blog_assets/attention-mri.tif")

plt.imshow(struct_arr[75])
```

**>>> Interactive images here! <<<**

# … Back To Plotting


```python
# fix the aspect parameter
plt.imshow(struct_arr[75], aspect=0.5)

# transpose the data
# horizontal slices
struct_arr2 = struct_arr.T
plt.imshow(struct_arr2[34])

# slice along a different axis
plt.imshow(struct_arr2[5])
```

**>>> Interactive images here! <<<**

Explore 3D data within Python, minimizing the need to switch contexts between data exploration and data analysis.

The key is to use the matplotlibevent handler API.

https://matplotlib.org/users/event_handling.html

Bind the J and K keys on the keyboard to previous slice and next slice.


```python
def previous_slice():
    pass

def next_slice():
    pass

def process_key(event):
    if event.key == 'j':
        previous_slice()
    elif event.key == 'k':
        next_slice()
```

Use the `process_key` function to process keyboard presses and the figure canvas method `mpl_connect`.


```python
fig, ax = plt.subplots()
ax.imshow(struct_arr[..., 43])
fig.canvas.mpl_connect('key_press_event', process_key)
```

**>>> Interactive images here! <<<**

`imshow` returns an `AxesImage` object, which lives inside the matplotlib `Axes` object where all the drawing takes place, in its `.images` attribute. This object provides a convenient `set_array` method that swaps out the image.


```python
def multi_slice_viewer(volume):
    fig, ax = plt.subplots()
    ax.volume = volume
    ax.index = volume.shape[0] // 2
    ax.imshow(volume[ax.index])
    fig.canvas.mpl_connect('key_press_event', process_key)

def process_key(event):
    fig = event.canvas.figure
    ax = fig.axes[0]
    if event.key == 'j':
        previous_slice(ax)
    elif event.key == 'k':
        next_slice(ax)
    fig.canvas.draw()

def previous_slice(ax):
    """Go to the previous slice."""
    volume = ax.volume
    ax.index = (ax.index - 1) % volume.shape[0]  # wrap around using %
    ax.images[0].set_array(volume[ax.index])

def next_slice(ax):
    """Go to the next slice."""
    volume = ax.volume
    ax.index = (ax.index + 1) % volume.shape[0]
    ax.images[0].set_array(volume[ax.index])
```

Go!


```python
multi_slice_viewer(struct_arr2)
```

**>>> Interactive images here! <<<**

Matplotlib simply piles them on on top of each other.

K is a built-in keyboard shortcut to change the x-axis to use a logarithmic scale.
If we want to use K exclusively, we have to remove it from matplotlib’s default
key maps.

These live as lists in the `plt.rcParams` dictionary, which is matplotlib’s 
repository for default system-wide settings:
    
`plt.rcParams['keymap.<command>'] = ['<key1>', '<key2>']` 
where pressing any of the keys in the list (i.e. `<key1>` or `<key2>`) 
will cause `<command>` to be executed.

Let’s rewrite the function.


```python
def multi_slice_viewer(volume):
    remove_keymap_conflicts({'j', 'k'})
    fig, ax = plt.subplots()
    ax.volume = volume
    ax.index = volume.shape[0] // 2
    ax.imshow(volume[ax.index])
    fig.canvas.mpl_connect('key_press_event', process_key)

def process_key(event):
    fig = event.canvas.figure
    ax = fig.axes[0]
    if event.key == 'j':
        previous_slice(ax)
    elif event.key == 'k':
        next_slice(ax)
    fig.canvas.draw()

def previous_slice(ax):
    volume = ax.volume
    ax.index = (ax.index - 1) % volume.shape[0]  # wrap around using %
    ax.images[0].set_array(volume[ax.index])

def next_slice(ax):
    volume = ax.volume
    ax.index = (ax.index + 1) % volume.shape[0]
    ax.images[0].set_array(volume[ax.index])
```

We should be able to view all the slices in our MRI volume without pesky interference from the default keymap! One nice feature about this method is that it works on any matplotlib backend!

So, in the IPython terminal console, we will still get the same interaction as we did in the browser! And the same is true for a Qt or Tkinter app embedding a matplotlib plot.

This simple tool therefore lets us build ever more complex applications around matplotlib’s visualization capabilities.


```python
#multi_slice_viewer(struct_arr2)
```

Delete the temporary directory.


```python
d = tempfile.mkdtemp()

print(d)
```

    /tmp/tmpyylc3632



```python
import shutil

# Remove the temporary directory
shutil.rmtree(d)
```
