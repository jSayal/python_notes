# 	Python Basics

##Basic data types

Python has very simple data types, that fulfils most of the needs. You do not have to declare the **type** of data, Python will infer data type automaically from the value. The operation of a Python program hinges on data it handles. Data values in Python are known as objects; each object, AKA *value* has a type.

Name|Type|Description
----|----|-----------
Integers|int|Whole numbers such as 1, 2, 400, etc
Floating point|float|Numbers with a decimal point 1.23 3.45 etc
Strings|str|Order sequence of characters "Hello world"
Lists|list|Ordered Sequence of objects
Dictionaries|dict|Unordred key/value pairs
Tuples|tup|Ordered immutable sequences of object
Sets|set|Unordered collection of unique objects
Boolean|bool|Logical values indicatoing true of false

### Numbers

Basic operations on numbers are **+, -, /, *, % and ** (power)**

### Strings

String are ordered sequences of characters, wrapped in single or double quotes. In this section, we will only go over basic operations on strings, Python has a large number of methods for transforming, searching and formatting strings. We will discuss some of the imporant methods, and you can read the reference later to get more information. 

Since strings are ordered collection, we can index and slice to get subsections of a string.

Indexing notation uses ```[ ]``` square brackets notation, and we can only get one character at a time. Indexing starts at 0 in python, see below a visualzation of string and its index

```
String	
    +---+---+---+---+---+---+
   | P | y | t | h | o | n |
   +---+---+---+---+---+---+
   0   1   2   3   4   5
  -6  -5  -4  -3  -2  -1

So, [0] will get H, [1] will get e and so on. 
```

**Negative index means, start from the end.** Important point to note here is that there is no -0. 0 and -0 are equal, so counting the index backward, start from -1. To get the last character using negative index, see the following code

```python
a = 'Hello world'
a[-1]
# output will be d character
```

**Python strings are immutable**, means that once a string a has been created you can't change it. This also implies that you cannot reassign an index. See example below.

```python
a = 'Hello World'
a[0] = 'h'

# Output
# you will get some error like this
# Traceback (most recent call last):
#   File "<stdin>", line 1, in <module>
# TypeError: 'str' object does not support item assignment
```

**Slicing** allows you to get a subsection of multiple characters of a string, also called slice of string. Syntax for slicing is as follows.

```python
a = 'hello world'
b = a[2:4] # output is llo
b = a[:4]  # output is hell
b = a[4:]	 # output is o world
b = a[2:10:1] # a[start, stop, stride] 
							# output is lowr

'''
'start' 	is index of slice start
'stop' 		is the index where you will go upto slice a string, but
          the character at this index is not included in slice.
'stride'	is the size of the jump you make from start to stop. Or 					in simpler words, it is the number of characters, 							pointer will jump after getting one character.
'''

# Slicing can be used to reverse a string
a = 'Hello World'
b = a[::-1]
# Output is 'dlroW olleH
```

**To get length of a string** we can ```len()``` function.

```python
a = 'Hello World'
print(len(a))
# output is 11 as white space is also counted as a character.
```

**To print a string** we can use builtin ```print()``` function.

```python
name = 'Jahanzeb Sayal'
print(name)
```

**To escape characters in strings**, we can ```\``` symbol.

```python
question = 'What\'s your name'
# We have escaped the ' with \. If we use "", then we do not have to escape '
question = "What's your name"
```

If you do not want to change charters by ```\```, then you can use raw strings. For example if you want to print a file path. You can use raw string instead of escaping ```\``` with ```\```. To tell Python that you are using raw string add ```r``` to the beginning of string.

```python
path = r'C:>Users\Documents' # Notice r before '
# In python REPL, if you type path, you will get 
# 'C:>Users\\Documents', that means Python automatically escaped
# the \. However, with print function you get what you have typed.
print(path)
# Output C:>Users\Documents
```

Some strings can span **multiple lines**, in other languages we have to cocatenate using ```+``` or other concatenation operator, but Python also has a very elegant solution to this problem - ```'''``` - triple quotes. *Triple quotes preserves line breaks. To omit a line break in a tripled quoted string use \ at the end of line*.

```python
m = '''
Line 1
Line 2
Line 3
'''
print(m)
# Output will ne
#
# Line 1
# Line 2
# Line 3
#

# Note the line breaks, on line 8 and 12. To get rid of them use
# \ at the end of line
m = '''\
Line1
Line2
Line3\
'''
# Ouput will now change
# Line1
# Line2
# Line3
```

**To concate strings**, use ```+``` operator. Also two adjacent string literals will automatically be concatenated and it only works with two or more literals, not a combination of a variable and literal.

```python
first = 'Jahanzeb'
last = 'Sayal'
fullName = first + ' ' + last
print(fullName)
# Output Jahanzeb Sayal

'Jahanzeb' + ' ' + 'Sayal'
# Output is Jahanzeb Sayal

fullName = 'Jahan ' 'Zeb'
print(fullName)

# Other than + operator, we can also use * to concatenate string
letter = 'a'
letter * 10
# Output is aaaaaaaaaa
```

**String interpolation** in Python - also called formatted strings.

```python
# Very comprehensive material is available at the  https://pyformat.info
# website on how to format string


firstName = 'Jahan'
lastName = 'Zeb'

# Using .format() methods to format strings
fullName = 'Full name is {} {}'.format(firstName, lastName);
print(fullName)


print('The {q} {b} {f} jumps.'.format(q = 'quick', b = 'brown', f = 'fox'));


# Using f at the start of string, tells Python that this is a formatted
# string, and Python will replace the variable names with values
fullName = f'Full name is {firstName} {lastName}'
print(fullName)


# We can also use formatted string to truncate long strings
someLongString = 'This is a very very very long string'
print('{:.8}'.format(someLongString))
```

## Comments

Python only has single line comments. `#` is used for comment.

```python
# This is python comment
# For multiline comments, we can use multiple single line comments.

fruit_list = ["Apple", "Orange", "Mango", "Banana"]  # List of fruits

# Using # in a string.
str = "This is a string, but # sign here does not make it a comment."
```

## Variables

A variable is a human readable, memoy location where data is saved. You use the variable name to retrieve contents stored at that memory location.

Rules for naming variables in python are

1. Names cannot start with a number.
2. Do not use python keywords for variable names.
3. There cannot be any spaces b/w names and to separate different words use kebab case or camel case convention.
4. Can't use any of these symbols  ```: ' '' , < > /? |( ) ! @ # $ % ^ & ~ - + ``` in simpler words - no special characters.
5. It is considered best practice that variables have lower case names and use _ for separating different words. **(PEP8)**.

```python
a = 20
# we can reassign variables
a = 30 # Now a becomes 30

# Assume we want tp declare a variable to store first name
first_name = 'Jahan'		# good practice
firtName = 'Jahan'			# Considered not good, but no syntax error
```

> **PEP8**
>
> Throughout these notes, you will read the term PEP8, so it's better to clarify it early. [PEP8](https://www.python.org/dev/peps/pep-0008/?) is a style guide for python. In simpler terms, it is a collection of guidelines on how to write Python code. These guidelines are evolving overtime and it's main purpose is to enhance readability of code. PEP stands for Python Enhancement Proposal.

To determine type of a variable, we can use builtin ```type()``` function.

```python
a = 20
type(a)
<class 'int'>
```

Also, it is very important to note that is **NoneType** in python, which is useful when you do not have a value for a variable available at the time.

```Python
b		# Python will throw undefined name error

# To overcome this, we can assign it to None
b = None

# Later, when we have the actual value for b, we can reassign.
```



## Pass Statement

Pass statement is just like NoneType in the sense that, we do not know what to do in a certain function or class (functions and classes ) will be discussed in later chapters. For now, just rememer that, if we want to have a function but do not want to write code for it, we can use `pass` statement.

```python
def some_func:
  pass

class Shape:
	pass
```



## Lists

Lists are ordered sequence types that can hold objects of various different types. Lists use square brackets ```[] and ,``` to contain its elements and separate them. Lists support indexing and slicing. Lists can have other lists as an element and has a variety of useful methods to manipulate strings. Python lists are very similar to Javascript arrays. Indexing and slicing notations are same as strings.

Some useful methods for lists

| Method    | Description                           |
| --------- | ------------------------------------- |
| append()  | adds an element to the end of list    |
| pop()     | removes an element at the end of list |
| sort()    | sort list items in ascending order    |
| reverse() | reverse elements of list              |

```Python
# Capitalize 'c', 'd' & 'e'. This is basically replacing values
letters[2:5] = ['C', 'D', 'E']
print(letters);

# Reset letters list
letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']

# Remove letters 'c', 'd' & 'e'
letters[2:5] = []
print(letters);

# Reset letters list
letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']

# Clear whole list
letters[:] = []
print(letters)

# Reset letters list
letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']

# Reverse list
reversed_letters = letters[::-1]
print(reversed_letters)
```

## Dictionary

Dictionary is an unordered mapping for key-value pairs. Values are retrieved from a dictionary by using a key. Dictionaries are the same as Javascript objects. Syntax for dictionary is as follows

```python
my_dict = {
  'id': 1,
  'name': 'Jahan',
  'age': 39
}

# keys are always string values

# Dictionary methods
my_dict.keys() 		# returns a list of keys of dictionary
my_dict.values()	# returns a list of values of dictionary
```

Values in dictionary cannot be sorted likes lists and also there is no order among different key value pairs. There is another data structure called **ordereddict** that can maintain order in key value pairs.

Dictionary methods

| Method | Description                                 |
| ------ | ------------------------------------------- |
| keys   | Returns a list of keys of dictionary        |
| values | Returns a list of values of dictionary      |
| items  | Returns a list of tuples of key/value pairs |

## Tuples

Tuples are very similar to lists, but they are immutable. Once a value is in tuple, it cannot be reassigned. Tuples use paranthesis ```(1, 2, 3)```. Just like lists, tuples can also have mixed object types. Also supports indexing and slicing.

```Python
my_tuple = ('one', 2, 2, 3, True)

# We can use len() function to find length of tuple
len(my_tuple)

# Tuple methods - Only 2 methods
my_tuple.count(2)			# count number of times, 2 is in tuple
my_tupple.index(2)		# first index of 2 in tuple

```

**Why use tuples whrn we have lists?** Tuples are useful when you are passing around objects, and want to make sure that values cannot be changed or if you want to return multiple values from a function, return a tuple. Also, tuples are very useful in functional programming when immutable data structures are needed.

| Method | Description                                                  |
| ------ | ------------------------------------------------------------ |
| count  | Count the number of occurances an element in tuple           |
| index  | Returns first available index of an element. Python will throw ValueError if |

## SETS

Sets are unordered collection of unique elements. Every element in a set is unique (no duplicates) and must be immutable, means that once an element becomes part of a set, it cannot be changed. Set itself is mutable data structure, means we can add remove elements from set. Sets can be used to perform mathematical set operations like union, intersection, symmetric difference etc.

Sets can be created using ```set``` function or by using literal notation ```{}```.  However if you want to create an empty set, you cannot use literal notation because it will create an empty dictionary, so you have to use ```set()``` function.

```python
my_set = set() # using set() function
my_set.add(1)
my_set.add(2)
my_set.add(2) #since 2 already exists, it will not be added again
my_set
# Ouput {1, 2}

my_set = {1, 2, 3, 3} # using literal notation

# While creating above set, we have added 3 twice. The second
# 3, will be ignored by set.
print(my_set)
# Ouput {1, 2, 3}

# Casting a list to set - this how we can extract unique elements
# from a list
my_list = [1,1,1,1,2,2,2,2,3,3,3,3]	
unique_values_list = set(myList)
print(unique_values_list)
# Output is {1, 2, 3}

```

Set methods

| Method  | Description                                                  |
| ------- | ------------------------------------------------------------ |
| add     | Adds a single element to a set                               |
| update  | Adds multiple elements to a set. Update method can take lists, tuples, strings and other sets as input. |
| discard | Removes an element from a set.                               |
| remove  | Removes an element from a set. Only difference between discard and remove is that remove will throw error, if element is not an element of set |
| clear   | Removes all elements from a set.                             |

Set operations and other set class methods will be discussed in later chapters.

## Booleans

Booleans are true and false values. Booleans are important in decision making, control flow and logic.

```Python
True				# true
False				# false
```

## File I/O

Python can handle text files and binary files. Default mode for file read is text file. In this section we will briefly discuss text file operations.

```python
# Jupyter notebook has a special function to write a text file. 
# NOTE: The following code cannot work in REPL or script. Only
# specific to Jupyter notebook.
%%writefile myfile.text 
Hello this is a text file.
This is line 1.
This is line 2.
```

```open()``` method is used to open, create, append and overwrite to an existing or new file.

```python
open(file_path, mode, optional arguments)

Values for mode are:
'r'       open for reading (default)
'w'       open for writing, truncating the file first
'x'       create a new file and open it for writing
'a'       open for writing, appending to the end of the file if it exists
'b'       binary mode
't'       text mode (default)
'+'       open a disk file for updating (reading and writing)

Default mode is rt (read mode and text file)
'r+'			for reading and writing
'w+'			for writing and reading - overwrites existing file or 
					create a new one.
```

**Open a file, and read it's contents**

```Python
my_file = open('myfile.txt')
# Read the file as one big string and close it.
contents = my_file.read()
my_file.close()
```

**Using ```with``` keyword, will close the file automatically.**

```Python
# We can also read lines of a line in a list. This will make it 
# easier to iterate over file contents. 
# usage of with keyword is also shown below
# readlines() method will read file as a list.
with open('myfile.txt') as my_file:
    contents = my_file.readlines()

contents
```

**Writing to a file**

```python
# Now we will set the second argument of open() to w or w+. This 
# allows us to write new content in file. But all the previous 
# content is deleted.

with open('myfile.txt', 'w+') as my_file:
    my_file.write('This is a new line.')
    my_file.seek(0)
    contents = my_file.readlines()
contents
```

**Appending to a file**

```python
# Appending to a file
# Now we will recreate the same file and using a+ mode, we will 
# append lines.

my_file = open('myfile.txt', 'a+')
my_file.write('This is line four.\n')
my_file.write('This is line five.\n')
my_file.seek(0)
contents = my_file.read()
contents
my_file.close()
print(contents)
```

**Iterating over a file**

```Python
# We will be using a for loop to iterate over myfile.txt
my_file = open('myfile.txt')
for line in my_file:
  print(line)

my_file.close()
```

