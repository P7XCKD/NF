```python
# Importing numpy library
import numpy as np

# Creating 1D Arrays
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

# Display arrays
print("Array a:", a)
print("Array b:", b)

# Basic operations
print("\nAddition (a + b):", a + b)
print("Subtraction (a - b):", a - b)
print("Multiplication (a * b):", a * b)
print("Division (a / b):", a / b)

# Array Properties
print("\nShape of array a:", a.shape)

# Reshaping a 2D array
c = np.array([[1, 2], 
              [3, 4], 
              [5, 6]])

print("\nOriginal 2D Array:\n", c)

reshaped_c = c.reshape(2, 3)
print("Reshaped Array (2 rows, 3 columns):\n", reshaped_c)

# Mathematical operations
print("\nSum of elements in array a:", a.sum())
print("Mean of elements in array a:", a.mean())
print("Max element in array a:", a.max())
print("Min element in array a:", a.min())

# Creating and displaying 3D Array
d = np.array([[[1, 2], [3, 4]],[[5, 6], [7, 8]]])

print("\n3D Array:\n", d)
print("Shape of 3D Array:", d.shape)