<p>
    <span style="float:left;">
        <h3> DSA Experiment 5
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>

<br clear="both">

### AIM

Implementation of Singly Linked List and various operations for real-world applications.

### OBJECTIVE

- To create a singly linked list.
- To insert a node at the beginning.
- To delete a node from the beginning.
- To display the linked list.

### THEORY

A **Singly Linked List** is a dynamic data structure consisting of nodes. Each node contains data and a pointer to the next node. The last node points to `NULL`.

**Operations:**
- **Create:** Creates nodes and links them together.
- **Insertion:** Adds a new node at the beginning of the list.
- **Deletion:** Removes the first node and frees its memory.
- **Traversal:** Visits and displays each node until `NULL` is reached.

### ALGORITHM

**1. Create a Linked List**
1. Start.
2. Enter the number of nodes.
3. Allocate memory for each node.
4. Enter data and link the nodes.
5. Set the last node's pointer to `NULL`.
6. Stop.

**2. Insert at Beginning**
1. Create a new node.
2. Enter the data.
3. Set its next pointer to the current head.
4. Update head to the new node.
5. Stop.

**3. Delete from Beginning**
1. Check whether the list is empty.
2. Store the first node in a temporary pointer.
3. Update head to the next node.
4. Free the previous first node.
5. Stop.

**4. Display the List**
1. Start from head.
2. Display each node's data.
3. Move to the next node.
4. Repeat until `NULL` is reached.
5. Stop.

### OUTCOME

A menu-driven C program was implemented to create, insert, delete, and display nodes in a singly linked list.

### CONCLUSION

Thus, a singly linked list was successfully implemented in C with various operations.