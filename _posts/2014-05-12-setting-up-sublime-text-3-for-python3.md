---
layout: post
title: "Setting Up Sublime Text 3 for Python3"
description: "help sublime text run python3 scripts"
category: blogs
tags: [Python, SublimeText]
---
{% include JB/setup %}
I'm recently studying Python3 programing. I use SublimeText as my editor. There is one problem that SublimeText can only run Python2 scripts becasue it is the default version on OSX even if the Python3 has already been installed. Here below is the solution.
##Python3 build
Go to：
tools -- build system -- new build system
Create a file named **Python3.sublime-build** and write in it：
```
{
    "cmd": ["/usr/local/bin/python3", "-u", "$file"],
    "file_regex": "^[ ]*File \"(...*?)\", line ([0-9]*)",
    "selector": "source.python",
    "encoding": "utf8",
    "path": "/usr/local/Frameworks/Python.framework/Versions/3.3/bin/"
}
```
##Install SublimeREPL
First install the [package control](https://sublime.wbond.net/installation#st3)；
Then go to: 
preferences -- package control -- install package 
search **SublimeREPL** and install.
##Make Python3 Running in SublimeREPL
Go to directory: 
/Users/jared/Library/Application Support/Sublime Text 3/Packages/SublimeREPL/config/Python
open **Main.sublime-menu**，find the content which contains **Python - RUN current file**, replace the content with：
```
{"command": "repl_open",
 "caption": "Python3 - RUN current file",
 "id": "repl_python_run",
 "mnemonic": "d",
 "args": {
            "type": "subprocess",
            "encoding": "utf8",
            "cmd": ["python3", "-u", "$file_basename"],
            "cwd": "$file_path",
            "syntax": "Packages/Python/Python.tmLanguage",
            "external_id": "python",
            "extend_env": {"PYTHONIOENCODING": "utf-8"}
            }
}
```
##Setting Up the RUN current file shortcut
Go to **preferences -- key bindings - user**, and fill in：
```
[ 
    {"keys":["command+p"],
        "caption": "SublimeREPL: Python3 - RUN current file",
        "command": "run_existing_window_command", "args":
        {
            "id": "repl_python_run",
            "file": "config/Python/Main.sublime-menu"
        }
    }
]
```
