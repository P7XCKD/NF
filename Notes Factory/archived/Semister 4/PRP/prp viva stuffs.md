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
# Qbify + Solvify: Python Viva Questions with Answers

---

### 1. Basics of Python

***Q.1 What is Python and what are its key features?***
#solvify:
- Python is a high-level, interpreted, and general-purpose programming language.
- **Key features**:
  - Easy-to-read syntax
  - Dynamically typed
  - Interpreted language
  - Extensive standard library
  - Supports multiple paradigms: procedural, OOP, and functional
  - Open source and community-supported

***Q.2 What are the different data types in Python?***
#solvify:
- Numbers: `int`, `float`, `complex`
- Sequence: `list`, `tuple`, `range`
- Text: `str`
- Set: `set`, `frozenset`
- Mapping: `dict`
- Boolean: `bool`
- Binary: `bytes`, `bytearray`, `memoryview`
- NoneType: `None`

***Q.3 How is Python interpreted?***
#solvify:
- Python code is executed line by line using an interpreter.
- The interpreter converts Python code into bytecode, which is then executed by the Python Virtual Machine (PVM).

***Q.4 What is PEP8 and why is it important?***
#solvify:
- PEP8 is Python's official style guide.
- It promotes readability and consistency across Python code by specifying naming conventions, indentation, line length, and spacing.

***Q.5 Explain indentation in Python.***
#solvify:
- Indentation defines blocks of code in Python.
- Python uses **whitespace indentation** instead of braces to mark code blocks.
- Consistent indentation is required or it results in a `IndentationError`.

---

### 2. Variables and Data Types

***Q.6 How are variables declared in Python?***
#solvify:
- Variables are declared by simply assigning a value using `=`.
- No explicit declaration or type is required due to dynamic typing.

***Q.7 What is dynamic typing?***
#solvify:
- Python determines the variable type at runtime.
- A variable can be reassigned to different data types during execution.

***Q.8 What is the difference between `is` and `==` in Python?***
#solvify:
- `==` checks if **values** are equal.
- `is` checks if **both variables refer to the same object** in memory.

***Q.9 Explain mutable vs immutable types with examples.***
#solvify:
- **Mutable**: Can be changed after creation (e.g., `list`, `dict`, `set`)
- **Immutable**: Cannot be changed after creation (e.g., `int`, `str`, `tuple`)

---

### 3. Control Flow

***Q.10 Explain the use of if, elif, and else in Python.***
#solvify:
- Used to perform conditional execution.
- `if` checks the first condition, `elif` allows multiple conditions, `else` runs if none are true.

***Q.11 How does a while loop differ from a for loop?***
#solvify:
- `while` loop executes as long as the condition is true.
- `for` loop iterates over sequences like list, tuple, range.

***Q.12 Explain the use of break, continue, and pass statements.***
#solvify:
- `break`: Terminates loop entirely.
- `continue`: Skips to the next iteration.
- `pass`: Placeholder; does nothing.

---

### 4. Functions

***Q.13 How do you define a function in Python?***
#solvify:
- Functions are defined using the `def` keyword followed by function name and parentheses.

***Q.14 What is the difference between *args and **kwargs?***
#solvify:
- `*args`: Accepts variable number of positional arguments.
- `**kwargs`: Accepts variable number of keyword arguments.

***Q.15 What is a lambda function and when is it used?***
#solvify:
- Anonymous one-liner function using `lambda` keyword.
- Used for short operations, especially with `map`, `filter`, and `sorted`.

***Q.16 What is recursion?***
#solvify:
- A function calling itself to solve subproblems.
- Used in problems like factorial, Fibonacci, etc.

---

### 5. Data Structures

***Q.17 Differentiate between list and tuple.***
#solvify:
- **List**: Mutable, allows modifications.
- **Tuple**: Immutable, faster access, more memory efficient.

***Q.18 Differentiate between set and dictionary.***
#solvify:
- **Set**: Collection of unique unordered elements.
- **Dictionary**: Key-value pairs, unordered.

***Q.19 How do you iterate over a dictionary?***
#solvify:
- Using `.items()` to access key-value pairs.
- Can also use `.keys()` or `.values()` for keys and values respectively.

***Q.20 What is list comprehension? Provide an example.***
#solvify:
- Concise way to create lists using `[expression for item in iterable if condition]`.

---

### 6. Object-Oriented Programming

***Q.21 What is a class? What is an object?***
#solvify:
- **Class**: Blueprint for creating objects.
- **Object**: Instance of a class.

***Q.22 Explain the use of the `__init__()` method in Python.***
#solvify:
- It's the constructor method.
- Automatically called when an object is created to initialize attributes.

***Q.23 What is inheritance in Python? How is it implemented?***
#solvify:
- One class (child) derives properties and behavior from another (parent).
- Syntax: `class Child(Parent):`

***Q.24 What is the difference between class method, static method, and instance method?***
#solvify:
- **Instance method**: Takes `self`; works with object’s attributes.
- **Class method**: Takes `cls`; works with class attributes.
- **Static method**: No `self` or `cls`; acts as a regular function inside a class.

***Q.25 What are dunder (magic) methods? Give examples.***
#solvify:
- Special methods with double underscores.
- Used to override built-in behavior.
- Examples: `__init__()`, `__str__()`, `__len__()`, `__add__()`

---

### 7. File Handling

***Q.26 How do you open a file in Python?***
#solvify:
- Using `open(filename, mode)` function.

***Q.27 Explain modes of file opening like r, w, a, rb.***
#solvify:
- `r`: Read
- `w`: Write (overwrite)
- `a`: Append
- `rb`: Read binary

***Q.28 What is the difference between read(), readline(), and readlines()?***
#solvify:
- `read()`: Reads entire file as string.
- `readline()`: Reads one line at a time.
- `readlines()`: Returns list of lines.

***Q.29 Explain the use of `with open(...) as f:` syntax.***
#solvify:
- Context manager that ensures file is automatically closed after use.

---

### 8. Exception Handling

***Q.30 What is exception handling in Python?***
#solvify:
- Mechanism to handle runtime errors to prevent crashing.

***Q.31 How do you use try, except, and finally?***
#solvify:
- `try`: Code that might raise an error.
- `except`: Handles the error.
- `finally`: Executes no matter what.

***Q.32 How do you raise a custom exception in Python?***
#solvify:
- Using `raise` with a custom exception class derived from `Exception`.

---

### 9. Modules and Packages

***Q.33 What is a module in Python?***
#solvify:
- A file containing Python code (functions, variables, classes).
- Allows code reuse.

***Q.34 How do you import a module?***
#solvify:
- Using `import module` or `from module import name`.

***Q.35 Difference between `import module` and `from module import ...`.***
#solvify:
- `import module`: Requires full qualification (`module.name`)
- `from module import name`: Directly uses `name` without prefix.

---

### 10. Python Libraries

***Q.36 What are some commonly used Python libraries?***
#solvify:
- `math` for mathematical operations
- `random` for random numbers
- `datetime` for date/time operations
- `os` for OS-level tasks
- `sys` for system-specific info

***Q.37 How to install external libraries in Python?***
#solvify:
- Using `pip install <library_name>` from command line.

---

### 11. Miscellaneous Concepts

***Q.38 What is list slicing? Provide examples.***
#solvify:
- Extracting sublists using `[start:stop:step]`
- Example: `a[1:4]` gives elements at index 1, 2, 3

***Q.39 What is the difference between global and local variables?***
#solvify:
- **Global**: Declared outside functions; accessible everywhere.
- **Local**: Declared inside functions; accessible only within.

***Q.40 What is the difference between deepcopy and copy?***
#solvify:
- `copy`: Shallow copy; references nested objects.
- `deepcopy`: Recursively copies all nested objects as new.

***Q.41 What is a generator? How is it different from a function?***
#solvify:
- Generator yields values using `yield`.
- Maintains internal state across calls, unlike functions.

---


