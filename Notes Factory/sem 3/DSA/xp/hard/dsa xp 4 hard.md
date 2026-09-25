# DSA Experiment 4

### Aim:

To implement a Double-ended Queue (Deque) using an array and demonstrate Input Restricted Deque and Output Restricted Deque operations.

### Theory:

A Double-ended Queue (Deque) is a linear data structure in which insertion and deletion can be performed from both ends.

There are two types of restricted deque:

**Input Restricted Deque:**  
Insertion is allowed only from one end, while deletion is allowed from both ends.

**Output Restricted Deque:**  
Deletion is allowed only from one end, while insertion is allowed from both ends.

In this experiment, an array is used to implement the deque. The variables `left` and `right` are used to keep track of the two ends of the deque.

### Algorithm:



1. Start.
2. Initialize the deque using an array and set `left = -1` and `right = -1`.
3. Select the type of deque: Input Restricted or Output Restricted.
4. For **Input Restricted Deque**:
   - Insert elements only from the right end.
   - Delete elements from either the left or right end.
5. For **Output Restricted Deque**:
   - Insert elements from either the left or right end.
   - Delete elements only from the left end.
6. Before insertion, check whether the deque is full. If full, display Overflow.
7. Before deletion, check whether the deque is empty. If empty, display Underflow.
8. Perform the selected insertion, deletion, or display operation.
9. Repeat the operations until Exit is selected.
10. Stop.

### Outcome:

The program successfully implements a double-ended queue using an array and demonstrates Input Restricted Deque and Output Restricted Deque operations.

### Conclusion:

The experiment demonstrates the implementation of a Deque using an array and the different insertion and deletion restrictions of Input Restricted and Output Restricted Deques.