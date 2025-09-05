# NUMPY library
The Numerical Python library **numpy** typically shortened to **np** is a fundamental Python library for scientific computing.
It provides a powerful N-dimensional array object, to hold vectors and matrixes, and many useful tools for linear algebra.

```python
import numpy as np

# Create a 1D array (vector)
array_vector = np.array([1, 2, 3, 4, 5])
print(array_vector)

$ [1 2 3 4 5]
```

```python
# Create a 2D array (matrix)
array_matrix = np.array([[1, 2, 3], [4, 5, 6]])
print(array_matrix)

$ [[1 2 3]   
   [4 5 6]]
```

## Creating a numpy array
Numpy offers several functions to create arrays quickly

```python
# np.array(i): Creates an array from a python list
my_list = [1,2,3,4,5]
my_array = np.array(my_list)
print(my_array)

$ [1 2 3 4 5]

# np.zeros(shape): Creates an array filled with zeros.
my_array = np.zeros((5,5))
print(my_array)

$ [[0. 0. 0. 0. 0.]
   [0. 0. 0. 0. 0.]
   [0. 0. 0. 0. 0.]
   [0. 0. 0. 0. 0.]
   [0. 0. 0. 0. 0.]]

# np.ones(shape): Creates an array filled with ones.
my_array = np.ones(10)
print(my_array)

$ [1. 1. 1. 1. 1. 1. 1. 1. 1. 1.]

# np.arange(start, stop, step): Creates an array with a range of values.
my_array = np.arange(0,10,1)
print(my_array)

$ [0 1 2 3 4 5 6 7 8 9]

# np.linspace(start, stop, num): Creates an array with evenly spaced numbers over a specified interval.
my_array = np.linspace(1,10,6)
print(my_array)

$ [ 1.   2.8  4.6  6.4  8.2 10. ]

```


## Core concepts
- 

