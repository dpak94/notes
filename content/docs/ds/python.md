---
type: "docs"
title: Python
draft: false
---

# Python Notes

## Programming Tips

1. Use ''' ''', '' '' or ' ' to write comments in the script.
2. Multiple Assignment in Python : Example : a, b, c, good = 5, True, 'Stranger'
3. The following keywords are reserved in Python :

   `and` `assert` `break` `class` `continue` `def` `del` `elif` `in` `is` `lambda` `not` `or` `else` `except` `exec` `finally` `for` `from` `global` `if` `import` `while` `with` `pass` `print` `raise` `return` `try` `yield`

4. Python has one **unary** operator, **Unary Minus** Operator. If a number is positive, it becomes negative when preceded by a unary minus operator.
5. Python does not support prefix and postfix increment as well as decrement operators.
6. Parentheses can change the order in which an operator is applied. The operator in the parenthesis is applied first even if there is a higher priority operator in the expression.
7. Operators are associated from left to right. This means that operators with same precedence are evaluated in a left to right manner.
8. Always prefer slicing over looping.
9. Python is more forgiving when stepping over the range when slicing than when indexing or looping.

---

## Operators in Python

| Operator                           | Description                                 |
| ---------------------------------- | ------------------------------------------- |
| \*\*                               | Exponentiation                              |
| ~, +, -                            | Complement, unary plus and unary minus      |
| \*, /, %, //                       | Multiply, divide, modulo and floor division |
| +, -                               | Addition and Subtraction                    |
| >>, <<                             | Right and Left bitwise shift                |
| &                                  | Bitwise 'AND'                               |
| ^ \|                               | Bitwise exclusive 'OR' and regular 'AND'    |
| <= < > >=                          | Comparison Operators                        |
| <> == !=                           | Equality Operators                          |
| =, %=, /=, //=, -=, +=, \*=, \*\*= | Assignment Operators                        |
| is, is not                         | Identity Operators                          |
| in, not in                         | Membership Operators                        |
| not, or, and                       | Logical Operators                           |

### Shift Operators

x = 0001 1101

**Shift Left (<<)**
x << 1 gives result 0011 1010

**Shift Right (>>)**
x >> 1 gives result 0000 1110

### Bitwise Operators

1. **Bitwise AND(&)**
   The bit operand is ANDed with the corresponding bit in the second operand. The bitwise AND operator compares each bit of its first operand with the corresponding bit of its second operand. If both bits are 1, the corresponding bit in the result is 1 and 0 otherwise.

`10101010 & 01010101 = 00000000`

2. **Bitwise OR(|)**
   The bit operand is ORed with the corresponding bit in the second operand. The bitwise OR operator compares each bit of its first operand with the corresponding bit of its second operand. If one or both of the bits is 1, the corresponding bit in the result is 1 and 0 otherwise.

`10101010 | 01010101 = 11111111`

3. **Bitwise XOR(^)**
   The bit operand is XORed with the corresponding bit in the second operand. The bitwise XOR operator compares each bit of its first operand with the corresponding bit of its second operand. If one of the bits is 1, the corresponding bit in the result is 1 and 0 otherwise.

`10101010 ^ 01010101 = 11111111`

4. **Bitwise NOT(~)**
   The bitwise NOT or Complementary operator, is a unary operation, which performs logical negation on each bit of the operand. By performing negation of each bit, it actually produces the ones' complement of the given binary value. Bitwise NOT operator sets the bit to 1, if it was initially 0 and sets the bit to 1, if it was initially 0 and sets it to 0, if it was initially 1.

`~10101011 = 01010100`

### Logical Operator

| Command   | Syntax           | Comment                              |
| --------- | ---------------- | ------------------------------------ |
| AND (&&)  | a > b && b > c   | Both expressions must be conditional |
| OR (\|\|) | a > b \|\| b > c | Both expressions must be conditional |
| NOT (!)   | b != a           | Both expressions must be conditional |

**Truth Table**

| A   | B   | A&&B | A   | B   | A\|\|B | A   | !A  |
| --- | --- | :--: | --- | --- | :----: | --- | --- |
| 0   | 0   |  0   | 0   | 0   |   0    | 0   | 1   |
| 0   | 1   |  0   | 0   | 1   |   1    | 1   | 0   |
| 1   | 0   |  0   | 1   | 0   |   1    | -   | -   |
| 1   | 1   |  1   | 1   | 1   |   1    | -   | -   |

---

## Type Conversion Functions

| Function  | Description                                         |
| --------- | --------------------------------------------------- |
| int(x)    | Converts x to an integer                            |
| long(x)   | Converts x to a long integer                        |
| float(x)  | Converts x to a floating point number               |
| str(x)    | Converts x to a string                              |
| tuple(x)  | Converts x to a tuple                               |
| list(x)   | Converts x to a list                                |
| set(x)    | Converts x to a set                                 |
| ord(x)    | Converts a single character to its integer value    |
| oct(x)    | Converts an integer to its octal value              |
| hex(x)    | Converts an integer to a hexadecimal string         |
| chr(x)    | Converts an integer to a character                  |
| unichr(x) | Converts an integer to a unicode character          |
| dict(x)   | Creates a dictionary if x contains a key-value pair |

---

## Map(), Filter() & Reduce() Functions

### map() Function

**map()** function applies a particular function to every element in the list.

**Syntax** : `map(function, sequence)`
**Notes**

- The function must have as many arguments as there are sequences
- Each argument is called with the coresponding item from each sequence (or None if one sequence is shorter then another)

**Demo 1** : A program that adds 2 to every element in the list

```python
def add_2(x):
    x += 2
    return x

num_list = [1,2,3,4,5,6,7,8,8,10]
print("Original list is : ", num_list)
new_list = list(map(add_2,num_list))
print("Modified List is :", new_list)
```

:arrow_double_down:

```
Original list is :  [1, 2, 3, 4, 5, 6, 7, 8, 8, 10]
Modified List is : [3, 4, 5, 6, 7, 8, 9, 10, 10, 12]
```

**Demo 2** : Program where more than one sequence is passed to the map() function.

```python
def add(x,y):
    return x + y
list1 = [1,2,3,4,5]
list2 = [6,7,8,9,10]
list3 = list(map(add,list1,list2))
print("Sum of list1 and list2 is : ",list3)
```

:arrow_double_down:

```
Sum of list1 and list2 is :  [7, 9, 11, 13, 15]
```

### filter() Function

**filter()** function constructs a list from those elements of the list for which a function returns True.

**Syntax** : `filter(function, sequence)`

**Notes**

- If the sequence is a string, Unicode or a Tuple, then the result will be of the same type, otherwise it is always a list.
- Functions that return a Boolean value are called predicates.

**Demo 1** :

```python
def check(x):
    if (x % 2 == 0 or x  % 4 == 0):
        return 1
# Call check for every value between 2 to 21.
evens = list(filter(check,range(2,22)))
print(evens)
```

:arrow_double_down:

```
[2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
```

### reduce() Functions

The **reduce()** function returns a single value generated by calling the function on the first two itemsof the sequence, then on the result and the next item and so on.

**Syntax** : `reduce(function, sequence)`

```python
def add(x,y):
    return x + y

num_list = [1,2,3,4,5]
print('Sum of the values in list =')
print(functools.reduce(add,num_list))
```

:arrow_double_down:

```
Sum of the values in list =
15
```

- **reduce()** function is not imported by default. Import `functools` module to use **reduce** function.
- If there is only one item in the sequence, then its value will be returned.
- If the sequence is empty, then an exception is raised.
- Creating a list in a very extensive range will generate a _MemoryError_ or _OverflowError_.

**Eg.** `list = [5*i for i in range(100*100)`

When this statement is executed, you will get the system overflow problem. Python window will stop responding and you will have to press ==Ctrl+C== to get out of this state.

---

## Random Module

**choice() Attribute**

```python
import random
coin = random(choice(['heads', 'tails']))
print(coin)
```

:arrow_double_down:

```
heads
```

**RANDINT()**

```python
import random
num = random.randint(1,10)
print(num)
```

:arrow_double_down:

```
9
```

**SHUFFLE()**

```python
import random
cards = ['jack','queen','jack']
random.shuffle(cards) # The list order is shuffled.
# print(cards)
for card in cards:
    print(card)
```

:arrow_double_down:

```
queen
jack
jack
```

---

## Iteration Functions

### enumerate function

- When you want to print both index as well as an item in the list, **enumerate()** is used.
- The **enumerate()** function returns an enumerate object which contains the index and value of all the items of the list as tuple.

**Example**

```python
num_list = [1,2,3,4,5]
for index, i in enumerate(num_list):
    print(i, " is at index : ",index)
```

:arrow_double_down:

```
1  is at index :  0
2  is at index :  1
3  is at index :  2
4  is at index :  3
5  is at index :  4
```

### range function

- If you need to print index alone, use **range()** function

**Example**

```python
num_list = [1,2,3,4,5]
for i in range(len(num_list)):
    print("index : ", i)
```

:arrow_double_down:

```
index :  0
index :  1
index :  2
index :  3
index :  4
```

### iter function

- Iterator function is used using the built-in **iter()** function.
- The iterator is used to loop over the elements of the list.
- For this, the iterator fetches the value and then automatically points to the next item in the list when it is used with the **next()** method.

**Example**

```python
num_list = [1,2,3,4,5]
it = iter(num_list)
for i in range(len(num_list)):
    print("Element at index ",i, " is : ",next(it))
```

:arrow_double_down:

```
Element at index  0  is :  1
Element at index  1  is :  2
Element at index  2  is :  3
Element at index  3  is :  4
Element at index  4  is :  5
```

### zip function

- **zip()** is a built-in function that takes two or more sequences and 'zips' them into a list of tuples.
- The tuple thus formed has one element from each sequence.
- If the sequences have different lengths, then the result has the length of the shortest one.

**Example**

```python
tup_1 = (1,3,4,5,6)
list_1 = ['astrisk', True, 45, 3.1456789]
print(list(zip(tup_1, list_1)))
```

:arrow_double_down:

```
[(1, 'astrisk'), (3, True), (4, 45), (5, 3.1456789)]
```

---

## Trivial Functions

### update function

```python
s = set([1, 2, 3, 4])
t = set([6, 7, 8])
s.update(t)
print(s)
```

:arrow_double_down:

```
{1, 2, 3, 4, 6, 7, 8}
```

### ord & chr Functions

```python
str = 'r'
print(ord(str))
str2 = 112
print(chr(str2))
```

:arrow_double_down:

```
114
p
```

### dir Functions

```python
dtr = "Hello"
print(dir(str))
```

:arrow_double_down:

```
['__add__', '__class__', '__contains__', '__delattr__', '__dir__', '__doc__', '__eq__',
'__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__', '__getstate__', '__gt__', '__hash__',
'__init__', '__init_subclass__', '__iter__', '__le__', '__len__', '__lt__', '__mod__', '__mul__', '__ne__', '__new__',
'__reduce__', '__reduce_ex__', '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__',
'__str__', '__subclasshook__', 'capitalize', 'casefold', 'center', 'count', 'encode', 'endswith', 'expandtabs',
'find', 'format', 'format_map', 'index', 'isalnum',
'isalpha', 'isascii', 'isdecimal', 'isdigit', 'isidentifier', 'islower', 'isnumeric', 'isprintable',
'isspace', 'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'maketrans', 'partition', 'removeprefix', 'removesuffix',
'replace', 'rfind', 'rindex', 'rjust', 'rpartition',
'rsplit', 'rstrip', 'split', 'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper', 'zfill']
```

### match case Functions

```python
name = input("What's your name?")
match name:
    case 'Harry'| 'Hermione' | 'Ron':
        print('Gryffindor')
    case 'Draco':
        print('Slytherin')
    case _:
        print('Who?')
```

:arrow_double_down:

```
Input In [5]
    match name:
          ^
SyntaxError: invalid syntax
```

### hash() Function

- Python **hash()** function is a built-in function and returns the hash value of an object if it has one.
- The hash value is an integer which is used to quickly compare dictionary keys while looking at a dictionary.
  `Syntax : hash(obj)`

```python
int_val = 4
str_val = 'GeeksforGeeks'
flt_val = 24.56

print("The integer hash value is : " + str(hash(int_val)))
print("The string hash value is : " + str(hash(str_val)))
print("The float hash value is : " + str(hash(flt_val)))
```

:arrow_double_down:

```
The integer hash value is : 4
The string hash value is : 7234223982570738077
The float hash value is : 1291272085159665688
```

### SYS.ARGV()

```python
import sys
print("Hello I am", sys.argv[1])
```

:arrow_forward:

```
Hello, my name is : ---ip=127.0.0.1
```

**Shuffling a deck of cards.**

```python
import random as rand
import itertools as iter

# Now we form a deck of cards.
deck = list(iter.product(range(1,14), ['Spade', 'Heart', 'Diamond', 'Club']))

# Shuffle the cards.
rand.shuffle(deck)

# Now we draw three cards.
print("Your combination of cards is :")
for i in range(3):
    print(deck[i][0], " of ",deck[i][1])
```

---

## Object Oriented Programming

- Classes define property & behaviour of objects.

- A class is a blue-print while an object is the actual product.

- A class is a collection of objects.

- Defining a class does not create any objects. Objects have to be explicitly created by using syntax :

          `objName = className()`

- A method is a function associated with a class. It defines the operations that the object can execute when it receives a message.

The set of values that the object takes at a particular time is known as the ==state of the object==.

**Data Abstraction** : Refers to the process by which data & functions are defined in such a way that only essential details are revealed & implementation details are hidden.

**Data Encapsulation** : Also called Data Hiding, this is the technique of packing data & functions into a single component (class) to hide implementation details of a class from the user.

**Encapsulation** organizes the data & methosd into a structure that prevents data access by any function (or method) that is not specified in the class. This ensures the integrity of data contained in the object.

### Creating a Class

```python
class Computer():

    def config(self):
        print("i5, 1TB SSD, 32GB RAM")

comp_1 = Computer()

Computer.config(comp_1) # Older syntax of calling objects.
comp_1.config() # Frequently used syntax to call objects.

print(type(comp_1)) # Printing out the object type.
```

:arrow_double_down:

```
i5, 1TB SSD, 32GB RAM
i5, 1TB SSD, 32GB RAM
<class '__main__.Computer'>
```

### \_\_init\_\_ method

==Program I==

```python
class Computer:

    def __init__(self):
        print("The computer specs :")

    def config(self):
        print("i5, 1TB SSD, 32GB RAM")

comp_1 = Computer()

Computer.config(comp_1) # Older syntax of calling objects.
comp_1.config() # Frequently used syntax to call objects.

print(type(comp_1)) # Printing out the object type.
```

:arrow_double_down:

```
The computer specs :
i5, 1TB SSD, 32GB RAM
i5, 1TB SSD, 32GB RAM
<class '__main__.Computer'>
```

==Program II==

```python
class Computer:

    def __init__(self, cpu, ram):
        print("The computer specs :")
        self.cpu = cpu
        self.ram = ram

    def config(self):
        print("Config is ", self.cpu, self.ram)

comp_1 = Computer('i9', 16)
comp_2 = Computer('R6 3600', 32)

comp_1.config()
comp_2.config()
```

:arrow_double_down:

```
The computer specs :
The computer specs :
Config is  i9 16
Config is  R6 3600 32
```

### Constructor

**\_\_init\_\_** is a constructor

==Program==

```python
class Computer:

    def __init__(self):
        self.name = 'Deepak'
        self.age = 28

    def update(self):
        self.age = 20

    def compare(self,other):
        if self.age == other.age:
            return True
        else:
            return False


c1 = Computer()
c2 = Computer()

c1.update()

print(c1.age)

if c1.compare(c2):
    print("They are same.")
else:
    print("They are different.")
```

:arrow_double_down:

```
Output :
20
They are different.
```

### Types of variables in Python - Instance variable & Static Variable

```python
class Car:
    wheels = 4 # Class/Static Variable.

    def __init__(self):
        self.mil = 10      # Instance Variable
        self.com = 'BMW'   # Instance Variable

c1 = Car()
c2 = Car()

c1.mil = 8

print(c1.com, c1.mil, c1.wheels)
print(c2.com, c2.mil, c2.wheels)
```

:arrow_double_down:

```
Output :
BMW 8 4
BMW 10 4
```

### Methods in Python

1. Instance Methods
2. Class Methods
3. Static Methods

```python
class Student:

    school = 'DataMan'

    def __init__(self, m1, m2, m3):
        self.m1 = m1
        self.m2 = m2
        self.m3 = m3

    def avg(self):
        return (self.m1 + self.m2 + self.m3) / 3

    def get_m1(self):
        return self.m1


s1 = Student(34,67,32)
s2 = Student(67,32,12)

print(s1.avg())
```

:arrow_double_down:

```
Output :
44.333333333333336
```

## Tuples

- Tuples are useful for records / structures in other programming languages.
- Unlike lists, Tuples do not support pop(), remove(), append(), insert() etc. methods.
- If a sequence is specified without parentheses, it is treated as tuple by default.

**Advantages of tuple over list :**
A. Tuples can be used as keys for dictionaries but lists cannot be.
B. Tuples are best-suited for storing data that is write-protected.
C. Tuples can store values of differenet datatypes whereas lists can only store values of same datatype.
D. Tuples can be used in place of lists where the number of values is known and small.
E. Multiple values from a function can be returned using a tuple.
F. Tuples are used to format strings.

Tuples are not just immutable but also acts as records with no field names.Each item in the tuple holds the data for one filed and the position of the item gives the meaning.

Benefits of using tuples :
A. **Clarity** : Its clear that the length is never going to change.
B. **Performance** : Occupies less memory than a list of same length.

References in a tuple cannot be changed. But if one of those references points to a mutable object, once that object is changed, then the value of the tuple changes.

Tuples with mutable items can be a source of bugs. An object is only hashable if its value cannot ever change. An unhashable tuple cannot be inserted as a dictionary key, or a set element.

**Parallel Assignment** : Assigning items from an iterable to a tuple of variables.

```python
lax_coord = (33.9426, -118.408)
latitude, longitude = lax_coord
print(latitude, longitude)
```

:arrow_double_down:

```
33.9426 -118.408
```

**Example for Parallel Assignment**

```python
a = 5
b = 10
print(a, b)
a, b = b, a
print(a, b)
```

:arrow_double_down:

```
Output :
5 10
10 5
```

In function calls, **\*** can be used multiple times

```python
def fun(a, b, c, d, *rest):
    return a, b, c, d, rest
```

:arrow_forward:

```
fun(*[1,2], 3, 4, *range(5, 7))
```

---

## Lists

| Action             | Syntax                                 | Explanation                                                                                                                                         |
| ------------------ | -------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| Extend a list      | list1.extend(list2[0:2])               | Adds items 1 to 3 from list2 to list1                                                                                                               |
| Append             | list1.append('item')                   | Appends 'item' to the end of list1                                                                                                                  |
| Insert             | list1.insert(index,element)            | Inserts an element at desired index in list1                                                                                                        |
| Clear              | list1.clear()                          | Clears all elements in the list                                                                                                                     |
| Pop                | list1.pop()                            | Eliminates the last element in the list                                                                                                             |
| index(element)     | list1.index(element)                   | Gives the index number of the position in the list or the first instance position if duplicates exist                                               |
| count(element)     | list1.count(element)                   | Gives out the no. of times an element is repeated in the list.                                                                                      |
| sort()             | list1.sort()                           | Sorts the list in an ascending order. Uses ASCII values to sort the list elements.Num < Upper < Lower                                               |
| reverse()          | list.reverse()                         | Sorts the list in an descending order                                                                                                               |
| copy()             | list2 = list1.copy()                   | Copies elements in list1 to create list2. Editing list1 maked edits in list2 bcoz only reference is copied and not the actual elements in the list. |
| Replace()          | print(list2.replace('elem2','elem1'))  | Replaces elem1 with elem2 in list2                                                                                                                  |
| abs                | abs.var                                | Gives the absolute number of the variable                                                                                                           |
| copy()             | lst_2 = copy.copy(lst_1)               | Copies elements from one list to other with distinct id                                                                                             |
| deepcopy()         | lst_2 = copy.deepcopy(lst_1)           | Copies elements from one list to other with distinct id. Used when the list has lists within it                                                     |
| set()              | set(list_1)                            | Duplicates in a list or tuple can be eliminated by using set() method                                                                               |
| List Comprehension | list = [i**3 for I in range(5)]        | Creating a list of cubes for numbers upto 5                                                                                                         |
| enumerate()        | for index, element in enumerate(list): | Used when both both index and item needed to be printed                                                                                             |
| iterator           | next(list)                             | Used to iterate a list                                                                                                                              |
| sorted()           | list2 = sorted(list1)                  | Returns a sorted list. Original list is not sorted                                                                                                  |
| max(), min()       | x = max(list1)                         | Returns the max/min element in the list                                                                                                             |
| len()              | print(len(list1))                      | Prints the length of a list                                                                                                                         |
| id(list1)          | print(id(list1))                       | Prints the ID of the list                                                                                                                           |

### List Comprehension

`List = [expression for variable in sequence]`

**Examples**

```python
cubes = [i**3 for i in range(1,11)]
z = [(x,y) for x in [10,20,30] for y in [40,50,10] if x!= y]

print(cubes)
print(z)
```

:arrow_forward:

```
[1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]
[(10, 40), (10, 50), (20, 40), (20, 50), (20, 10), (30, 40), (30, 50), (30, 10)]
```

**Caution** Creating a list in a very extensive range will generate a _MemoryError_ or _OverflowError_.

## File Access Modes

| Mode                          | Purpose                                                                                                                                                                                                                                             |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| "r" (read mode)               | Open the file for reading. If the file does not exist, a FileNotFoundError is raised.                                                                                                                                                               |
| "w" (write mode)              | Open the file for writing. If the file exists, its contents are truncated. If the file does not exist in the file path, a new file is created.                                                                                                      |
| "a" (append mode)             | Open the file for writing, but instead of truncating its contents, new data is added to the end of the file. If the file does not exist in the file path, a new file is created.                                                                    |
| "x" (exclusive creation mode) | Open the file for writing, but only if the file does not already exist. If the file exists, a FileExistsError is raised.                                                                                                                            |
| "b" (binary mode)             | Open the file in binary mode. When used in combination with other modes, the "b" mode changes the way data is read from or written to the file. For example, "rb" opens the file in binary read mode, and "wb" opens the file in binary write mode. |
| "t" (Text mode)               | Used in combination with other modes to indicate that the file should be opened in text mode (default)                                                                                                                                              |
| "+" (read and write mode)     | Open the file for reading and writing. The file's pointer is positioned at the starting of the file.                                                                                                                                                |
| 'r+' (Read and write mode)    | Opens the file for reading and writing and the pointer is placed at the beginning of the file. If the file does not exist, an error is raised.                                                                                                      |
| 'a+' (Read and append mode)   | Opens the file for reading and writing and the pointer is placed at the end of the file. If the file does not exist in the file path, it is created.                                                                                                |

| Attribute        | Info                                                |
| ---------------- | --------------------------------------------------- |
| `fileObj.closed` | Returns True if the file is closed                  |
| `fileObj.mode`   | Returns access mode with which file has been opened |
| `fileObj.name`   | Returns name of the file                            |

## Strings

| Command        | Syntax                     | Comment                                                                                                                |
| -------------- | -------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| sep            | `print(objects, sep ="")`  | sep determines how two objects inside the print statement are separated.                                               |
| end            | `print(objects, end ="")`  | end determines if the print statement should move on or continue in the same line.                                     |
| id             | `print(id(object))`        | prints the location id of a variable, list etc.                                                                        |
| len()          | `print(len('string'))`     | prints the no. of characters in the string 'string'.                                                                   |
| \n             | `print("\n")`              | Prints new line.                                                                                                       |
| \t             | `print("\t")`              | Prints tab space                                                                                                       |
| \              | `print("\"") `             | Prints " inside the string by putting \ (backslash/escape char) before it.                                             |
| \f             | `print('Hello\fWorld')`    | Prints form feed character                                                                                             |
| \a             | `print('\a')`              | Rings bell                                                                                                             |
| \o             | `print('\o56')`            | Prints octal value.                                                                                                    |
| \x             | `print('\x87')`            | Prints hex value.                                                                                                      |
| Raw String     | `print(r"string")`         | Prints the string raw,i.e., escapes " and other chars and treats them as normal text.                                  |
| f-string       | `print(f"String")`         | Prints the string with variables inside it.                                                                            |
| lower()        | `spam.lower()`             | Converts string into lower/upper case.                                                                                 |
| Unicode String | `u'Sample Unicode String'` | Specifies that the text is in Unicode format i.e., written in language other than English. Both /u and /U can be used. |

### String Functions

| Command      | Syntax                           | Comment                                                                                                 |
| ------------ | -------------------------------- | ------------------------------------------------------------------------------------------------------- |
| islower()    | spam.islower()                   | Is True if String is lower case.                                                                        |
| isupper()    | spam.isupper()                   | String is upper case.                                                                                   |
| isinteger()  | spam[index No.].isinteger()      | String has integers only.                                                                               |
| isspace()    | spam[index No.].isspace()        | String or string index pos has space.                                                                   |
| endswith()   | string.endswith()                | String or string index ends with char or integer (within the parentheses)                               |
| istitle()    | string.istitle()                 | Checks whether string is title (starts with Capital Letter and every word starts with a Capital Letter) |
| startswith() | string.startswith(pattern)       | Checks if a string starts with a pattern.                                                               |
| ().join()    | (x).join(string items)           | Joins a bunch of strings into one using a joining character.                                            |
| split()      | 'I am a man'.split( )            | Splits a string along the defined character.                                                            |
| rjust()      | 'hello'.rjust(10,'\*')           | Right-justifies by 10 characters.                                                                       |
| rstrip()     | spam.rstrip()                    | Removes white spaces from right of the string. Strip() just removes whitespace.                         |
| replace()    | spam.replace(replaced, replacer) | Replaces a char or a group of chars with other char/group of chars.                                     |

| Symbol   | Purpose                                                                   |
| -------- | ------------------------------------------------------------------------- |
| %c       | Character                                                                 |
| %d or %i | Signed Decimal Integer                                                    |
| %s       | String                                                                    |
| %u       | Unsigned Decimal Integer                                                  |
| %o       | Octal Integer                                                             |
| %x or %X | Hexadecimal Integer (x for lowercase a-f, X for uppercase characters A-F) |
| %E or %e | Exponential Notation                                                      |
| %f       | Floating Point Number                                                     |
| %g or %G | Short Numbers in floating point or exponential notation                   |

### String Notes

1. Python strings are immutable. Once created, they cannot be changed.
2. Can be concatenated using the + operator.
3. A substring of slice is called a slice.
4. Slice operation is used to refer to sub-parts of sequences and strings.
5. Use the dir() with the module name as an argument to see the contents of the string module.
6. Use help() to print details of a particular item in the string module.
7. type() shows the type of an object.
8. Passing ‘\n’ in split() allows us to split the multiline string stored in the string variable.
9. To find the details of a particular function, you can print its documentation using the docstring through **\_\_doc\_\_** attribute.
10. A string can be printed muliple times using print('str' \* n) where n is the no. of times to be printed.

**Stride Example**

Stride refers to the number of characters the string has to move forward after retrieving the first character.
Specifying stride while slicing strings.

```python
str = "Welcome to the world of Python."
print(str[2:10]) # Here default stride is 1.
print(str[2:10:1]) # Same as above.
print(str[2:10:2]) # Stride by 2 i.e., skips every alternate character.
print(str[2:13:4]) # Stride by 4 i.e., skips every 4 character.
```

:arrow_forward:

```
Output :
lcome to
lcome to
loet
le
```

Slice operation with just last positive argument.

```python
str = 'Welcome to the world of Python.'
print(str[::3])
```

:arrow_forward:

```
WceohwloPh.
```

## Dictionaries

```python
actors = {'Michael' : 'Nacho', 'Bob' : 'Saul','Giancarlo':'Fring','Rhea':'Kim'}
for actor in actors:
    print(actor, actors[actor], sep=' : ')
```

The **key** is accessed using **actor** variable from **for** loop, while the values/definitions are accessed using **dict_name[for_var]**. Both are separated using the separator " **:** ".

:arrow_forward:

```
Michael : Nacho
Bob : Saul
Giancarlo : Fring
Rhea : Kim
```

**Note** : When more key value pairs exist, a **list** of dictionaries can be defined and accessed.

```python
actors = [
    {'name':'mando','character':'Nacho','profession':'enforcer'},
    {'name':'rhea','character':'kim','profession':'lawyer'},
    {'name':'bob','character':'jimmy','profession':'lawyer'},
    {'name':'esposito','character':'gustavo','profession':'businessman'}
         ]

print(actors[1]['name']) # Accessing individual character within the dict_list.

for i in actors:
    print(i['name'])
```

:arrow_forward:

```
rhea

mando
rhea
bob
esposito
```

> Another way of accessing dictionary definitions is by using keys.

`Syntax : print(dict_name(key))`

```python
actors = {'Michael' : 'Nacho', 'Bob' : 'Saul','Giancarlo':'Fring','Rhea':'Kim'}
print(actors.get('Michael'))
```

:arrow_forward:

```
Nacho
```

> When populating a dictionary, make sure that there are no keys or values that are duplicate and that every key is unique. If not, then Python keeps only the first key and removes the duplicates.

```python
dict_1 = {1:'one', True:'Boolean'}
dict_2 = {False:'Bool', 0:'Zero'}
dict_3 = {0:'Zero', 1:'one',2:'two',True:'true'}
print(dict_1)
print(dict_2)
print(dict_3)
```

:arrow_forward:

```
{1: 'Boolean'}
{False: 'Zero'}
{0: 'Zero', 1: 'true', 2: 'two'}
```

---

## Running Python Files

**Shebang Line** The first line of all your Python programs should be a shebang line, which tells your
computer that you want Python to execute this program.
The shebang line begins with #!, but the rest depends on your operating system.

On Windows, the shebang line is **#! python3**
On OS X, the shebang line is **#! /usr/bin/env python3**
On Linux, the shebang line is **#! /usr/bin/python3**

**Batch File Code Format**

Place the following in a .bat file :

```
@py.exe E:\Pending Projects\hsquery.py %*
@pause
```

---

## Functions

**Defining a Function**

```python
def display(name, course = 'Gender Studies'):
    print("Name :' + name)
    print("Course :' + course)

display(course='Engineering', name = 'Blaskowicz')
display(name = 'Geralt')
```

:arrow_forward:

```
Name : Blaskowicz
Course : Engineering
Name : Geralt
Course : Gender Studies
```

> When default argument comes before non-default argument(s), it gives **SyntaxError**

```python
def func(m = 500, v):
    return "Force of the body is :" + str(m * v)

func(m = 500, 5)
```

:arrow_forward:

```python
File "Path\program.py", line 2
  def func(m = 500, v):
                    ^
SyntaxError : Non-default argument follows default argument
```

### Lambda Function

1. **Lambda** functions are created using the Lambda keyword. They are a one-line version of functions added to Python due to demand from LISP programmers.
2. **Lambda Functions** have no name.
3. Can take any number of arguments.
4. Can return just one value in the form of expression.
5. Lambda function definition does not have an explicit return statement but contains an expression which is returned.
6. Since they are one-line version of functions, they cannot contain/return multiple expressions.
7. They cannot access variables other than those in their parameter list. They also cannot access global variables.
8. Lambda functions can be passed as variables in other functions.

**Example**

Program written using regular function

```python
def small(a, b):
    if a > b:
        return a
    else:
        return b

small(4,5)
```

:arrow_forward:

```
Output :
5
```

Program written using Lambda Function

```python
summ = lambda x, y: x + y # Smaller number using lambda function.
diff = lambda x, y: x - y

print("Smaller of the numbers is : ", small(summ(-3, 2), diff(-1, 5)))
```

:arrow_forward:

```
Smaller of the numbers is :  -1
```

**More Examples**

Using a Lambda FUnction with an ordinary function

```python
def increment(y):
    return (lambda x: x+1)(y)

a = int(input("Enter the value of a :"))
print("a = ", a)
print("a after incrementing = ",end ="")
b = increment(a)
print(a)
```

:arrow_forward:

```
a =  -5
a after incrementing = -5
```

Program where Lambda Function is used without assigning it to a variable

```python
# Lambda function assigned to a variable.
twice = lambda x: x**2
print(twice(9))
# Lambda function not assigned to any variable twice.
print((lambda x: x**2)(9))
```

:arrow_forward:

```
81
81
```

A Lambda function that receives no arguments but returns an expression

Sum of first 10 natural numbers

```python
x = lambda : sum(range(1,11))
print(x()) # Invokes the lambda expression that accepts no arrguments but returns a value in y
```

:arrow_forward:

```
55
```

### Recursive Function

A ==recursive function== is a function that calls itself to solve a smaller version of its task until a final call is made which does not require a call to itself. Every recursive function has two major cases, which are as follows.

1. Base Case, in which the problem is simple enough to be solved directly without making any further calls to the same function.
2. Recursive Case, in which first the problem at hand is divided into simpler sub-parts. Second, the function calls itself but with sub-parts of the problem obtained in the first step. Third, the result is obtained by combining the solutions of simpler sub-parts.

Thus, we see that recursion utilized the divide and conquer technique of problem solving.
Recursion can also be indirect. That is, one function may call the second function which may call the first function, which again calls the first and so on. This can occur on any number of functions.

Python does not allow more than 1000 recursive calls thereby setting a limit in case of infinite recursion and reports a runtime error message.

Pros and Cons of using recursion :

**Pros**

- Recursive Solutions often tends to be shorter (and simpler) than conventional ones.
- Code is clearer and easier to use.
- Recursion uses the original formula to solve a problem.
- It follows a Divide and Conquer technique to solve problems. In some instances, recursion may be more efficient.

**Cons**

- Aborting a recursive function is sometimes slow and nasty.
- Takes more memory and time to complete as compared to the conventionasl, non-recursional code.
- Difficult to find bugs, especially when using global variables.
- **Factorial of a Number**

```python
def fact(n):
    if (n == 1 or n == 0):
        return 1
    else:
        return n * fact(n-1)

n = int(input("Enter the value of n :"))
print("The factorial of",n,"is",fact(n))
```

**Program to calculate GCD using Recursive Function**

```python
def gcd(a, b):
    rem = a & b
    if rem == 0:
        return b
    else:
        return gcd(b, rem)

a = int(input("Enter the greatest number :"))
b = int(input("Enter the other number : "))

print("GCD of",a," and ",b," is ",gcd(a, b))
```

**Fibonacci Series using recursion**

```python
def fibo(n):
    if (n < 2):
        return 1
    return (fibo(n-1) + fibo(n-2))

n = int(input("Enter the number of terms you want :"))
for i in range(n):
    print("Fibonacci(", i, ") =", fibo(i))
```

:arrow_forward:

```
Enter the number of terms you want : 5
Fibonacci( 0 ) = 1
Fibonacci( 1 ) = 1
Fibonacci( 2 ) = 2
Fibonacci( 3 ) = 3
Fibonacci( 4 ) = 5
```

**Program to calculate the exponent of a given number**

```python
def exporec(x, y):
    if y == 0:
        return 1
    else:
        return (x * exporec(x, y-1))

x = int(input("Enter the index :"))
y = int(input("Enter the exponent :"))
print("Result :", exporec(x, y))
```

:arrow_forward:

```
Result : 25
```

**Program to concatenate two strings using recursion**

```python
def orderedConcat(string1, string2):
    if len(string1 + string2) == 0:
        return ''
    elif (len(string1) > 0 and len(string2) == 0) or (len(string1) == 0 and len(string2) > 0):
        return string1 + string2
    else:
        if string1[0] < string2[0]:
            return string1[0] + orderedConcat(string1[1:], string2)
        elif string2[0] < string1[0]:
            return string2[0] + orderedConcat(string1, string2[1:])
        else: # if they're equal
            return string1[0] + string2[0] + \
                orderedConcat(string1[1:], string2[1:])


def main():
    string1 = "acdrt"
    string2 = "bdet"
    print("First string:", string1)
    print("Second string:", string2)
    print("Result :", end=' ')
    print(orderedConcat("acdrt", "bdet"))

main()
```

:arrow_forward:

```
First string: acdrt
Second string: bdet
Result : abcddertt
```

**Fibonacci Series using Recursive Function**

```python
def fibonacci(n):
    if n < 2:
        return 1
    return (fibonacci(n-1) + fibonacci(n-2))

n = int(input("Enter the no. of items :"))
for i in range(n):
    print("Fibonacci (",i,") = ", fibonacci(i))
```

:arrow_forward:

```
Fibonacci ( 0 ) =  1
Fibonacci ( 1 ) =  1
Fibonacci ( 2 ) =  2
Fibonacci ( 3 ) =  3
Fibonacci ( 4 ) =  5
```

**Program to calculate exp(x, y) using Recursive Function**

```python
def exp_rec(x, y):
    if y == 0:
        return 1
    else:
        return (x * exp_rec(x, y-1))

n = int(input("Enter the base number :"))
print("BASE :",n)
m = int(input("Enter the power number :"))
print("POWER :",m)
print("Result is ",exp_rec(n, m))
```

:arrow_forward:

```
BASE : 5
POWER : 3
Result is  125
```

## Documentation Strings

```python
def func():
    ''' The program just prints the message. It will display Hello World!'''
    print("Hello World!")

print(func.__doc__) # func.__doc__prints the docstring
```

:arrow_forward:

```
The program just prints the message. It will display Hello World!
```

**Notes**
Documentation Strings are the same as that of comments, they explain the code. However, they are more specific and have proper syntax. They are created by putting a multiline string to explain the function.

1. As the first line, it should always be short and concise highlighting the summary of the object’s purpose.
2. Begin with capital and end with a period.
3. Triple quotes to be used to extend the docstrings into multiple lines.
4. Should not specify info like object name or type.
5. In case of multiple lines in the doc string, the second line should be blank, to separate the summary from the rest of the description.
6. The other lines should be one or more paragraphs describing the object’s calling conventions, side effects etc.
7. The first non-blank line after the first line of the documentation string determines the indentation for the entire doc string.
8. Unlike comments, docstrings are retained throughout the runtime of the program. So, users can inspect them during program execution.

## Modules

- When a python file is executed directly, it is considered the main module of that program.
- Main modules are given the special name **main** and provide the basis for a complete Python program.
- The main module may import any number of other modules which in turn may import other modules.But the main module of a Python program cannot be imported into other modules.

**Program to print the sys.path variable**

```python
import sys
print("\n Python Path = \n", sys.path)
```

**Notes**

1. A module must be first be located and loaded into memory before it can be imported and used in the program.
2. Python searches for modules at different locations in the following order: 'CWD\Python310\Lib'
3. If the module is still not found, an error ImportError exception is generated.

### Module Loading & Execution

1. Once the module is located, it is loaded in memory. A compiled version of the module with file extension ==pyc== is generated. Next time, when the module is imprted, this pyc module is loaded to save recompile time.
2. A new recompiled version of the module is again produced whenever the compiled version is out of date(based on the dates when the pyc file was created.)
3. The programmer can force the Python shell to reload and recompile the .py file to generate a new .pyc file by using the `reload()` function.

To import all the identifiers in a module (in this case sys), type from `sys` import . However, you should avoid using the import statement as it confuses the variables in the code with the variables in the modules.

**Program that shows the use of from import statement**

```python
from math import pi
print("Pi =",pi)
```

**Program that shows importing a function within a mosule as another variable**

```python
from math import sqrt as sq
print("Square root of 25 is ",sq(25))
```

:arrow_forward:

```
Pi = 3.141592653589793
Square root of 25 is  5.0
```

### Name of the Module

You can find the name of the module by using the **name** attribute of the module.

**Printing the name of the module**

```python
print("Hello)
print("Name of the module is ", __name__)
```

:arrow_forward:

```
Hello
Name of the module is __main__
```

**Notes**

1. Modules provide all the benefits of modular software design.
2. They provide service and functionality that can be reused in other programs.
3. Even the standard library of Python contains a set of modules.
4. It allows you to logically organize the code so that it becomes easy to understand and use.
5. Modules can only be loaded once, regardless of how many times it is imported.
6. It is customary, but not mandatory, to place the import module code at the beginning of a module.

### Making Your Own Module

Every Python file is a `module`, that is, every file saved as a ==.py== file is a `module`.

The MyModule.py program file is created, which will be imported into the main.py file.

```python
# Develping the MyModule.py
def display():
    print("Hello)
    print("Name of the called module is :", __name__)

str = "Welcome to the world of Python !!!!" # Variable definition.
```

The ==main.py== is now created below

```python
import MyModule
print("MyModule str = ", MyModule.str)
MyModule.display()
print("Name of the calling module is :", __name__)
```

:arrow_forward:

```
MyModule str = Welcome to the world of Python !!!
Hello
Name of the module is :
MyModule
Name of the calling module is :
__main__
```

We have used str and display attributes from `MyModule` module. Both these can also be imported as `from MyModule import str, display`. By convention, modules are named using lowercase letters & optional underscore characters.

### Modules & Namespaces

Created in Module 1 (==module1.py==)

```python
def repeat_x(x):
    return x*2
```

Created in Module 2 (==module2.py==)

```python
def repeat_x(x):
    return x**2
```

On ==main.py==

```python
import module1
import module2

result = repeat_x(10) # Ambiguous reference for identifier repeat_x.
```

- A namespace is a container that provides a named context for identifiers. Two identifiers with the same name in the same scope will lead to a a nameclash.
- Hence, Python does not allow programmers to have two different identifiers with the same name.
- However, in some situations, we need to have same name identifiers.
- Namespaces caters to such situations.
- Namespaces allows programs to avoid potential name clashes by associating each identifier with the namespace from which it originates.
- Module1 & Module2 are imported into the same program. Each module has a function repeat_x(), which return very different result.
- There will be a name clash as it will be difficult to determine which of these two functions should be called.
- Namespaces provide a means for resolving such problems.

### Local, Global & Built-in Namespaces

1. During a program’s main execution, there are three main namespaces that are referenced
   - **built-in namespace**
   - **global namespace**
   - **local namespace**
2. The built-in namespace contains all the built-in functions, constants, etc.
3. The global namespace contains identifiers of the currently executing module.
4. The local namespace contains identifiers defined in the currently executing function.

In this program, we have used function **max()** which is defined in the global namespace of the program. Local identifier, large is defined in a function. So it is accessible.

Program to demonstrate nameclashes in different namespaces.

```python
def max(number):
    print("User defined function max...")
    large = -1
    for i in number:
        if i > large:
            large = i
    return large

number = [9, -1, 4, 2, 7]
print(max(number))
print("Sum of these numbers = ", sum(number)) # Built-in namespace
```

:arrow_forward:

```
User defined function max...
9
Sum of these numbers =  21
```

### Module Private Variables

- If you want some variables or functions in a module to be accessed privately within the module, but not to be accessed from outside it, then you need to declare those identifiers as private.
- In Python, identifiers whose name starts with two underscores (\_\_) are private identifiers. These identifiers can be use d only within the module, but not to be accessed from outside it, then you need to declare those identifiers as private.
- When the module is imported using the `import * from modulename`, all the identifiers of a module’s namespace is imported except the private ones. Thus, private modules become inaccessible from within the importing module.

## Packages

A package is a hierarchical file directory structure that has modules and other packages within it. Like modules, one can easily create a package. Every package is a directory which must have a special file called \_\_init\_\_.py . This file need not contain a single line of code. It is added to indicate that the directory is not a normal one, but a Python Package. 3. You can import the package the same way that you import a module.

### Creating Packages in Python

- To create a package called `MyPackage`, create a directory called ==MyPackage== having the module `MyModule` and the ==\_\_init\_\_.py== file.
- Now, to use the MyModule program, you must import it. This is done in two ways.

`import MyPackage.Mymodule`

or

`from  MyPackage import MyModule`

- The ==\_\_init**.py== is a very important file that also determines which modules the package exports as the API, while keeping other modules internal, by overriding the `**all\_\_` variable as shown below.

```python
__init__.py:
__all__ = [“MyModule”]
```

**Notes**

1. Packages are searched for in the path specified by sys.path.
2. ==\_\_init**.py== file can be an empty file and may also be used to execute initialization code for the package or set the \_\_all** variable.
3. The import statement first checks if the item is defined in the package. If it is unable to find it, an ImportError exception is raised.
4. When importing an item using syntax like Python import item.subitem.subitem, each item except the last must be a package. In no case, it can be a class or function or variable defined in the previous item.
5. Packages have an attribute **path** which is initialized with a list having the name of the dirtectory holding the ==\_\_init**.py== file. The **path\_\_attribute can be modified to change the future searches for modules and sub-packages contained in the package.

**Program that prints absolute value, square root and cube of a number**

```python
import math

def cube(x):
    return x ** 3

a = -100
print("a =", a)

a = abs(a)
print("Square root of ", a, "is", math.sqrt(a))
print("Cube of",a, " is ", cube(a))
```

:arrow_forward:

```
a = -100
Square root of 100 is 10.0
Cube of 100 is 1000000
```
