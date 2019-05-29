---
layout: post
title:  "Custom setup.py Commands"
categories: software-development
tags: [setup.py, python, packaging, custom, extension]
---
It appears that one can install a custom command in either of these places:
* cmdclass vs. distutils.commands

This makes the commands available to libraries that include this package in 
`setup_requires`:
```
setup(
    ...
    entry_points={
        ...
        "distutils.commands": [
            "my_command = my_package:MyCommand",
            "my_other_command = my_package:MyOtherCommand",
        ],
    },
    ...
)
```

This makes the commands available to this project only:

```
from my_package import MyCommand, MyOtherCommand
...
setup(
    ...
    cmdclass={
        "my_command": MyCommand,
        "my_other_command": MyOtherCommand,
    },
    ...
```
