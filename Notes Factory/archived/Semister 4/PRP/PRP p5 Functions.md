```python
# Function exercise

# Factorial Calculator
# Write a function factorial(n: int) -> int that calculates the factorial of a given number n. Implement input validation to ensure n is non-negative.
def factorial(n: int):
    if n < 0:
        raise ValueError("Input must be non-negative.")
    elif n == 0:
        return 1
    else:
        return n * factorial(n-1)
# Palindrome Checker
# Create a function is_palindrome(s: str) -> bool that checks if a given string s is a palindrome. Ignore spaces and case sensitivity.
def is_palindromne(s: str):
    s = s.lower().replace(" ", "")
    return s == s[::-1]
# Prime Number Checker
# Write a function is_prime(n: int) -> bool that determines if a number n is prime. Implement another function list_primes(limit: int) -> list that returns all prime numbers up to limit.
def is_prime(n: int):
    if n <= 1:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True
# Greatest Common Divisor (GCD)
# Implement a function gcd(a: int, b: int) -> int that finds the greatest common divisor of two numbers using the Euclidean algorithm.
def gcd(a: int,b: int):
    while b != 0:
        a, b = b, a % b
    return a
# Fibonacci Sequence Generator
# Write a function fibonacci(n: int) -> list that returns a list containing the first n Fibonacci numbers.
def fibonacci(n: int):
    fib_sequence = [0, 1]
    for i in range(2, n):
        fib_sequence.append(fib_sequence[i-1] + fib_sequence[i-2])
    return fib_sequence

# Armstrong Number Checker
# Implement a function is_armstrong(n: int) -> bool that checks whether a number n is an Armstrong number (sum of its digits each raised to the power of the number of digits equals the number itself).
def is_armstrong(n:int):
    digits = str(n)
    num_digits = len(digits)
    total = 0
    for digit in digits:
        total += int(digit) ** num_digits
    return total == n

# Temperature Converter
# Create a function convert_temperature(value: float, scale: str) -> float that converts temperatures between Celsius, Fahrenheit, and Kelvin.
def convert_temperature(value: float,scale: str):
    if scale == "C":
        return value
    elif scale == "F":
        return (value * 9/5) + 32
    elif scale == "K":
        return value + 273.15
    else:
        raise ValueError("Invalid temperature scale.")

# Word Frequency Counter
# Implement a function word_count(sentence: str) -> dict that takes a sentence and returns a dictionary with each unique word as a key and its frequency as the value.
def word_count(sentence: str) -> dict:
    words = sentence.split()
    word_freq = {}
    for word in words:
        if word in word_freq:
            word_freq[word] += 1
        else:
            word_freq[word] = 1
    return word_freq

# Simple Calculator
# Create a function calculate(a: float, b: float, operator: str) -> float that performs basic arithmetic operations (+, -, *, /). Handle division by zero properly.

# Count Vowels and Consonants
# Write a function count_vowels_consonants(s: str) -> tuple that returns the number of vowels and consonants in a given string s.

# Sorting Algorithm (Bubble Sort)
# Implement a function bubble_sort(arr: list) -> list that sorts a given list of numbers using the Bubble Sort algorithm.

# Reverse a String
# Write a function reverse_string(s: str) -> str that reverses a given string without using built-in functions like [::-1].

# Check Leap Year
# Create a function is_leap_year(year: int) -> bool that determines if a given year is a leap year based on leap year rules.

# Sum of Digits
# Write a function sum_of_digits(n: int) -> int that calculates the sum of the digits of a given number n.

# Find Second Largest Number
# Implement a function second_largest(numbers: list) -> int that returns the second largest number from a given list of numbers.
def main():
    # Factorial Calculator
    print(factorial(5)) 
    # Palindrome Checker
    print(is_palindromne("level"))
    # Prime Number Checker
    print(is_prime(13))
    # Greatest Common Divisor (GCD)
    print(gcd(12, 18))
    # Fibonacci Sequence Generator
    print(fibonacci(10))
    # Armstrong Number Checker
    print(is_armstrong(153))
    # Temperature Converter
    print(convert_temperature(212, "F"))
    print(convert_temperature(0, "C"))
    print(convert_temperature(273.15, "K"))
    # Word Frequency Counter
    print(word_count("Hello world, hello again!"))

main()
```