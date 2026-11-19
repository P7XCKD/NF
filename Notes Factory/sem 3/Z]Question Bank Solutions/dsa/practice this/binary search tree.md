# Binary Search Tree (BST) – Practice Solutions

**Rule:** Smaller values go to the left; greater values go to the right.

For each question, insert the elements in the given order, draw the
final BST, and find the three traversals.

------------------------------------------------------------------------

## Q1. Easy

**Elements:**

``` text
50, 30, 70, 20, 40, 60, 80
```

### Step 1: Insert elements

1.  50 → Root node.
2.  30 → Smaller than 50, goes left.
3.  70 → Greater than 50, goes right.
4.  20 → Smaller than 50 and 30, goes left of 30.
5.  40 → Smaller than 50 but greater than 30, goes right of 30.
6.  60 → Greater than 50 but smaller than 70, goes left of 70.
7.  80 → Greater than 50 and 70, goes right of 70.

### Step 2: Final BST

``` text
        50
       /  \
     30    70
    / \    / \
   20 40  60 80
```

### Step 3: Traversals

| Traversal | Rule                | Answer                     |
|-----------|---------------------|----------------------------|
| Inorder   | Left → Root → Right | 20, 30, 40, 50, 60, 70, 80 |
| Preorder  | Root → Left → Right | 50, 30, 20, 40, 70, 60, 80 |
| Postorder | Left → Right → Root | 20, 40, 30, 60, 80, 70, 50 |

------------------------------------------------------------------------

## Q2. Medium

**Elements:**

``` text
45, 25, 65, 15, 35, 55, 75, 30, 40, 60
```

### Step 1: Insert elements

| Element | Position    |
|---------|-------------|
| 45      | Root        |
| 25      | Left of 45  |
| 65      | Right of 45 |
| 15      | Left of 25  |
| 35      | Right of 25 |
| 55      | Left of 65  |
| 75      | Right of 65 |
| 30      | Left of 35  |
| 40      | Right of 35 |
| 60      | Right of 55 |

### Step 2: Final BST

``` text
             45
           /    \
         25      65
        /  \    /  \
      15   35  55   75
          /  \   \
         30  40   60
```

### Step 3: Traversals

| Traversal | Answer                                 |
|-----------|----------------------------------------|
| Inorder   | 15, 25, 30, 35, 40, 45, 55, 60, 65, 75 |
| Preorder  | 45, 25, 15, 35, 30, 40, 65, 55, 60, 75 |
| Postorder | 15, 30, 40, 35, 25, 60, 55, 75, 65, 45 |

------------------------------------------------------------------------

## Q3. Hard

**Elements:**

``` text
60, 40, 80, 20, 50, 70, 90, 10, 30, 45, 55, 65, 75, 85, 100, 42
```

### Step 1: Insert elements

| Element | Position    |
|---------|-------------|
| 60      | Root        |
| 40      | Left of 60  |
| 80      | Right of 60 |
| 20      | Left of 40  |
| 50      | Right of 40 |
| 70      | Left of 80  |
| 90      | Right of 80 |
| 10      | Left of 20  |
| 30      | Right of 20 |
| 45      | Left of 50  |
| 55      | Right of 50 |
| 65      | Left of 70  |
| 75      | Right of 70 |
| 85      | Left of 90  |
| 100     | Right of 90 |
| 42      | Left of 45  |

### Step 2: Final BST

``` text
                         60
                    /         \
                  40           80
                /   \         /  \
              20     50      70   90
             / \    /  \    / \   / \
           10  30  45  55  65 75 85 100
                  /
                 42
```

### Step 3: Traversals

| Traversal | Answer                                                          |
|-----------|-----------------------------------------------------------------|
| Inorder   | 10, 20, 30, 40, 42, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 100 |
| Preorder  | 60, 40, 20, 10, 30, 50, 45, 42, 55, 80, 70, 65, 75, 90, 85, 100 |
| Postorder | 10, 30, 20, 42, 45, 55, 50, 40, 65, 75, 70, 85, 100, 90, 80, 60 |

------------------------------------------------------------------------

## Quick Revision

| Traversal | Rule                |
|-----------|---------------------|
| Inorder   | Left → Root → Right |
| Preorder  | Root → Left → Right |
| Postorder | Left → Right → Root |

**Exam trick:** In a BST with distinct values, Inorder traversal always
gives the elements in ascending order.
