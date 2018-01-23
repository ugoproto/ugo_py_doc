---

[TOC]

---

**Foreword**

Notes. Python and gedit.

---

- In the gedit menu: Tools/Manage External Tools
- On the left, add: Execute Highlighted Python Code
- On the right, add:

~~~
#!/usr/bin/env python3
import sys
exec(sys.stdin.read())
~~~

- At the bottom,
    - Choose a shortcut key: `Alt+x`.
    - Input: `Current selection (default to document)`.
    - Output: `Display in bottom pane`.
    - Do not change the other parameters.
- Create a python document (.py), add Python code, highlight the code, and press `Alt+x`: a bottom pane opens showing the results.
- The external tool is now part of gedit and ready to use.

---
