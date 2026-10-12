# Python Notes

Complete Python notes, organized for revision and practice.

## Table of Contents

1. [Getting Started](#1-getting-started)
2. [Variables and Data Types](#2-variables-and-data-types)
3. [Strings](#3-strings)
4. [Lists and Tuples](#4-lists-and-tuples)
5. [Dictionaries and Sets](#5-dictionaries-and-sets)
6. [Conditional Expressions](#6-conditional-expressions)
7. [Loops](#7-loops)
8. [Functions and Recursion](#8-functions-and-recursion)
9. [File I/O](#9-file-io)
10. [Object Oriented Programming](#10-object-oriented-programming)
11. [Inheritance and More OOP](#11-inheritance-and-more-oop)
12. [Advanced Python 1](#12-advanced-python-1)
13. [Advanced Python 2](#13-advanced-python-2)
14. [Quick Revision Sheet](#quick-revision-sheet)

## 1. Getting Started

### What Is Programming?

Programming means giving instructions to a computer so it can do tasks, solve problems, and automate work. Just like people use languages such as Hindi or English to communicate, programmers use programming languages to communicate with computers.

### What Is Python?

Python is a beginner-friendly programming language. Its syntax is close to simple English, so it is easier to read and write compared with many other languages.

Python is used in:

- Web development
- Automation
- Artificial intelligence
- Machine learning
- Data science
- Software development

### Features of Python

- Easy to learn and beginner friendly.
- Free and open source.
- Works on Windows, Linux, and Mac.
- Widely used in modern technologies and AI.

### Installing Python

Download Python from [python.org](https://www.python.org), choose the installer for your operating system, and complete the setup.

### First Python Program

Create a file named `hello.py`:

```python
print("hello world")  # print is a function
```

Run it from the terminal:

```bash
python hello.py
```

### Modules

A module is a file containing code that can be imported and reused in your program.

Examples of built-in modules:

- `os`
- `random`

Examples of external modules:

- `flask`
- `tensorflow`

### Pip

`pip` is Python's package manager. It installs external modules.

```bash
pip install flask
```

### Python as a Calculator

You can type `python` in the terminal to open REPL mode.

REPL means:

- Read
- Evaluate
- Print
- Loop

This lets you run Python statements directly, like a calculator.

### Comments

Comments are notes in code that Python does not execute.

Single-line comment:

```python
# This is a single-line comment
```

Multiline comment:

```python
"""
This is an example
of a multiline comment.
"""
```

### Practice Set

- Print the "Twinkle Twinkle Little Star" poem in Python.
- Use REPL to print the table of 5.
- Install an external module and use it for something interesting.
- Print the contents of a directory using the `os` module.
- Add comments to the directory-printing program.

## 2. Variables and Data Types

### Variables

A variable is a name given to a memory location. Think of it as a container that stores a value.

```python
a = 30
b = "Ujjawal"
c = 71.22
```

### Keywords and Identifiers

- Keywords are reserved words in Python.
- Identifiers are names given to variables, functions, classes, and other objects.

### Main Data Types

- `int`: integers, such as `71`
- `float`: decimal numbers, such as `88.44`
- `str`: strings, such as `"Ujjawal"`
- `bool`: `True` or `False`
- `None`: represents no value

Python automatically detects data types:

```python
a = 71       # int
b = 88.44    # float
name = "Ujjawal"  # str
```

### Rules for Variable Names

- Can contain letters, digits, and underscores.
- Can start with a letter or underscore.
- Cannot start with a digit.
- Cannot contain spaces.

Examples:

```python
ujjawal = "name"
one8 = 18
seven_ = 7
_seven = 7
```

### Operators

Common Python operators:

- Arithmetic: `+`, `-`, `*`, `/`
- Assignment: `=`, `+=`, `-=`
- Comparison: `==`, `>`, `>=`, `<`, `!=`
- Logical: `and`, `or`, `not`

### `type()` Function

Use `type()` to check the data type of a value.

```python
a = 31
print(type(a))  # <class 'int'>

b = "31"
print(type(b))  # <class 'str'>
```

### Typecasting

Typecasting means converting one data type to another.

```python
str(31)      # int to string
int("32")    # string to int
float(32)    # int to float
```

### `input()` Function

`input()` takes keyboard input from the user. It always returns a string.

```python
name = input("Enter name: ")
print(name)
```

If the user enters `Ujjawal`, the value stored in `name` is `"Ujjawal"`.

### Practice Set

- Add two numbers.
- Find the remainder when a number is divided by `z`.
- Check the type of a variable assigned using `input()`.
- Use comparison operators to check whether `a = 34` is greater than `b = 80`.
- Find the average of two numbers entered by the user.
- Calculate the square of a number entered by the user.

## 3. Strings

### What Is a String?

A string is a sequence of characters enclosed in quotes.

```python
a = 'Ujjawal'
b = "Ujjawal"
c = '''Ujjawal'''
```

### String Indexing

String indexes start from `0`.

For `"Python"`:

- `P` is at index `0`
- `y` is at index `1`
- `n` is at index `5`

### String Slicing

Slicing extracts part of a string.

```python
name = "Ujjawal"
print(name[0:3])  # Ujj
```

General syntax:

```python
string[start:stop]
```

The `stop` index is not included.

### Slicing with Skip Value

```python
word = "amazing"
print(word[1:6:2])  # mzn
```

More examples:

```python
word = "amazing"
print(word[-7:-1])  # amazin
print(word[:7])     # amazing
print(word[0:])     # amazing
```

### Common String Functions

```python
text = "Ujjawal"

len(text)                 # length of string
text.endswith("wal")      # True
text.count("j")           # 2
text.capitalize()         # Ujjawal
text.find("jaw")          # first index of "jaw"
text.replace("j", "z")    # Uzzawal
```

### Escape Sequence Characters

Escape sequences start with a backslash and represent special characters inside strings.

Examples:

- `\n`: new line
- `\t`: tab
- `\\`: backslash
- `\"`: double quote
- `\'`: single quote

```python
letter = "Dear Ujjawal,\nThis Python course is nice.\nThanks!"
print(letter)
```

### Practice Set

- Display a user-entered name followed by `Good Afternoon`.
- Fill this letter template with name and date:

```python
letter = '''
Dear <|Name|>,
You are selected!
<|Date|>
'''
```

- Detect double spaces in a string.
- Replace double spaces with single spaces.
- Format a letter using escape sequence characters.

## 4. Lists and Tuples

### Lists

A list stores multiple values in one variable. A list can contain values of different data types.

```python
l1 = [7, 9, "Ujjawal"]
```

### List Indexing and Slicing

```python
l1 = [7, 9, "Ujjawal"]

print(l1[0])    # 7
print(l1[1])    # 9
print(l1[2])    # Ujjawal
print(l1[0:2])  # [7, 9]
```

### List Methods

```python
l1 = [1, 8, 7, 2, 21, 15]

l1.sort()        # [1, 2, 7, 8, 15, 21]
l1.reverse()     # reverses the list
l1.append(8)     # adds 8 at the end
l1.insert(3, 8)  # inserts 8 at index 3
l1.pop(2)        # removes and returns element at index 2
l1.remove(21)    # removes value 21
```

### Tuples

A tuple is an immutable collection. Immutable means it cannot be changed after creation.

```python
a = ()        # empty tuple
b = (1,)      # tuple with one element
c = (1, 7, 2) # tuple with multiple elements
```

### Tuple Methods

```python
a = (1, 7, 2, 1)

print(a.count(1))  # number of times 1 appears
print(a.index(7))  # index of first occurrence of 7
```

### Practice Set

- Store seven fruits in a list entered by the user.
- Accept marks of 6 students and display them in sorted order.
- Check that a tuple cannot be changed.
- Sum a list with 4 numbers.
- Count zeros in this tuple:

```python
a = (7, 0, 8, 0, 0, 9)
```

## 5. Dictionaries and Sets

### Dictionaries

A dictionary stores key-value pairs.

```python
a = {
    "key": "value",
    "Ujjawal": "code",
    "marks": "100",
    "list": [1, 2, 9]
}

print(a["key"])   # value
print(a["list"])  # [1, 2, 9]
```

### Properties of Dictionaries

- Mutable.
- Indexed by keys.
- Cannot contain duplicate keys.
- Modern Python preserves insertion order, but you should usually access values by key.

### Dictionary Methods

```python
a = {
    "name": "Ujjawal",
    "from": "india",
    "marks": [92, 98, 96]
}

a.items()                 # key-value pairs
a.keys()                  # all keys
a.update({"friend": "A"}) # add/update values
a.get("name")             # returns value safely
```

Difference between `a["name"]` and `a.get("name")`:

- `a["name"]` gives an error if key is missing.
- `a.get("name")` returns `None` if key is missing.

### Sets

A set is a collection of unique values.

```python
s = set()
s.add(1)
s.add(2)
```

You can also create a set like this:

```python
s = {1, 2}
```

### Properties of Sets

- Unordered.
- Unindexed.
- Cannot contain duplicate values.
- Items inside a set must be hashable, so lists cannot be stored inside sets.

### Set Operations

```python
s = {1, 8, 2, 3}

len(s)                  # 4
s.remove(8)             # removes 8
s.pop()                 # removes an arbitrary item
s.clear()               # empties the set
s.union({8, 11})        # all unique items
s.intersection({8, 11}) # common items only
```

### Practice Set

- Create a dictionary of Hindi words with English translations and allow lookup.
- Input eight numbers and display unique numbers.
- Check whether a set can contain both `18` and `"18"`.
- Find the length of:

```python
s = set()
s.add(20)
s.add(20.0)
s.add("20")
```

- Check the type of:

```python
s = {}
```

- Create an empty dictionary where 4 friends enter their favorite languages.
- Check what happens if two friends have the same name.
- Check what happens if two friends have the same favorite language.
- Check whether you can put a list inside a set:

```python
s = {8, 7, 12, "Ujjawal", [1, 2]}
```

## 6. Conditional Expressions

### Why Conditions Are Needed

Programs often need to make decisions. For example:

- If it is Sunday, play a game.
- If it is sunny, order ice cream.
- If parents allow, go hiking.

In Python, this is done using conditionals.

### `if`, `elif`, and `else`

```python
if condition1:
    print("yes")
elif condition2:
    print("no")
else:
    print("maybe")
```

Example:

```python
a = 22

if a > 9:
    print("greater")
else:
    print("lesser")
```

### Relational Operators

- `==`: equal to
- `>=`: greater than or equal to
- `<=`: less than or equal to
- `>`: greater than
- `<`: less than
- `!=`: not equal to

### Logical Operators

- `and`: true if both conditions are true
- `or`: true if at least one condition is true
- `not`: reverses true/false

### `elif` Ladder

```python
if condition1:
    # code
elif condition2:
    # code
elif condition3:
    # code
else:
    # code
```

Notes:

- You can use any number of `elif` statements.
- The final `else` runs only when all previous conditions fail.
- The ladder stops as soon as one condition is true.

### Practice Set

- Find the greatest of four numbers entered by the user.
- Check whether a student passed. Conditions: total at least 40 percent and at least 33 percent in each subject.
- Detect spam comments containing keywords such as `Make a lot of money`, `buy now`, `subscribe this`, or `click this`.
- Check whether a username contains fewer than 10 characters.
- Check whether a given name is present in a list.
- Calculate grade from marks:

```text
90-100 -> Ex
80-90  -> A
70-80  -> B
60-70  -> C
50-60  -> D
<50    -> F
```

- Check whether a post is talking about `Ujjawal`.

## 7. Loops

### Why Loops Are Needed

Loops repeat a set of statements. For example, printing numbers from 1 to 1000 would be boring to write manually. Loops make repetition easy.

### Types of Loops

- `while` loop
- `for` loop

### `while` Loop

```python
while condition:
    # body of loop
```

The condition is checked first. If it is true, the body runs. This continues until the condition becomes false.

Example:

```python
i = 0
while i < 5:
    print("Ujjawal")
    i = i + 1
```

Be careful: if the condition never becomes false, the loop runs forever.

### `for` Loop

A `for` loop iterates over a sequence such as a list, tuple, string, or range.

```python
l = [1, 7, 8]

for item in l:
    print(item)
```

### `range()` Function

`range()` generates a sequence of numbers.

```python
range(start, stop, step_size)
```

Example:

```python
for i in range(0, 7):
    print(i)  # 0 to 6
```

### `for` Loop with `else`

The `else` block runs when the loop finishes normally.

```python
l = [1, 7, 8]

for item in l:
    print(item)
else:
    print("done")
```

### `break`

`break` exits the loop immediately.

```python
for i in range(0, 80):
    print(i)
    if i == 3:
        break
```

### `continue`

`continue` skips the current iteration and moves to the next one.

```python
for i in range(4):
    print("printing")
    if i == 2:
        continue
    print(i)
```

### `pass`

`pass` means "do nothing". It is useful as a placeholder.

```python
l = [1, 7, 8]

for item in l:
    pass
```

### Practice Set

- Print the multiplication table of a number using a `for` loop.
- Greet names in a list that start with `S`:

```python
l = ["Ujjawal", "Soham", "Sachin", "Rahul"]
```

- Print a multiplication table using a `while` loop.
- Check whether a number is prime.
- Find the sum of first `n` natural numbers using a `while` loop.
- Calculate factorial using a `for` loop.
- Print star patterns for `n = 3`:

```text
*
***
*****
```

```text
*
**
***
```

```text
* * *
*   *
* * *
```

- Print a multiplication table of `n` in reverse order.

## 8. Functions and Recursion

### Functions

A function is a group of statements that performs a specific task. Functions make programs easier to organize and reuse.

```python
def func1():
    print("hello")
```

### Function Call

To run a function, call it by its name followed by parentheses.

```python
func1()
```

### Function Definition

The function definition contains the actual instructions that run when the function is called.

### Types of Functions

- Built-in functions: already available in Python, such as `len()`, `print()`, and `range()`.
- User-defined functions: written by the programmer.

### Functions with Arguments

Functions can accept values.

```python
def greet(name):
    gr = "hello " + name
    return gr

a = greet("Ujjawal")
print(a)
```

### Default Parameter Value

Default values are used when no argument is passed.

```python
def greet(name="stranger"):
    print("hello " + name)

greet()
greet("Ujjawal")
```

### Recursion

Recursion means a function calls itself.

It is useful when a problem can be broken into smaller versions of the same problem.

Factorial example:

```python
def factorial(n):
    if n == 0 or n == 1:
        return 1
    return n * factorial(n - 1)
```

Be careful with recursion. Every recursive function needs a stopping condition, otherwise it can call itself forever.

### Practice Set

- Find the greatest of three numbers using a function.
- Convert Celsius to Fahrenheit using a function.
- Prevent `print()` from printing a new line at the end.
- Use recursion to calculate the sum of first `n` natural numbers.
- Print this pattern using a function:

```text
***
**
*
```

- Convert inches to centimeters.
- Remove a word from a list and strip spaces at the same time.
- Print the multiplication table of a number using a function.

## 9. File I/O

### Why Files Are Needed

RAM is temporary. When a program ends, data stored in memory is lost. Files let us store data permanently.

A Python program can:

- Read from files.
- Write to files.
- Update files.
- Work with text and binary data.

### Types of Files

- Text files: `.txt`, `.c`, `.py`, etc.
- Binary files: `.jpg`, `.dat`, etc.

### Opening a File

Python uses `open()` to open files.

```python
open("this.txt", "r")
```

Syntax:

```python
open("filename", "mode")
```

### Reading a File

```python
f = open("this.txt", "r")
text = f.read()
print(text)
f.close()
```

### Reading Line by Line

```python
f.readline()
```

This reads one full line at a time.

### File Opening Modes

- `r`: read
- `w`: write
- `a`: append
- `+`: update
- `rb`: read binary
- `rt`: read text

### Writing to a File

```python
f = open("this.txt", "w")
f.write("this is nice")
f.close()
```

### `with` Statement

The `with` statement automatically closes the file.

```python
with open("this.txt", "r") as f:
    text = f.read()
    print(text)
```

Use `with` whenever possible. It is cleaner and safer.

### Practice Set

- Read `poems.txt` and check whether it contains `twinkle`.
- Update `Hi-score.txt` when a game score beats the previous high score.
- Generate multiplication tables from 2 to 20 and save them in separate files.
- Replace the word `Donkey` with `#####` in a file.
- Repeat the censoring program for a list of words.
- Mine a log file and check whether it contains `python`.
- Find the line number where `python` appears in the log file.
- Copy a text file named `this.txt`.
- Check whether two files have identical content.
- Wipe out the content of a file using Python.
- Rename a file to `renamed_by_python.txt`.

## 10. Object Oriented Programming

### What Is OOP?

Object Oriented Programming solves problems by creating objects. It focuses on reusable code and follows the DRY principle: Do Not Repeat Yourself.

### Class

A class is a blueprint for creating objects.

```python
class Employee:
    # methods and variables
    pass
```

Class names are commonly written in PascalCase.

### Object

An object is an instance of a class. A class is like a template; an object is an actual thing created from that template.

Objects can use methods without needing to know internal details. This is related to:

- Abstraction
- Encapsulation

### Modeling a Problem in OOP

A simple way to map real-world problems:

- Noun -> Class -> `Employee`
- Adjective -> Attributes -> `name`, `age`, `salary`
- Verb -> Methods -> `getSalary()`, `increment()`

### Class Attributes

Class attributes belong to the class.

```python
class Employee:
    company = "Google"

ujjawal = Employee()
print(ujjawal.company)

Employee.company = "YouTube"
```

### Instance Attributes

Instance attributes belong to a specific object.

```python
ujjawal.name = "Ujjawal"
ujjawal.salary = "30k"
```

Instance attributes take priority over class attributes when both have the same name.

When Python looks for `ujjawal.attribute`, it checks:

1. Is the attribute present in the object?
2. Is the attribute present in the class?

### `self` Parameter

`self` refers to the current object. Python automatically passes it when a method is called from an object.

```python
ujjawal.getSalary()
```

This is equivalent to:

```python
Employee.getSalary(ujjawal)
```

Example:

```python
class Employee:
    company = "Google"

    def getSalary(self):
        print("Salary is not there")
```

### Static Method

A static method does not use `self`.

```python
class Employee:
    @staticmethod
    def greet():
        print("Hello user")
```

### `__init__()` Constructor

`__init__()` runs automatically when an object is created.

```python
class Employee:
    def __init__(self, name):
        self.name = name

    def getSalary(self):
        pass

ujjawal = Employee("Ujjawal")
```

### Practice Set

- Create a `Programmer` class to store information about programmers working at Microsoft.
- Create a `Calculator` class that finds square, cube, and square root.
- Create a class with class attribute `a`; create an object and set `object.a = 0`. Check whether the class attribute changes.
- Add a static method to greet the user with hello.
- Create a `Train` class with methods to book a ticket, get seat status, and get fare information for Indian Railways.
- Change the `self` parameter name to something else, such as `slf` or `ujjawal`, and observe what happens.

## 11. Inheritance and More OOP

### Inheritance

Inheritance creates a new class from an existing class.

```python
class Employee:
    # base class
    pass

class Programmer(Employee):
    # derived class
    pass
```

The child class can use methods and attributes of the parent class. It can also add new features or override existing ones.

### Types of Inheritance

- Single inheritance
- Multiple inheritance
- Multilevel inheritance

### Single Inheritance

Single inheritance means one child class inherits from one parent class.

```python
class Base:
    pass

class Derived(Base):
    pass
```

### Multiple Inheritance

Multiple inheritance means one child class inherits from more than one parent class.

```python
class Parent1:
    pass

class Parent2:
    pass

class Child(Parent1, Parent2):
    pass
```

### Multilevel Inheritance

Multilevel inheritance means a child class becomes the parent of another class.

```python
class Parent:
    pass

class Child1(Parent):
    pass

class Child2(Child1):
    pass
```

### `super()` Method

`super()` accesses methods of the parent class.

```python
super().__init__()
```

This is commonly used to call the parent class constructor.

### Class Method

A class method is bound to the class, not the object.

```python
class Employee:
    @classmethod
    def show(cls):
        print(cls)
```

### `@property`

`@property` lets you use a method like an attribute.

```python
class Employee:
    @property
    def name(self):
        return self.ename
```

Now `e.name` internally calls the `name()` method.

### Getter and Setter

The method with `@property` is the getter. A setter updates the value.

```python
class Employee:
    @property
    def name(self):
        return self.ename

    @name.setter
    def name(self, value):
        self.ename = value
```

### Operator Overloading

Operators can be overloaded using dunder methods.

```python
p1 + p2   # p1.__add__(p2)
p1 - p2   # p1.__sub__(p2)
p1 * p2   # p1.__mul__(p2)
p1 / p2   # p1.__truediv__(p2)
p1 // p2  # p1.__floordiv__(p2)
```

Other useful dunder methods:

```python
__str__()  # controls str(obj)
__len__()  # controls len(obj)
```

### Practice Set

- Create a 2-D vector class and use it to create a 3-D vector class.
- Create `Pets` from `Animals`, then create `Dog` from `Pets`; add a `bark` method.
- Create an `Employee` class with salary and increment properties. Add a `salaryAfterIncrement` property and setter.
- Create a `Complex` class and overload `+` and `*`.
- Create a vector class for `n` dimensions. Overload `+` and `*` for sum and dot product.
- Write `__str__()` to print a 3-D vector like:

```text
7i + 8j + 10k
```

- Override `__len__()` to display vector dimension.

## 12. Advanced Python 1

### Walrus Operator

The walrus operator `:=` assigns a value inside an expression. It was introduced in Python 3.8.

```python
if (n := len([1, 2, 3, 4, 5])) > 3:
    print(f"List is too long ({n} elements, expected <= 3)")
```

Here, `n` gets the list length and is used in the same condition.

### Type Definitions

Type hints help describe what kind of value a variable or function uses.

```python
age: int = 25

def greeting(name: str) -> str:
    return f"Hello, {name}!"
```

Type hints do not force types at runtime by default, but they make code easier to understand and help editors catch mistakes.

### Advanced Type Hints

The `typing` module provides types such as `List`, `Tuple`, `Dict`, and `Union`.

```python
from typing import List, Tuple, Dict, Union

numbers: List[int] = [1, 2, 3, 4, 5]
person: Tuple[str, int] = ("Alice", 30)
scores: Dict[str, int] = {"Alice": 90, "Bob": 85}
identifier: Union[int, str] = "ID123"
```

### Match Case

Python 3.10 introduced `match`, which is similar to switch-case in other languages.

```python
def http_status(status):
    match status:
        case 200:
            return "OK"
        case 404:
            return "Not Found"
        case 500:
            return "Internal Server Error"
        case _:
            return "Unknown status"
```

### Dictionary Merge and Update Operators

Python supports `|` and `|=` for dictionaries.

```python
dict1 = {"a": 1, "b": 2}
dict2 = {"b": 3, "c": 4}

merged = dict1 | dict2
print(merged)  # {'a': 1, 'b': 3, 'c': 4}

dict1 |= dict2
```

### Multiple Context Managers

You can open multiple files in one `with` block.

```python
with (
    open("file1.txt") as f1,
    open("file2.txt") as f2
):
    pass
```

### Exception Handling

Exceptions are errors that occur while a program is running.

```python
try:
    print(10 / 0)
except Exception as e:
    print(e)
```

Specific exceptions:

```python
try:
    # risky code
    pass
except ZeroDivisionError:
    # division by zero
    pass
except TypeError:
    # wrong type
    pass
except:
    # all other exceptions
    pass
```

### Raising Exceptions

Use `raise` to create your own error.

```python
age = -5

if age < 0:
    raise ValueError("Age cannot be negative")
```

### `try` with `else`

The `else` block runs only if the `try` block succeeds.

```python
try:
    print("success")
except:
    print("error")
else:
    print("try was successful")
```

### `try` with `finally`

The `finally` block always runs, whether an error happens or not.

```python
try:
    print("try")
except:
    print("except")
finally:
    print("always runs")
```

### `if __name__ == "__main__"`

`__name__` tells whether a file is being run directly or imported.

```python
if __name__ == "__main__":
    print("Running directly")
```

This is useful when a file should behave differently when imported as a module.

### `global` Keyword

`global` lets a function modify a variable outside its local scope.

```python
x = 10

def change():
    global x
    x = 20
```

Use `global` carefully. Too much global state can make programs harder to debug.

### `enumerate()`

`enumerate()` adds a counter while looping over an iterable.

```python
list1 = ["Ujjawal", "Rohan", "Shubham"]

for i, item in enumerate(list1):
    print(i, item)
```

### List Comprehensions

List comprehension is a short way to create a list from another iterable.

```python
list1 = [1, 7, 12, 11, 22]
list2 = [item for item in list1 if item > 8]
```

### Practice Set

- Open `1.txt`, `2.txt`, and `3.txt`; if a file is missing, print a message without crashing.
- Print the third, fifth, and seventh elements from a list using `enumerate()`.
- Create a multiplication table list from a user-entered number using list comprehension.
- Display `a / b`; if `b = 0`, handle `ZeroDivisionError` and display `infinite`.
- Store the multiplication table generated above in `Tables.txt`.

## 13. Advanced Python 2

### Virtual Environment

A virtual environment is an isolated Python environment. It behaves like a separate Python installation, so project packages do not disturb the system Python or other projects.

Install virtualenv:

```bash
pip install virtualenv
```

Create an environment:

```bash
virtualenv myprojectenv
```

Then activate it using the activation command for your operating system.

### `pip freeze`

`pip freeze` lists installed packages with versions.

```bash
pip freeze > requirements.txt
```

This creates `requirements.txt`. Another user can recreate the same environment:

```bash
pip install -r requirements.txt
```

### Lambda Functions

A lambda is a small anonymous function written in one expression.

```python
square = lambda x: x * x
print(square(6))

total = lambda a, b, c: a + b + c
print(total(1, 2, 3))
```

Use lambda for small, simple functions. For complex logic, use `def`.

### `join()` Method

`join()` creates a string from iterable items.

```python
l = ["apple", "mango", "banana"]
result = ", and, ".join(l)
print(result)
```

### `format()` Method

`format()` inserts values into a string.

```python
"{} is a good {}".format("Ujjawal", "boy")
"{1} is a good {0}".format("Ujjawal", "boy")
```

### `map()`

`map()` applies a function to every item in an iterable.

```python
numbers = [1, 2, 3]
squares = list(map(lambda x: x * x, numbers))
print(squares)
```

### `filter()`

`filter()` keeps only the items for which a function returns `True`.

```python
numbers = [1, 2, 3, 4, 5]
even = list(filter(lambda x: x % 2 == 0, numbers))
print(even)
```

### `reduce()`

`reduce()` applies a rolling computation to a sequence.

```python
from functools import reduce

numbers = [1, 2, 3, 4]
total = reduce(lambda a, b: a + b, numbers)
print(total)  # 10
```

For `[1, 2, 3, 4]`, addition works like:

```text
1 + 2 = 3
3 + 3 = 6
6 + 4 = 10
```

### Practice Set

- Create two virtual environments. Install packages in the first and recreate a similar second environment.
- Input name, marks, and phone number of a student and format it like:

```text
The name of the student is Ujjawal, his marks are 72 and phone number is 99999888
```

- Convert a multiplication table of 7 into a vertical string:

```text
7
14
21
...
```

- Filter numbers divisible by 5.
- Find the maximum number in a list using `reduce()`.
- Run `pip freeze` for the system interpreter and create a similar virtual environment.
- Explore Flask and create a web server using Flask and Python.

## Quick Revision Sheet

### Must-Know Basics

- Python files usually end with `.py`.
- `print()` displays output.
- `input()` takes user input as a string.
- Variables store values.
- `type()` checks data type.
- Typecasting converts values between types.
- Comments explain code and are ignored by Python.

### Core Data Structures

- String: text data.
- List: mutable ordered collection.
- Tuple: immutable ordered collection.
- Dictionary: key-value pairs.
- Set: unique values.

### Core Control Flow

- `if`, `elif`, `else` make decisions.
- `for` loops iterate over sequences.
- `while` loops repeat while a condition is true.
- `break` exits a loop.
- `continue` skips an iteration.
- `pass` does nothing.

### Core Functions and OOP

- Functions group reusable logic.
- Recursion is a function calling itself.
- Classes are blueprints.
- Objects are instances.
- `self` refers to the current object.
- Constructors initialize objects.
- Inheritance reuses and extends classes.

### Useful Advanced Tools

- `with` handles files safely.
- Exceptions prevent programs from crashing unexpectedly.
- Type hints improve readability.
- `enumerate()` gives index and item together.
- List comprehensions create lists neatly.
- Virtual environments isolate dependencies.
- `pip freeze` records installed packages.
- `lambda`, `map`, `filter`, and `reduce` support functional-style programming.

