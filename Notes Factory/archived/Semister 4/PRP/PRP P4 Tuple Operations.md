```python
# Write a program to create a tuple containing integers, strings, and a mix of both. Display the tuple.

wow = ("a", "b", 7,9)
print(wow)

# Given a tuple (10, 20, 30, 40, 50), write a program to access and print the first, third, and last elements.

wow = (10,20,30,40,50)

print(wow[0])  
print(wow[2])
print(wow[-1])

# Write a program to slice the tuple (1, 2, 3, 4, 5, 6, 7) to display elements from index 2 to 5.

wow = (1, 2, 3, 4, 5, 6, 7)
print(wow[2:6])

# Write a program to count the occurrences of the number 5 in the tuple (5, 10, 5, 20, 5, 30).

wow = (5, 10, 5, 20, 5, 30)
print(wow.count(5))

# Write a program to find the index of the first occurrence of the element 25 in the tuple (10, 15, 20, 25, 30).

wow = (10, 15, 20, 25, 30)
print(wow.index(25))

# Given two tuples (1, 2, 3) and (4, 5, 6), write a program to concatenate them into a single tuple.

wow1 = (1,2,3)
wow2 = (4,5,6)
wow3 = wow1+wow2
print(wow3)

# Write a program to check if the element 15 is present in the tuple (10, 15, 20, 25).

wow = (10, 15, 20, 25)

if 15 in wow:
    print("Element is present in the tuple")
else:
    print("Element is not present in the tuple")

# Write a program to reverse the tuple (1, 2, 3, 4, 5) and print the reversed tuple.

wow = (1,2,3,4,5)
wow_rev = wow[::-1]
print(wow_rev)

# Demonstrate the immutability of tuples by trying to modify an element in the tuple (1, 2, 3)

# wow = (1,2,3,4,5)
# wow[0]=343
# print(wow)
################################    ERROR  ################################  
# #Traceback (most recent call last):
#   File "E:\A026Py\programs.py", line 54, in <module>
#     wow[0]=343
#     ~~~^^^
# TypeError: 'tuple' object does not support item assignment

# Write a program to convert the tuple (10, 20, 30) into a list, modify the list by adding a new element 40, and convert it back to a tuple.

wow = (10, 20, 30)
list = list(wow)
list.append(40)
wow = tuple(list)
print(wow)

# Write a program to create a tuple with a single element, 5, and print its type to verify it is a tuple.

wow = (5)
print(type(wow))

# Given a tuple (3, 7, 1, 9, 5), write a program to find and print the maximum and minimum values.

wow = (3,7, 1, 9, 5)
print(max(wow))
print(min(wow))

# Write a program to access the second element of the nested tuple ((1, 2), (3, 4), (5, 6)).

wow = ((1,2), (3,4), (5,6))
print(wow[1][::])

# Write a program to unpack the tuple (10, 20, 30) into three variables and print the values of these variables.

wow = (10, 20, 30)
a, b, c = wow
print(a, b, c)

# Write a program to create a tuple containing the squares of the first 10 prime numbers.

for num in range(1, 11):
    if num > 1: 
        for i in range(2, num):
            if num % i == 0:
                break
        else:
            print(num , num**2)
           

# Write a program to find and print the length of the tuple (10, 20, 30, 40, 50).

wow = (10, 20, 30, 40, 50)
print(len(wow))

# Write a program to convert a list ['apple', 'banana', 'cherry'] into a tuple. Then, modify the list by adding 'orange', convert it back into a tuple, and display both tuples.

wow = ['apple', 'banana', 'cherry']
tuple_wow = tuple(wow)
print(tuple_wow)
wow.append('orange')
tuple_wow_modified = tuple(wow)
print(tuple_wow_modified)

# Write a program to take a string, "Python is fun", and convert it into a tuple of individual words. Then, sort the tuple alphabetically and display the sorted tuple.

wow = "Python is fun"
words = wow.split()
sorted_words = tuple(sorted(words))
print(sorted_words)


# Given a tuple (1, 2, 3) and a list [4, 5, 6], write a program to convert the list into a tuple and merge it with the first tuple to create a single tuple (1, 2, 3, 4, 5, 6).
# Write a program to take a string "Hello, world! Programming is amazing.", split it into individual words, and store them as a tuple. Then, count how many times the word "is" appears in the tuple.
# Given a list of strings ["apple", "banana", "kiwi", "pear", "mango"], write a program to filter out words with less than 5 characters and store the remaining words in a tuple.
# # Write a program to take a list of strings ["hello", "world", "python", "programming"], extract the first character of each string, and store those characters in a tuple. Then, join the characters into a single string and display it.

```