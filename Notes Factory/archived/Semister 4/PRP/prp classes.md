```python
# 1. Class for a Rectangle
# Problem: Create a class called Rectangle that has the following methods:

# __init__(self, width, height): Initializes the rectangle with a given width and height.
# area(self): Returns the area of the rectangle.
# perimeter(self): Returns the perimeter of the rectangle.
# display(self): Prints the width, height, area, and perimeter of the rectangle.
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height
        self._area = self.width * self.height
        self._perimeter = 2 * (self.width + self.height)
    def area(self):
        return self._area
    def perimeter(self):
        return self._perimeter
    def display(self):
        print(f"Width: {self.width}, Height: {self.height}, Area: {self.area()}, Perimeter: {self.perimeter()}")

# 2. Class for a Bank Account
# Problem: Create a class called BankAccount that has the following methods:

# __init__(self, owner, balance): Initializes the account with the owner's name and balance.
# deposit(self, amount): Deposits a specified amount into the account.
# withdraw(self, amount): Withdraws a specified amount from the account.
# get_balance(self): Returns the current balance of the account.
# display(self): Prints the owner's name and the current balance.
class BankAccount:
    def __init__(self, owner, balance=0):
        # Initializes the account with the owner's name and balance (default is 0)
        self.owner = owner
        self.balance = balance
    def deposit(self, amount):
        # Deposits a specified amount into the account
        if amount > 0:
            self.balance += amount
            print(f"Deposited {amount}. Current balance: {self.balance}")
        else:
            print("Deposit amount must be positive.")
    def withdraw(self, amount):
        # Withdraws a specified amount from the account
        if 0 < amount <= self.balance:
            self.balance -= amount
            print(f"Withdrew {amount}. Current balance: {self.balance}")
        else:
            print("Insufficient funds or invalid withdrawal amount.")
    def get_balance(self):
        # Returns the current balance of the account
        return self.balance
    def display(self):
        # Prints the owner's name and the current balance
        print(f"Owner: {self.owner}, Current balance: {self.balance}")

# 3. Class for a Book
# Problem: Create a class called Book that has the following methods:

# __init__(self, title, author, year): Initializes the book with a title, author, and year of publication.
# get_book_info(self): Returns a string with the book's title, author, and year.
# is_old(self): Returns True if the book is more than 20 years old, otherwise False.
from datetime import datetime

class Book:
    def __init__(self, title, author, year):
        self.title = title
        self.author = author
        self.year = year
    def get_book_info(self):
        return f"Title: {self.title}, Author: {self.author}, Year: {self.year}"
    def is_old(self):
        current_year = datetime.now().year
        return current_year - self.year > 20
    
# 4. Class for a Car
# Problem: Create a class called Car that has the following methods:

# __init__(self, make, model, year): Initializes the car with its make, model, and year.
# get_car_info(self): Returns a string with the car's make, model, and year.
# start(self): Prints "The car is starting."
# stop(self): Prints "The car is stopping."
# 5. Class for a Student
# Problem: Create a class called Student that has the following methods:

# __init__(self, name, grade): Initializes the student with their name and grade.
# change_grade(self, new_grade): Changes the student's grade to the new grade.
# get_student_info(self): Returns the student's name and grade as a string.
# is_passed(self): Returns True if the student's grade is above or equal to 50, otherwise False.

def main():
    rect = Rectangle(5, 10)
    rect.display()
    account = BankAccount("Alice", 1000)
    account.display()
    account.deposit(500)
    account.withdraw(200)
    print(f"Current balance: {account.get_balance()}")
    account.display()
    book = Book("The Great Gatsby", "F. Scott Fitzgerald", 1925)
    print(book.get_book_info())

    if book.is_old():
        print("The book is more than 20 years old.")
    else:
        print("The book is not more than 20 years old.")

    new_book = Book("A Modern Book", "John Doe", 2010)
    print(new_book.get_book_info())

    if new_book.is_old():
        print("The book is more than 20 years old.")
    else:
        print("The book is not more than 20 years old.")

main()

```