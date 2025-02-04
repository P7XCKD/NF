```python
# 1. Convert two lists into a dictionary
keys = ['a', 'b', 'c']
values = [1, 2, 3]
merged_dict = dict(zip(keys, values))
print("1. Convert two lists into a dictionary:", merged_dict)

# 2. Merge two Python dictionaries into one
dict1 = {'a': 1, 'b': 2}
dict2 = {'b': 3, 'c': 4}
merged_dict = {**dict1, **dict2}
print("2. Merge two Python dictionaries into one:", merged_dict)

# 3. Delete a list of keys from a dictionary
dict_data = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
keys_to_delete = ['b', 'd']
for key in keys_to_delete:
    if key in dict_data:
        del dict_data[key]
print("3. Delete a list of keys from a dictionary:", dict_data)

# 4. Check if a dictionary is empty or not
sample_dict = {}
if not sample_dict:
    print("4. Dictionary is empty")
else:
    print("4. Dictionary is not empty")

# 5. Iterate over dictionaries using for loops
sample_dict = {'a': 1, 'b': 2, 'c': 3}
print("5. Iterate over dictionaries using for loops:")
for key, value in sample_dict.items():
    print(f"Key: {key}, Value: {value}")

# 6. Rename key of a dictionary
sample_dict = {'a': 1, 'b': 2}
sample_dict['new_key'] = sample_dict.pop('a')
print("6. Rename key of a dictionary:", sample_dict)

# 7. Get the key of a minimum value from a dictionary
sample_dict = {
    'Physics': 82,
    'Math': 65,
    'History': 75
}
min_key = min(sample_dict, key=sample_dict.get)
print("7. Key of the minimum value:", min_key)

# 8. Merge two Python dictionaries
dic1 = {1: 10, 2: 20}
dic2 = {3: 30, 4: 40}
merged_dict = {**dic1, **dic2}
print("8. Merge two Python dictionaries:", merged_dict)

# 9. Change Brad’s salary to 8500
sample_dict = {
    'emp1': {'name': 'John', 'salary': 7500},
    'emp2': {'name': 'Emma', 'salary': 8000},
    'emp3': {'name': 'Brad', 'salary': 500}
}
sample_dict['emp3']['salary'] = 8500
print("9. Change Brad's salary to 8500:", sample_dict)

# 10. Print a dictionary line by line
sample_dict = {'a': 1, 'b': 2, 'c': 3}
print("10. Print a dictionary line by line:")
for key, value in sample_dict.items():
    print(f"{key}: {value}")

# 11. Sort a dictionary by value (ascending and descending)
sample_dict = {'Math': 81, 'Physics': 83, 'Chemistry': 87}
sorted_dict_asc = sorted(sample_dict.items(), key=lambda x: x[1])
sorted_dict_desc = sorted(sample_dict.items(), key=lambda x: x[1], reverse=True)
print("11. Sorted dictionary by value (ascending):", sorted_dict_asc)
print("11. Sorted dictionary by value (descending):", sorted_dict_desc)

# 12. Count the number of items in a dictionary value that is a list
sample_dict = {'a': [1, 2, 3], 'b': [4, 5], 'c': [6, 7, 8, 9]}
count_items = {key: len(value) for key, value in sample_dict.items()}
print("12. Count the number of items in a dictionary value that is a list:", count_items)

# 13. Concatenate dictionaries to create a new one
dic1 = {1: 10, 2: 20}
dic2 = {3: 30, 4: 40}
dic3 = {5: 50, 6: 60}
merged_dict = {**dic1, **dic2, **dic3}
print("13. Concatenate dictionaries to create a new one:", merged_dict)

# 14. Sum all the items in a dictionary
sample_dict = {'a': 1, 'b': 2, 'c': 3}
sum_items = sum(sample_dict.values())
print("14. Sum all the items in a dictionary:", sum_items)

# 15. Multiply all the items in a dictionary
from functools import reduce
sample_dict = {'a': 1, 'b': 2, 'c': 3}
product_items = reduce(lambda x, y: x * y, sample_dict.values())
print("15. Multiply all the items in a dictionary:", product_items)

# 16. Add a key to a dictionary
sample_dict = {0: 10, 1: 20}
sample_dict[2] = 30
print("16. Add a key to a dictionary:", sample_dict)

# 17. Combine two dictionaries by adding values for common keys
d1 = {'a': 100, 'b': 200, 'c': 300}
d2 = {'a': 300, 'b': 200, 'd': 400}
from collections import Counter
combined_dict = Counter(d1) + Counter(d2)
print("17. Combine two dictionaries by adding values for common keys:", combined_dict)

# 18. Print all distinct values in a dictionary
data = [{"V":"S001"}, {"V": "S002"}, {"VI": "S001"}, {"VI": "S005"}, {"VII":"S005"}, {"V":"S009"},{"VIII":"S007"}]
unique_values = {v for dic in data for v in dic.values()}
print("18. Distinct values in a dictionary:", unique_values)

# 19. Find the highest 3 values of corresponding keys in a dictionary
sample_dict = {'Math': 81, 'Physics': 83, 'Chemistry': 87}
top_3 = sorted(sample_dict.items(), key=lambda x: x[1], reverse=True)[:3]
print("19. Highest 3 values:", top_3)

# 20. Sort Counter by value
from collections import Counter
sample_dict = {'Math': 81, 'Physics': 83, 'Chemistry': 87}
sorted_counter = sorted(sample_dict.items(), key=lambda x: x[1], reverse=True)
print("20. Sort Counter by value:", sorted_counter)

# 21. Create a dictionary from a string (count of letters)
sample_string = 'wwwroeocsursce'
letter_count = {char: sample_string.count(char) for char in set(sample_string)}
print("21. Create a dictionary from a string:", letter_count)

```