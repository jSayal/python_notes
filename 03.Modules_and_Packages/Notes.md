# Modules & Packages

Python supports modular programming. A module comprise a piece of program. For example, if you are programming a game you can have one module dealing with the game logic and other with the display. When we program, using modules it is called **Modular programming**. Modules can be written as procedures or classes (OOP). It is upto programmer to choose which approach is suited for a particular task. 

## Modules

In Python a module is just a .py file. Modules is the only way to namespace code in Python.

> PEP 20 -- The Zen of Python says
>
> Namespaces are one honking great idea -- let's do more of those!
>
> In Python REPL, if you type ```import this``` and hit Enter, you will get Zen of Python.

Since everything is Python is an object, a module is also an object. Objects have attributes so modules have attributes as well. ```__name__``` is an attribute of Python module that describes it's name. Python module name is same as filename but without .py extension. Every python module has it's own symbol table, which defines the names of all variables & functions. Symbol table also stores type, scope level and sometimes location of identifiers (Symbol table concept will be discussed in detail later).

```
__name__ attribute is important, as it tells us that if a python file is being executed as string or a module. 

When python file is being used as script __name__ value is set to __main__, otherwise its the name of file.
```

Let's write a very simple python module named demo.py. Create a new file and name it demo.py.

```Python
def add (num1, num2):
  return num1 + num2

def mult (num1 * num2):
  return num1 * num2

# The following code is executed only if this Python file is being executed as script.
if __name__ == '__main__':
  print(add(2, 2))
```

Modules can be imported in other .py files. There are three variations of `import` statement.

```Python
# import <module_name>
import math
# The above statement will import math module and all the
# functions and variables can be accessed by using math. prefix.
# import statement only enters the name of module math in current
# symbol table.

print(math.pi)
# Output is 3.141592653589793

# from <module_name> import <identifier>
from math import pi
# The above statement will import pi constant from math module 
# into current symbol table.
```

### Module search path

When a module is imported, the interpreter first searches for built-in modules. If not found, then it searches for module in paths given by`sys.path`. sys.path is initialized from these locations

- directory containing the executing script
- PYTHONPATH
- installation dependent default

```Python
import sys
for path in sys.path:
  print(path)
  
# Outptut on my Mac is as follows
#/usr/local/Cellar/python/3.7.0/Frameworks/Python.framework/Versions/3.7/lib/python37.zip
#/usr/local/Cellar/python/3.7.0/Frameworks/Python.framework/Versions/3.7/lib/python3.7
#/usr/local/Cellar/python/3.7.0/Frameworks/Python.framework/Versions/3.7/lib/python3.7/lib-dynload
#/usr/local/lib/python3.7/site-packages
```

### dir(<module_name>)

`dir ` function can be used to see all the names defined by a module. It returns a sorted list of strings.

```python
import math
print(dir(math))

# dir do not list the names of built-in functions and variables.
# To get list of built-in functions

import builtins
dir(builtins)
```

A module is only loaded once per interpreter sesssion. If a module contain any executable code as part of initialisation, it is also exected once. If for any reason you need to reload a module use `reload` function.

```Python
import math

# ... some code here

# For some reason, now we need to reload math module
import importlib
import importlib.reload(math)
```

## Packages

Packages are collection of modules separated into different directories. In later chapters, we will write a small package to demonstrate this concept. For now this information is enough.

## Functions

A function is a group of statements that execute upon request. Python provides many builtin function and allows programmers to create their own functions. A request to execute function is called function call. In Python, a function always returns a value, it can be None or result of computation.

Functions are first class objects in Python, means they are just like any other object in Python. Functions can be passed as argument to another function, a function can return a function, function can be bound to a variable, function can be an item in a container and can be attribute of an object.

Functions are basic block of code reuse in python. It groups related set of statements so that they can be executed together.

```Python
def print_full_name (first_name, last_name):
  print(first_name + last_name)

```

## Methods

Methods are essentially functions built into objects. We have used various methods of list object like append, count, extend etc. Methods are more related to object oriented programming. In next section, we will go over classes and discuss Python OOP model and methods in detail. For now, Any function that operates on an object is called method, and if a function is by itself it is a function.

