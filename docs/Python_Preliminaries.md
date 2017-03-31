# Python Preliminaries

**Foreword**

Notes.

-----

[TOC]

-----

## Installing

**Python**

- Installing Python, basic libraries, and virtual environments.
    - http://docs.python-guide.org/en/latest/starting/install/win/#install-windows
    - http://docs.python-guide.org/en/latest/starting/install/linux/

**pip**

<sub>pypi</sub>

Important commands:

- `pip help` ou `pip --help`,
- `pip install <module>`,
- `pip uninstall <module>`,
- `pip install --user <module>`: circumvent the `sudo` command.

**Virtual environment**

<sub>virtual, environment, separate, project</sub>

When you install a library, it is accessible to all python scripts. Project A and B have access to the library. 

It brings out a problem if "Project A depends on version 1.x but, Project B needs 4.x". This problem is recurrent when working with web frameworks. For example, you can work on a project which requires Django 1.3 while also maintaining a project which requires Django 1.0.

A virtual environment solves this problem by building a sandbox for a project.

Find more in the resources.

## Launching

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

**Launch a script**

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
    
## Better Python

Install the `flake8` module to inspect a script with PEP8. The module integrates with IDE and text editors (VIM, Emacs, gedit, Notepad++, etc.).

Install the `pdb` module: the debugger. The module runs within IDE or in the terminal by adding a few lines of code to a script.