---
type: "docs"
title: Numpy
draft: true
url: "/docs/ds/numpy/"
---

Documentation Link : [NumPy](https://numpy.org/doc/stable/)

**Installation**

- Conda : `conda install numpy`
- PIP : `pip install numpy`

**Importing Module** `import numpy as np`

| Command                 | Syntax                                              | Description                                                                                                                                                       |
| ----------------------- | --------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ones array              | `a = np.ones(5)`                                    | Creates an array of 5 elements, each having 1 as its value                                                                                                        |
| Zeros Array             | `b = np.zeros(3, dtype = int)`                      | Creates an array of 3 zeros. Specified int datatype                                                                                                               |
| Empty Array             | `c = np.empty(2)`                                   | Creates an array whose initial content is random and depends on the state of the memory. </br> The reason to use empty over zeros (or something similar) is speed |
| Full Array              | `z = np.full((2,2), 9)`                             | Creates an 2x2 array having 9 as each element                                                                                                                     |
| Arange Array            | `d = np.arange(2,6, 1)`                             | The start number, end number and the difference beween the numbers are input                                                                                      |
| Linspace Array          | `e = np.linspace(0, 10, 5)`                         | The start number, the end number and the no. of elements needed are entered                                                                                       |
| Logspace Array          | `f = np.logspace(0, 10, 5)`                         | Start, End and No. of divisions                                                                                                                                   |
| Random Elements Array   | `r = np.random.random((2, 2))`                      | Creates a 2x2 array of random elements                                                                                                                            |
| MxN Array               | `b = np.array([[1, 2, 4], [4, 6, 5], [9, 56, 34]])` |                                                                                                                                                                   |
| Shape of the array      | `d.shape`                                           | Prints shape of the array                                                                                                                                         |
| Dimension of Array      | `d.ndim`                                            | Prints Dimension of the array                                                                                                                                     |
| Size of the array       | `d.size`                                            | Prints Size of the array                                                                                                                                          |
| Object Type             | `print(type(d))`                                    | Prints object type                                                                                                                                                |
| Array Data Type         | `print(d.dtype)`                                    | Prints data type                                                                                                                                                  |
| Forcing Data Type       | `l = np.array([1,2], dtype = np.float64)`           | Forces the datatype from int32 to float64                                                                                                                         |
| Printing Array Elements | `print(d[2])`                                       | Prints elements based on their index                                                                                                                              |

## Array Attributes

### Shape of the array

```python
d = np.arange(6)
d.shape # OP:= (6, )
```

### Dimension of Array

`d.ndim # OP:= 1`

### Size of the array

`d.size # OP:= 6`

### Knowing Object Type & Data Type

```python
print(type(d)) # object Type
print(d.dtype) # Array Data Type
# OP:=
# <class 'numpy.ndarray'>
# int32
```

### Forcing DataType

```python
l = np.array([[1,2],[3,4],[5,8]],dtype = np.float64)
print(l.dtype)
# OP:=
# float64
```

### Printing Elements

```python
print(d[2]) # Prints eleemnts based on their index
# OP:= 2
```

### Array Slicing

```python
x = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [9, 8, 5]
])
i = x[:2, 1:]
print(i)
```

```
Output :
array([[2, 3],
       [5, 6]])
```

### Modifying elements using index position

```python
x = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [9, 8, 5]
])
x[1, 1] = 420
print(x)
```

```
Output :
array([[  1,   2,   3],
       [  4, 420,   6],
       [  9,   8,   5]])
```

### Array Reshape Operations

:memo: Flatten - Flattens the multi-dimensional array into a one-dimiensional array

```python
x = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [9, 8, 5]
])
Z = x.flatten()
print(Z)
```

```
Output :
array([1, 2, 3, 4, 5, 6, 9, 8, 5])
```

### Sorting an array

```python
a = np.array([3, 6, 1, 8, 3, 7, 9, 10, 45, 4])
a = np.sort(a)
print(a)
```

```
Output :
array([ 1,  3,  3,  4,  6,  7,  8,  9, 10, 45])
```

### Reversing an array

```python
x = np.array([
    [1, 2, 3],
    [4, 5, 6],
    [9, 8, 5]
])
q = np.flip(x, axis = 1) # Reversed along columns.
print(q)
```

```
Output :
array([[3, 2, 1],
       [6, 5, 4],
       [5, 8, 9]])
```

### Concatenate Arrays

```python
A = np.arange(5)
B = np.arange(4, 9, 1)
C = np.concatenate((A, B))
print(C)
```

```
Output :
array([0, 1, 2, 3, 4, 4, 5, 6, 7, 8])
```

### Reshaping an array

```python
A = np.arange(6)
print(A)
B = A.reshape(3,2)
print(B)
```

```
Output :
[0 1 2 3 4 5]
array([[0, 1],
       [2, 3],
       [4, 5]])
```

### Using conditional and logical operators to filter values in arrays

```python
a = np.array([
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12]
])
print(a[a < 5]) # Prints all values less than 5
```

```
Output :
[1 2 3 4]
```

```python
cond1 = a > 6
print(a[cond1]) # Prints all values greater than 6
```

```
Output :
[ 7  8  9 10 11 12]
```

```python
c = a[(a > 2) & (a < 11)]
print(c) # Prints all values in between 2 and 11
```

```
Output :
[ 3  4  5  6  7  8  9 10]
```

```python
d = (a > 5) | (a == 5) # Prints True or False wrt logical condition
print(d)
```

```
Output :
[[False False False False]
 [ True  True  True  True]
 [ True  True  True  True]]
```

### Converting 1D array into Multi-Dimensional arrays

#### 1D Axis

The np.newaxis() increases the axis of an array by one

```python
a = np.array([1, 2, 3, 4, 5, 6])
# a.shape
a2 = a[np.newaxis, :]
print(a2.shape)
print(a2)
```

```
Output :
(1, 6)
[[1 2 3 4 5 6]]
```

#### np.copy()

```python
a = np.array([1, 2, 3, 4, 5, 6])
b2 = a.copy()
print("b2 is ",b2)
a[0] = 420
print("a is ",a)
print("b2 is ",b2)
```

```
Output :
b2 is  [1 2 3 4 5 6]
a is  [420   2   3   4   5   6]
b2 is  [1 2 3 4 5 6]
```

#### Random Generator

All you need to do is pass in the number of elements or the a tuple of no. of rows and columns you want it to generate.

```Python
rand = np.random.default_rng()
print(rand.random((4, 2)))
```

```
Output :
[[0.9016336  0.36914537]
 [0.24840371 0.36678628]
 [0.95188125 0.89500768]
 [0.18904333 0.39622381]]
```

#### Unique Values & Indices of Unique Values

```python
a = np.array([11, 11, 12, 13, 14, 15, 16, 17, 12, 13, 11, 14, 18, 19, 20])
unique_values = np.unique(a)
print(unique_values)
```

:atom_symbol:

```
Output :
[11 12 13 14 15 16 17 18 19 20]
```

```python
unique_values, indices_list = np.unique(a, return_counts = True)
print(indices_list)
```

```
Output :
[3 2 2 2 1 1 1 1 1 1]
```

## Arithmetic Operations

| Command                      | Syntax                                             |
| ---------------------------- | -------------------------------------------------- |
| Addition                     | print(x + y)                                       |
| Subtraction                  | print(x - y)                                       |
| Multiplication               | print(x \* y)                                      |
| Division                     | print(x / y)                                       |
| Square Root                  | print(np.sqrt(x))                                  |
| Summation along rows/columns | np.sum(x, axis=1) # axis=0 for column, 1 for row   |
| max() & min()                | print(array.min()) / print(array.max())            |
| mean()                       | print(np.mean(x, axis=0))                          |
| unique items & columns       | print(np.unique(x)) # Prints all the unique values |
