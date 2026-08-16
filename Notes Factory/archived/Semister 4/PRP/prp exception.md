```python
# 1) Smart Calculator with Error Handling
# Problem Statement:
# Create a calculator that takes two numbers as input and performs division. The program should handle the following exceptions:

# ZeroDivisionError: If the denominator is zero, display a proper message.
# ValueError: If the user enters non-numeric values, ask them to enter numbers again.

# Example Usage:
# Enter first number: 10  
# Enter second number: ABC  
# Output: Invalid input! Please enter numbers only.  

# Enter first number: 10  
# Enter second number: 0  
# Output: Error! Cannot divide by zero.
def get_number(prompt):
    while True:
        try:
            return float(input(prompt))  # Attempt to convert the input to a float
        except ValueError:
            print("Invalid input! Please enter a valid number.")

def smart_calculator():
    print("Welcome to the Smart Calculator!")

    
    num1 = get_number("Enter the first number: ")

    
    num2 = get_number("Enter the second number: ")

    try:
       
        result = num1 / num2
    except ZeroDivisionError:
        print("Error: Cannot divide by zero!")
    else:
        print(f"The result of dividing {num1} by {num2} is: {result}")

smart_calculator()

# 2) User Input Validation for List Access
# Problem Statement:
# Create a program where the user enters an index to access an element from a predefined list. Handle the following exceptions:

# IndexError: If the user enters an index that is out of range, inform them.
# ValueError: If the user enters a non-integer value, prompt them to enter a valid index.
# Example Usage:

# List: ['Apple', 'Banana', 'Orange']  
# Enter an index: 5  
# Output: Index out of range! Please enter a number between 0 and 2.  

# Enter an index: ABC  
# Output: Invalid input! Please enter a number. 

def get_valid_index():
    while True:
        try:
            
            index = int(input("Enter an index: "))
            return index
        except ValueError:
            print("Invalid input! Please enter a number.")

def access_list_element():
    predefined_list = ['Apple', 'Banana', 'Orange']
    
    print(f"List: {predefined_list}")
    
    
    index = get_valid_index()

    try:
        
        element = predefined_list[index]
        print(f"The element at index {index} is: {element}")
    except IndexError:
        print(f"Index out of range! Please enter a number between 0 and {len(predefined_list) - 1}.")


access_list_element()

# 3) Division Calculator Handling ZeroDivisionError
# Problem Statement:
# Create a Calculator class that allows users to divide two numbers. If the user tries to divide by zero, handle the built-in ZeroDivisionError and display a meaningful error message.

# Class Requirements:
# A Calculator class with a method divide(a, b).
# The method should handle ZeroDivisionError if the denominator is zero.
# Instead of crashing, it should return "Error: Cannot divide by zero!".
# Example Usage:

# calc = DivisionCalculator()
# result = calc.divide(10, 0)  # Should return "Error: Cannot divide by zero!"

class DivisionCalculator:
    def divide(self, a, b):
        try:
            return a / b
        except ZeroDivisionError:
            return "Error: Cannot divide by zero!"

calc = DivisionCalculator()

result = calc.divide(10, 0)
print(result) 

result = calc.divide(10, 2)
print(result)

# 4) Dictionary Lookup Handling KeyError
# Problem Statement:
# Create a StudentDatabase class that stores student names and their scores in a dictionary. Implement a method get_score(student_name), which returns the student's score. If the student is not found, handle KeyError and return "Error: Student not found!".

# Class Requirements:
# A StudentDatabase class with a dictionary students.
# A method get_score(student_name), which fetches the score if found.
# If the student is not found, handle KeyError and display "Error: Student not found!".

# Example Usage:
# db = StudentDatabase({"Alice": 85, "Bob": 92})
# score = db.get_score("Charlie")  # Should return "Error: Student not found!"
class StudentDatabase:
    def __init__(self, students):
        self.students = students

    def get_score(self, student_name):
        try:
            return self.students[student_name]
        except KeyError:
            return "Error: Student not found!"

db = StudentDatabase({"Alice": 85, "Bob": 92})


score1 = db.get_score("Alice")
score2 = db.get_score("Charlie")  

print(f"Alice's score: {score1}")
print(f"Charlie's score: {score2}")


# 5) Problem Statement:
# You need to implement a BankAccount class that allows users to deposit and withdraw money. However, if a user tries to withdraw an amount greater than their balance, the system should raise a custom InsufficientFundsException.

# Class Requirements:
# A BankAccount class with attributes: account_holder, balance.
# Methods:
# deposit(amount): Adds money to the balance.
# withdraw(amount): Deducts money but raises InsufficientFundsException if balance is insufficient.
# A custom exception InsufficientFundsException that inherits from Exception.
# Example Usage:

# acc = BankAccount("John Doe", 500)
# acc.withdraw(600)  # Should raise InsufficientFundsException
# Custom Exception for Insufficient Funds
class InsufficientFundsException(Exception):
    def __init__(self, message="Insufficient funds in your account"):
        self.message = message
        super().__init__(self.message)

class BankAccount:
    def __init__(self, account_holder, balance=0):
        self.account_holder = account_holder
        self.balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            print(f"{amount} deposited. New balance is {self.balance}.")
        else:
            print("Deposit amount must be greater than zero.")

    def withdraw(self, amount):
        if amount > self.balance:
            raise InsufficientFundsException(f"Attempted to withdraw {amount}, but balance is only {self.balance}.")
        elif amount <= 0:
            print("Withdrawal amount must be greater than zero.")
        else:
            self.balance -= amount
            print(f"{amount} withdrawn. New balance is {self.balance}.")

try:
    acc = BankAccount("John Doe", 500)
    acc.withdraw(600)
except InsufficientFundsException as e:
    print(e)

acc.deposit(200)
acc.withdraw(400)


```