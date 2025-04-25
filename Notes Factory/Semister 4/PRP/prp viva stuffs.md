## Python Viva Questions and Answers

---

### Q1. What is Python and what are its key features?
- Python is a high-level, interpreted, general-purpose programming language.
- It emphasizes code readability and supports multiple programming paradigms.
- **Key features:**
  - Easy-to-read syntax
  - Dynamically typed
  - Interpreted language
  - Vast standard library
  - Supports OOP, functional, and procedural programming
  - Cross-platform compatibility

---

### Q2. Explain dynamic typing in Python.
- Python is dynamically typed, meaning you don’t have to declare the data type of a variable explicitly.
- The type is determined at runtime based on the value assigned.
- This adds flexibility but may lead to runtime errors if not handled properly.

---

### Q3. What are the built-in data types in Python?
- Numeric: `int`, `float`, `complex`
- Sequence: `list`, `tuple`, `range`
- Text: `str`
- Set types: `set`, `frozenset`
- Mapping: `dict`
- Boolean: `bool`
- Binary: `bytes`, `bytearray`, `memoryview`
- NoneType: `None`

---

### Q4. Explain the difference between `is` and `==` in Python.
- `==` checks **value equality** (i.e., whether the values of two variables are the same).
- `is` checks **identity** (i.e., whether two variables point to the same object in memory).

---

### Q5. What is indentation and why is it important in Python?
- Indentation refers to the whitespace at the beginning of a line.
- Python uses indentation to define the scope of loops, functions, conditionals, etc.
- Unlike other languages that use braces, Python enforces indentation to avoid ambiguity and improve readability.

---

### Q6. What are dunder methods? Explain with examples.
- Dunder (double underscore) methods, also called **magic methods**, start and end with double underscores (e.g., `__init__`, `__str__`, `__len__`).
- They allow customization of class behavior and operator overloading.
- Examples:
  - `__init__`: Initializes a class object.
  - `__str__`: Defines the string representation.
  - `__add__`: Overrides the `+` operator for objects.

---

### Q7. What is a constructor in Python? How is it defined?
- A constructor is a special method used to initialize objects in a class.
- In Python, it is defined using the `__init__` method.
- It is automatically called when a new object is created.
- It sets up initial values of object attributes.

---

### Q8. What are regular expressions in Python? How are they used?
- Regular expressions (regex) are used to match patterns in strings.
- Python provides the `re` module for regex operations.
- Common uses include searching, replacing, and validating text patterns (e.g., email, phone numbers).

---

### Q9. Define a class in Python. How is it different from an object?
- A class is a blueprint for creating objects. It defines attributes and behaviors (methods).
- An object is an instance of a class.
- The class defines the structure, while the object is a specific entity based on that structure.

---

### Q10. How are exceptions handled in Python?
- Exceptions are handled using `try`, `except`, `else`, and `finally` blocks.
- The `try` block contains code that might raise an exception.
- The `except` block handles specific or generic exceptions.
- `finally` block is used for cleanup code that must execute regardless of an exception.

---

### Q11. Explain the difference between a list, tuple, and set.
- **List**: Ordered, mutable, allows duplicate elements.
- **Tuple**: Ordered, immutable, allows duplicates.
- **Set**: Unordered, mutable, does not allow duplicate elements.

---

### Q12. What is the difference between a class method, static method, and instance method?
- **Instance Method**: Operates on instance data; takes `self` as the first argument.
- **Class Method**: Operates on class data; takes `cls` as the first argument. Defined with `@classmethod`.
- **Static Method**: Doesn’t take `self` or `cls`; behaves like a regular function inside a class. Defined with `@staticmethod`.

---

### Q13. What is the difference between deep copy and shallow copy?
- **Shallow copy**: Creates a new object but references nested objects from the original.
- **Deep copy**: Recursively copies all nested objects, resulting in a fully independent copy.

---

### Q14. What are global and local variables?
- **Local Variable**: Declared inside a function and accessible only within that function.
- **Global Variable**: Declared outside functions and accessible across the entire script.
- To modify a global variable inside a function, use the `global` keyword.

---

### Q15. What is list comprehension?
- A concise way to create lists using a single line of code.
- Syntax: `[expression for item in iterable if condition]`
- It is faster and more readable than using loops.
***
