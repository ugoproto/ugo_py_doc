# Freeze the Code

**Foreword**

Notes.

-----

[TOC]

-----

- Freezing a Python file is similar to compiling the file. When running the executable file, the code runs faster than with interpreted code.
    - http://docs.python-guide.org/en/latest/shipping/freezing/?highlight=freeze
- It is done on Windows in the following examples.
- It can be executed on all OS: Windows, Linux and Max OS X (using Wine for all UNIX OS).

## Distutils (an Overview)

- Building with distutils works well on all OS.
- The package provides support for building and installing additional modules (libraries or packages) into a Python installation.
- The new modules may be either 100%-pure Python, written in C, or coded in both Python and C.
- `distutils` autogenerates an install script.

**Documentation**

- https://wiki.python.org/moin/Distutils/Tutorial
- https://docs.python.org/2/distutils/

## cx-Freeze (with Snippets)

- `cx_Freeze` freezes Python scripts into executables.
- Alike `py2exe` for Windows only and `py2app` for Mac OS X only.
- Building with `cx_Freeze` works best on Windows.
- Supports Python 2.3 or higher (including Python 3).
- Simpler than `distutils`.

**Documentation**

- http://cx-freeze.readthedocs.io
- https://anthony-tuininga.github.io/cx_Freeze/
- Install `cx_Freeze` (works on Pyhon 2 & 3).
    - The easiest way is with `pip install cx_Freeze`.
    - `pip3 install cx_Freeze`.

**Procedure with a single script**

Have the `hello.py` ready.

```python
def main():
print("Hello World")
input("nPlease press ENTER to continue...")

if __name__ == "__main__":
main()
```

- Create a `setup.py`.
    - Find out more in the doc.
- Simple setup.

```python
import sys
from cx_Freeze import setup, Executable

setup(
name = "Hello",
version = "0.1",
description = "A general utility",
executables = [Executable("hello.py", base = None)]
)
```

- Better setup.

```python
import sys
from cx_Freeze import setup, Executable

includefiles = [] # include any files here that you wish
excludes = []
packages = []

exe = Executable(
# what to build
script = "hello.py", # the name of the main python script goes here 
initScript = None,
base = None, # if creating a GUI instead of a console app, type "Win32GUI"
targetName = "hello.exe", # the name of the executable file
icon = None # if you want to use an icon file, specify the file name here
)

setup(
# the actual setup & the definition of other misc. info
name = "Hello", # the program name
version = "0.1",
description = "A general utility",
author = "Your name",
author_email = "your@email.com",
options = {"build_exe": {"excludes":excludes,"packages":packages, "include_files":includefiles}},
executables = [exe]
)
```

- Place the files in C:\PythonXX\, where pip and Python are installed.
- Make sure the path is in the environment variables or exported (we assume this is understood and done).
- Open the shell (cmd), go to the C:\PythonXX\ directory.
- Build the executable by calling the `setup.py` script with the Python version of our choice.

```python
python setup.py build
```

- The created files are located in C:\PythonXX\build...
- Go in the subfolder, find the .exe file and launch it.
- On Linux and Mac OS X, the .exe file must to be run with Wine (executing Windows apps)
- Build an installer for Windows containing all the files.

```python
python setup.py bdist_msi
```

- The installer is located in C:\PythonXX\dist\
- It can be distributed and installed/repaired/removed as a Windows program.
- The installation creates what the build command does in a directory of our choice.
- Build an installer on Mac OS X.

```python
python setup.py bdist_dmg
```

- Procedure with a set of scripts (with folders)

- The project might look like this.

```text
└───project
    ├───bin
    └───map
```

- Under the project folder, the bin folder contains the main .py file to be launched; this file relies on other files in its own folders or in the other folders.
- The setup.py and project folders (bin, map, …) are located in C:\PythonXX\
- Create a `setup.py`.
    - Find out more in the doc.
- Simple setup (or a more elaborate setup).

```python
import sys
from cx_Freeze import setup, Executable

setup(
name = "Any Names",
version = "0.1",
description = "Any Description",
executables = [Executable("bin/FileName.py", base = None)]
)
```

- Build the executable by calling the setup.py script with the Python version of choice.

**Pros & Cons**

- It can handle a set of files (such as with the last example).
- Linux and Mac OS X can read the executable (using Wine).
- Easy to deploy (download, open, execute).
- It does not generate a single file, except with the `bdist_` commands. However, a distribution requires additional steps to deploy.

## pyInstaller (with Snippets)

- `pyinstaller` is a simpler alternative to cx-Freeze.
- Libraries like `PyQt`, `Django` or `matplotlib` are fully supported, without having to handle plugins or external data files manually.

**Documentation**

- http://www.pyinstaller.org/
- https://github.com/pyinstaller/pyinstaller
- Install pyinstaller (works on Pyhon 2 & 3).
    - The easiest way is with `pip install pyinstaller`.
    - `pip3 install pyinstaller`.

**Procedure with a single script**

- Have the `hello.py` ready.

```python
def main():
print("Hello World")
input("nPlease press ENTER to continue...")

if __name__ == "__main__":
main()
```

- Place the files in C:\PythonXX\, where pip and Python are installed.
- Make sure the path is in the environment variables or exported (we assume this is understood and done).
- Open the shell (cmd), go to the C:\PythonXX\ directory.
- Build the executable.

```python
pyinstaller hello.py
```

Or

```python
pyinstaller -D hello.py
```

- The created files are located in C:\PythonXX\dist...
- Go in the subfolder, find the .exe file and launch it.
- The default option is `-D` (above) is facultative.
- Build the single executable file with the bundle option `-F` (below).

```python
pyinstaller -F hello.py
```

- The created file is located in C:\PythonXX\dist...

- Find the single .exe file and launch it.

- Build with an icon (.ico file)
- The .ico and .py files are located in the same folder, otherwise we have to specify the path with filename.ico.

```python
pyinstaller -F -i "favicon.ico" hello.py
```

- Procedure with a set of scripts (with folders)

- The project might look like this.

```text
└───project
    ├───bin
    └───map
```

- Under the project folder, the bin folder contains the main .py file to be launched; this file relies on other files in its own folders or in the other folders.

- The setup.py and project folders (bin, map, …) are located in C:\PythonXX\

- Build the single executable file.

```python
pyinstaller -F -i "favicon.ico" bin/hello.py
```

**Pros & Cons**

- It can handle a set of files (such as with the last example).
- Linux and Mac OS X can read the executable (using Wine).
- Easy to deploy (download, open, execute). Easier than with cx-Freeze, but without the flexibility a `setup.py` file can allow.
- However, it can generate a single file: dowload, then launch in a single click.

## Nuitka (an Overview)

- Python compiler compatible with CPython.
- Works on all OS.
- Compiled files are faster.

**Documentation**

- http://nuitka.net/pages/overview.html.
- Check out the requirements.
    - Need for a C++ compiler.

## PyPy (an Overview)

- Alternative to CPython: RPython (restricted Python).
- Works on all OS, best on Linux.
- Compiled files are faster.

**Documentation**

- http://pypy.org/index.html