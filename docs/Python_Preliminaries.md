# Python Preliminaries

**Foreword**

Notes. Consult the [Hitchicker's Guide to Python](http://docs.python-guide.org/en/latest/).

-----

[TOC]

-----

## 1, Installing (Complementary Details)

**Python**

- Installing Python, basic libraries, and virtual environments.
    - http://docs.python-guide.org/en/latest/starting/install/win/#install-windows
    - http://docs.python-guide.org/en/latest/starting/install/linux/
- Setting the path in Windows (examples):
    - `set PATH=%PATH%;C:\Python27`.
    - `set PATH=%PATH%;C:\Python27\Scripts`.
    - `set PATH=%PATH%;C:\PythonXX`.
    - `set PATH=%PATH%;C:\PythonXX\Scripts`.
- Setting the path in Linux (example):
    - `export PYTHONPATH=$PYTHONPATH:`.
    - ...

## 2, pip

<sub>pypi</sub>

PyPY directory of libraries.

Important commands:

- `pip help` ou `pip --help`.
- `pip install <module>`.
- `pip --version`.
- `pip install --upgrade pip`
- `sudo pip install <module>`.
- `pip uninstall <module>`.
- `pip install --user <module>`: circumvent the `sudo` command.

## 3, Git

After installing Git, to execute Python module in the Git Bash, (re)set the path in the Git Bash (example): `export PATH="$PATH:/c/Python27"`, 
`export PATH="$PATH:/c/Python27/Scripts"`, ... The Git Bash simulates a UNIX-type environment.

## 4, Virtual Environment

<sub>virtual, environment, separate, project</sub>

When you install a library, it is accessible to all python scripts. Project A and B have access to the library. 

It brings out a problem if "Project A depends on version 1.x but, Project B needs 4.x". This problem is recurrent when working with web frameworks. For example, you can work on a project which requires Django 1.3 while also maintaining a project which requires Django 1.0.

A virtual environment solves this problem by building a sandbox for a project.

## 5, Launching

Windows vs. UNIX (Linux or Mac OS X).

**At the top of scripts**

- In Windows, Python 2:
    - `#! python`
- Windows, Python 3:
    - `#! python 3`
- UNIX, Python 2:
    - `#!/usr/bin/env python`
- UNIX, Python 3:
    - `#!/usr/bin/env python 3`
- Add:
    - `# -*coding: utf-8 -*-`
    - `# -*coding: latin-1 -*-`

**Launch a script -- Part 1**

- In Windows, Python 2:
    - `python script.py`
    - `py script.py`
    - `py -2 script.py`
    - `py -2.7 script.py`
- In UNIX, Python 2:
    - `python script.py`
- In Windows, Python 3:
    - `py -3 script.py`
    - `py -3.5 script.py`
- In UNIX, Python 3:
    - `python3 script.py`
    
**Launch a script -- Part 2**

- In Windows (examples):
    - `py -2 -m pip install script` if `pip install script` does not work.
    - `py -2 -m pip install flake8`.
    - `py -2 -m pip install pylint`.    
    
**Launch the shell/bash**

- The shell, Python 2:
    - `python`
    - `py -2`
    - `py -2.7`
- The bash, Python 2:
    - `python`
    - `python2`
- The shell, Python 3:
    - `py -3`
    - `py -3.5`
- The bash, Python 3:
    - `python3`