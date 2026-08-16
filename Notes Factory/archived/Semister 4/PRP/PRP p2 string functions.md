```python
str = "This is an example of a string that will  be displayed  in the output"

def countingwords(str):
    print(f"The number of words in the string is {str.count(' ')}")

def validategmail(str):
 if str.count('@') or str.count('.') != 1:
    print("Invalid email address")
 else:
    print("Valid email address")

def search(str):
    word = input("Enter a word to search: ")
    if str.count(word)<0:
        print(f"{word} not found in the string")
    else:
        print(f"{word} found {str.count(word)} times")

def displaydiff(str):
   words = str.split(' ')
   for i in range(0,len(words)):
      print(f'''{words[i]} \n''')

def filepath(str):
   w=input("Enter a string")
   numslash=w.rindex('/')
   numdot=w.rindex('.')
   print(f"The name is {w[numslash+1:numdot]}")

def reverse(str):
    print(str[::-1])

def main():
    print("1. Display the string")
    print("2. Count the number of words in the string")
    print("3. Validate email address")
    print("4. Search for a word in the string")
    print("5. Display the words in the string")
    print("6. Get the name from the filepath")
    print("7. Reverse the string")
    choice = int(input("Enter your choice: "))
    if choice == 1:
        print(str)
    elif choice == 2:
        countingwords(str)
    elif choice == 3:
        validategmail(str)
    elif choice == 4:
        search(str)
    elif choice == 5:
        displaydiff(str)
    elif choice == 6:
        filepath(str)
    elif choice == 7:
        reverse(str)
    else:
        print("Invalid choice")

main()

```