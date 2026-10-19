### DSA Experiment 9

### AIM:

To implement Binary Search Technique considering a real-world application.

### THEORY:

Binary Search is a searching technique used to find an element in a sorted array. It compares the target value with the middle element and repeatedly reduces the search range by half.

**Steps:**

1. Find the middle element of the sorted array.
2. If the middle element matches the target, the search is successful.
3. If the target is smaller, search the left half.
4. If the target is greater, search the right half.
5. Repeat until the element is found or the search range becomes empty.

**Time Complexity:** O(log n)

Binary Search is used in applications that require efficient searching of sorted data. In temperature monitoring, it can locate a specific temperature reading from a sorted list.

### ALGORITHM:

1. Start.
2. Read the number of temperature readings.
3. Input the temperature readings into an array.
4. Sort the array in ascending order.
5. Read the temperature to be searched.
6. Initialize `low = 0` and `high = n - 1`.
7. Calculate the middle index using `mid = (low + high) / 2`.
8. If the middle element matches the target, display its position.
9. If the target is smaller, set `high = mid - 1`; otherwise, set `low = mid + 1`.
10. Repeat steps 7–9 while `low <= high`.
11. If the element is not found, display an appropriate message.
12. Stop.

### OUTCOME:

Binary Search was implemented successfully to search for an element in a sorted array.

### CONCLUSION:

Binary Search efficiently searches sorted data by repeatedly dividing the search range into two halves.