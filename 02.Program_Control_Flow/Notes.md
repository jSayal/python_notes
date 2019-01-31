# Program control flow

Python scripts are evaluated top down, but this may not be the ideal situation for all programs. Sometimes, we want a certain piece of code to execute if certain conditions are true, keep executing some instructions until some condition becomes false or repeat a line of 100 different lines. Program control flow allows us to execute code conditionally or loop over some piece of code etc.

## Comparison operators

Comparison operators allows us to compare variables and ouput a boolean ```True or False``` result. Table below summarizes the comparsion operator.

| Operator | Description              |
| -------- | ------------------------ |
| ==       | Equality                 |
| !=       | Not equals to            |
| >        | Greater than             |
| <        | Less than                |
| >=       | Greater than or equal to |
| <=       | Less than or equal to    |

Python allows us to chain multiple comparison operators, and this allows us to shorthand large boolean expressions. Chaining always results in ```and``` operations.

```python
1 < 2 < 3
# Output True

# The above statement is same as 
1 < 2 and 2 < 3
```

## logical operators

Logical operators are used to combine True and False values to find out the resultant truth value. Python has three logical operators

| Operator | Description                                                  |
| -------- | ------------------------------------------------------------ |
| and      | True if both operands are true                               |
| or       | True, even if only one operand is true.                      |
| not      | Negates the truth value of a single operand. Truth becomes False and vice versa. |

## IF/elif/else statement

To conditionally execute code, Python only provides ```if elif else``` statements. Like other programming languages, Python does not have a switch statement. ```if elif ```statements can be nested. Python does not have any `switch case` statements.

```python
total_percentage = 88

if total_percentage > 100 or total_percentage < 0:
    print('Total percentage is not correct');
if total_percentage >= 90 <= 100:
    print('Your grade is A+')
elif total_percentage >=80 < 90:
    print('Your grade is A-')
elif total_percentage >= 70 < 80:
    print('Your grade is A')
elif total_percentage >= 60 < 70:
    print('Your grade is B')
else:
    print('Your grade is C')
```

Nested ```if elif``` statements

```python
# Example of nested if elif statements
gender = 'male'
age = 33

if gender == 'male':
    if age >= 18:
        print('You are a male adult')
    else:
        print('Your are a male minor')
elif gender == 'female':
    if age >= 18:
        print('You are a female adult')
    else:
        print('you are a female minor')
else:
    print('Unknown gender and adult status')
```

## Loops

**For loops** allows you to iterate over an iterable. By iterable, Python means any object or data structure, that we can go over and do some operation. For example list is iterable, we can loop over every element of list and perform some operation. Strings, dictionaries, sets, tuples are all iterable.

```python
# Basic example of a for loop
num_list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
for num in num_list:
  print(num)
```

```python
# Print even numbers from 1 to 100
for num in range(1, 101):
    if num % 2 == 0:
        print(num)
```

```Python
# Calculate sum of list
num_list = [2, 3, 4, 5, 6, 7, 8, 9]
sum = 0

for num in num_list:
    sum = += num
    
print(sum)
```

```python
# Iterating over tuple using for loop
tup = (1, 2, 3, 4, 5)
for num in tup:
    print(num)

# Unpacking tuples using for loop
tup_pairs = [('a', 'b'), ('c', 'd'), ('e', 'f')]
for (t1, t2) in tup_pairs:
    print(t1 + t2)
```

```Python
# Iterating over string
msg = 'Hello World'
for c in msg:
    print(c)
```

```Python
# Iterating over dictionary
# Here iterable is just the keys of dictionary
my_dict = {'k1': 1, 'k2': 2, 'k3': 3, 'k4': 4}
for e in my_dict:
    print(e)

# Dictionary view object
print(my_dict.items())

# We can use items() method to get a dictionary view object and
# and unpack the key/value pairs.
for k, v in my_dict.items():
    print(f'Value of {k} is {v}')

# To get true list of keys
print(list(my_dict.keys()))

# To get sorted items in a list created from dictionary
print(sorted(my_dict.values()))
```

**While loop** allows you to loop over certain code, until some condition is true. While loops are preferred over for loops, when we do not know in advance how many iterations are needed.

```Python
# Simple example of a while loop
x = 0
while x < 10:
    print(x)
    x += 1
```

```break & continue ``` statements can be used to interrupt flow of for and while loop. continue will pass over the current iteration of loop and move onto next, while break statement will end the loop.

```Python
# Print all even number b/w 1 and 100
for x in range(1, 100):
    if x % 2 == 0:
        print(x)
    else:
        continue
```

```Python
# Guess number
num = 20;
for x in range(1, 100):
    if x == num:
        print(x)
        break;
```

### Some useful functions to use with loops

#### range(start, stop, step)

Range function generates arithmetic progressions. it used to quickly generate sequence of integers. Default value of step is 1, we can use positive or negative values to have a different step, but **step cannot be 0**. For now without saying too much jargon, just know that range is a generator function and no matter how big the range is, it will only store three values iin memory i.e start, stop and step. Less memory consumption is a big advantage of using range over lists. When range object is executed, it will return a range object, we can use ```list()``` function to get all values.

```python
list(range(1, 10))
# Ouput [1, 2, 3, 4, 5, 6, 7, 8, 9]
```

#### enumerate(iterable)

To keep track of current index in a loop, enumerate function can come in very handy. It takes an iterable (list, string etc.) as input and return a tuple containing index and value of iterable.

```python
for n in enumerate('jahan'):
  print(n)
  
# Output of above 
# (0, 'j')	- tuple (index, value)
# (1, 'a')
# (2, 'h')
# (3, 'a')
# (4, 'n')
```

We can use the list function to generate a list of tuples and then unpack tulpe to get iindex easily.

```python
for i, c in list(enumerate('jahan')):
    print('Letter {} is at index {}'.format(c, i))
    
# Letter j is at index 0
# Letter a is at index 1
# Letter h is at index 2
# Letter a is at index 3
# Letter n is at index 4
```

#### zip(iterable1, ...)

The zip function takes 0 or more iterables and conver them into a list of tuples or more specifically an iterable of tuples.

```python
list_1 = [1, 2, 3, 4, 5]
list_2 = ['Apple', 'Orange', 'Banana', 'Peach', 'Guava']
aggr = list(zip(list_1, list_2))
print(aggr)

# Output
# [(1, 'Apple'), (2, 'Orange'), (3, 'Banana'), (4, 'Peach'), (5, 'Guava')]
```

Once iterables are zipped, we can unzip them by using unpack ```*``` operator. Only iterabble can be unpacked.

```Python
list_1 = [1, 2, 3, 4, 5]
list_2 = ['Apple', 'Orange', 'Banana', 'Peach', 'Guava']
aggr = list(zip(list_1, list_2))
# Unpacking
x, y = zip(*aggr)
print(x)
print(y)

# Output
# (1, 2, 3, 4, 5)
# ('Apple', 'Orange', 'Banana', 'Peach', 'Guava')
```

#### in operator

We can use in operator to quickly found out if an object is in iterable.

```Python
search_term = 1

my_list = [1, 2, 3, 4]
my_tuple = (1, 2, 3, 4, 5)
my_set = {1, 2, 3, 4, 5}
my_dict = {'V1': 1, 'V2': 2, 'V3': 3, 'V4': 4, 'V5': 5}

# For lists
if search_term in my_list:
    print('{} is found in my_list'.format(search_term))
else:
    print('{} is not found in my_list'.format(search_term))
    
# For tuples
if search_term in my_tuple:
    print('{} is found in my_tuple'.format(search_term))
else:
    print('{} is not found in my_tuple'.format(search_term))
    
# For sets
if search_term in my_set:
    print('{} is found in my_set'.format(search_term))
else:
    print('{} is not found in my_set'.format(search_term))
    
# For dictionaries
if search_term in my_dict.values():
    print('{} is found in my_dict'.format(search_term))
else:
    print('{} is not found in my_dict'.format(search_term))
    
# Output
# 1 is found in my_list
# 1 is found in my_tuple
# 1 is found in my_set
# 1 is found in my_dict
```

#### min(iterable) & max(iterable)

```min() and max()``` functions can be used to find min and max of an iteable.

```Python
my_list = [1, 2, 3, 4]
my_tuple = (1, 2, 3, 4, 5)
my_set = {1, 2, 3, 4, 5}
my_dict = {'V1': 1, 'V2': 2, 'V3': 3, 'V4': 4, 'V5': 5}

min(my_list)
max(my_tuple)
min(my_set)
```

#### random

Python has a builtin random module with a wide variety of functions. Here we will only go through shuffle and randint.

```shuffle``` is used to shuffle an iterable, and ```randint``` is used to generate random interger b/w a given range.

```Python
from random import shuffle, randint
my_list = [1, 2, 3, 4, 5]

shuffle(my_list)
print(my_list)

print(randint(10, 40))

# Ouput
# [5, 1, 2, 4, 3]
# 36
```

#### input

```input``` function can be used to take user input.

```Python
num_str = input('Input a number: ')
num = int(num_str)
print(num)
```

## List comprehension

List comprehension is a syntactical sugar on top of for loop in Python that helps to reduce number of lines of code. Important distinction is that list comprehension is an expression, not a block of statements. so you can use it wherever you need an expression e.g. function argument, return statement etc.

```python
# For example we have word 'JaHaNZeB', and we want to conver 
# all characters to lower case
word = 'JaHaNZeB'

# We can use for loop
result = ''
for i, c in enumerate(word):
    result += c.lower()
print(''.join(new_word))

# Using list comprehension
word = ''.join([x.lower() for x in word])
print(word)
```

General syntax for list comprehension is

```
[ expression for target in iterable lc-clauses ]

Every list comprehension statement starts and end with square brackets.
target and iterable are the same as in for statement
lc-clauses is a series or 0 or more clauses, with one of the following forms:
	for target in iterable	# nested for loop
	if expression						# if statement inside for loop
```

Using ```if lc-clause```

```python
results = [23, 67, 78, 21, 90, 76, 24, 55, 66]
# Filter results list for values < 50
results = [x for x in results if x > 50]
results.sort()
print(results)
```

Using ```for target in iterable```. This is equal to nested for loops. 

```python
# Flatten list of lists 
list_of_lists = [[1,2], [3, 4], [5, 6]]
list_of_lists = [x for sub_list in list_of_lists for x in sub_list]
print(list_of_lists)

# For each iteration on list_of_lists, x for sub_list in
# list_of_lists is executed, and output is passed to lc clause 
# that makes the final append to new list
```

Filtering a list

```python
results = [23, 67, 78, 21, 90, 76, 24, 55, 66]
# Filter results list for values < 50
filtered_list = [x for x in results if x > 50]
filtered_list.sort()
print(filtered_list)

results[0] = 200;
print(results[0])
print(filtered_list[0])

# Output 
# [55, 66, 67, 76, 78, 90]
# 200
# 55
```

#### Some other useful builtin functions

##### map function

`map` function can be used to apply a function to all elements of an iterable.

```Python
nums = [1, 2, 3, 4]

# Suppose we want to square all numbers of this nums list
list(map(lambda x : x**2, nums))
```

##### filter function

filter function can be used to filter list, based on some criteria

```python
nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
# Filter all even numbers
list(filter(lambda x: x % 2 != 0, nums))
```

NOTE: lambda is just like an arrow function in ES6.