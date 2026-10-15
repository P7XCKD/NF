<div align = "center">

<a href="https://ibb.co/0y4jv78d" align="center"><img src="https://i.ibb.co/8gvDtCTS/image.png" alt="image" align="center"></a>
</div>


<p>
    <span style="float:left;">
        <h3> DSA Experiment 6
    </span>
    <span style="float:right; text-align:right;"> 
        Name: Dev Mandora<br>
        Roll Number: 62 <br>
        Batch: SB4</h3>
    </span>
</p>
          
### Aim:

To Implement Binary Tree and its Traversal for real-world application.

### Objective:

- To understand the concept and structure of a Binary Tree.
- To learn how nodes are created and connected.
- To implement Inorder, Preorder, and Postorder traversal.
- To understand the applications of binary trees in real-world scenarios.
- To implement a simple decision-support use case using a binary tree.

### Software Used:

- Turbo C / Turbo C++
- DOSBox

### Theory:

A **Binary Tree** is a non-linear data structure in which each node can have at most two children: left and right. The topmost node is called the root, and nodes without children are called leaf nodes.

Tree traversal is the process of visiting every node in a specific order.

- **Inorder:** Left, Root, Right
- **Preorder:** Root, Left, Right
- **Postorder:** Left, Right, Root

Binary trees are used in decision-making systems, file-system hierarchies, expression evaluation, and searching. A Binary Search Tree stores smaller values on the left and larger values on the right.

### Program 1: AI Use Case – Heatwave Risk Classification Using Binary Tree

This program uses a Binary Search Tree to store temperature readings and classify them into heatwave alert levels using predefined rules. It demonstrates a simple rule-based decision-support application.


```c
#include <stdio.h>
#include <conio.h>
#include <stdlib.h>

struct node
{
    int temperature;
    struct node *left;
    struct node *right;
};

struct node* createNode(int temp)
{
    struct node *p;

    p = (struct node *)malloc(sizeof(struct node));

    p->temperature = temp;
    p->left = NULL;
    p->right = NULL;

    return p;
}

struct node* insert(struct node *root, int temp)
{
    if(root == NULL)
        return createNode(temp);

    if(temp < root->temperature)
        root->left = insert(root->left, temp);
    else if(temp > root->temperature)
        root->right = insert(root->right, temp);

    return root;
}

void displayRisk(int temp)
{
    printf("%d C - ", temp);

    if(temp >= 45)
        printf("Red Alert\n");
    else if(temp >= 43)
        printf("Orange Alert\n");
    else if(temp >= 40)
        printf("Yellow Alert\n");
    else
        printf("Normal\n");
}

void preorder(struct node *root)
{
    if(root == NULL)
        return;

    displayRisk(root->temperature);
    preorder(root->left);
    preorder(root->right);
}

void inorder(struct node *root)
{
    if(root == NULL)
        return;

    inorder(root->left);
    displayRisk(root->temperature);
    inorder(root->right);
}

void postorder(struct node *root)
{
    if(root == NULL)
        return;

    postorder(root->left);
    postorder(root->right);
    displayRisk(root->temperature);
}

void main()
{
    struct node *root = NULL;
    int choice, temp;

    do
    {
        printf("\n HEATWAVE RISK MENU ");
        printf("\n1. Insert Temperature");
        printf("\n2. Preorder Report");
        printf("\n3. Inorder Report");
        printf("\n4. Postorder Report");
        printf("\n5. Exit");
        printf("\nEnter choice: ");
        scanf("%d", &choice);

        switch(choice)
        {
            case 1:
                printf("Enter temperature: ");
                scanf("%d", &temp);
                root = insert(root, temp);
                printf("Temperature added.\n");
                break;

            case 2:
                if(root == NULL)
                    printf("Tree is empty.\n");
                else
                {
                    printf("\nPreorder Heatwave Report:\n");
                    preorder(root);
                }
                break;

            case 3:
                if(root == NULL)
                    printf("Tree is empty.\n");
                else
                {
                    printf("\nInorder Heatwave Report:\n");
                    inorder(root);
                }
                break;

            case 4:
                if(root == NULL)
                    printf("Tree is empty.\n");
                else
                {
                    printf("\nPostorder Heatwave Report:\n");
                    postorder(root);
                }
                break;

            case 5:
                printf("Exiting...");
                break;

            default:
                printf("Invalid choice.");
        }

        if(choice != 5)
        {
            printf("\nPress any key to continue...");
            getch();
        }

    } while(choice != 5);

    getch();
}
````

### Output:

Sample output:

```
 HEATWAVE RISK MENU 
1. Insert Temperature
2. Preorder Report
3. Inorder Report
4. Postorder Report
5. Exit
Enter choice: 1
Enter temperature: 43
Temperature added.

Enter choice: 1
Enter temperature: 38
Temperature added.

Enter choice: 1
Enter temperature: 46
Temperature added.

Enter choice: 3

Inorder Heatwave Report:
38 C - Normal
43 C - Orange Alert
46 C - Red Alert
```

### Program 2: Basic Binary Tree and Traversal

```c
#include <stdio.h>
#include <conio.h>
#include <stdlib.h>

struct node
{
    int data;
    struct node *left;
    struct node *right;
};

struct node* createNode(int value)
{
    struct node *p;

    p = (struct node *)malloc(sizeof(struct node));

    p->data = value;
    p->left = NULL;
    p->right = NULL;

    return p;
}

struct node* insert(struct node *root, int value)
{
    if(root == NULL)
        return createNode(value);

    if(value < root->data)
        root->left = insert(root->left, value);
    else if(value > root->data)
        root->right = insert(root->right, value);

    return root;
}

void preorder(struct node *root)
{
    if(root == NULL)
        return;

    printf("%d ", root->data);
    preorder(root->left);
    preorder(root->right);
}

void inorder(struct node *root)
{
    if(root == NULL)
        return;

    inorder(root->left);
    printf("%d ", root->data);
    inorder(root->right);
}

void postorder(struct node *root)
{
    if(root == NULL)
        return;

    postorder(root->left);
    postorder(root->right);
    printf("%d ", root->data);
}

void main()
{
    struct node *root = NULL;
    int choice, value;

    do
    {
        printf("\n BINARY TREE MENU ");
        printf("\n1. Insert a Node");
        printf("\n2. Preorder Traversal");
        printf("\n3. Inorder Traversal");
        printf("\n4. Postorder Traversal");
        printf("\n5. Exit");
        printf("\nEnter choice: ");
        scanf("%d", &choice);

        switch(choice)
        {
            case 1:
                printf("Enter value to insert: ");
                scanf("%d", &value);
                root = insert(root, value);
                break;

            case 2:
                if(root == NULL)
                    printf("Tree is empty.");
                else
                {
                    printf("Preorder: ");
                    preorder(root);
                }
                break;

            case 3:
                if(root == NULL)
                    printf("Tree is empty.");
                else
                {
                    printf("Inorder: ");
                    inorder(root);
                }
                break;

            case 4:
                if(root == NULL)
                    printf("Tree is empty.");
                else
                {
                    printf("Postorder: ");
                    postorder(root);
                }
                break;

            case 5:
                printf("Exiting...");
                break;

            default:
                printf("Invalid choice.");
        }

        if(choice != 5)
        {
            printf("\nPress any key to continue...");
            getch();
        }

    } while(choice != 5);

    getch();
}
```

### Output:

Sample output:

```
 BINARY TREE MENU 
1. Insert a Node
2. Preorder Traversal
3. Inorder Traversal
4. Postorder Traversal
5. Exit
Enter choice: 1
Enter value to insert: 32

Enter choice: 1
Enter value to insert: 52

Enter choice: 1
Enter value to insert: 21

Enter choice: 2
Preorder: 32 21 52

Enter choice: 3
Inorder: 21 32 52

Enter choice: 4
Postorder: 21 52 32

Enter choice: 5
Exiting...
```

### Outcome:

The Binary Tree was implemented successfully. Nodes were inserted, and Preorder, Inorder, and Postorder traversal techniques were performed. A rule-based heatwave risk classification application was also demonstrated.

### Conclusion:

Thus, binary tree construction and traversal techniques were implemented successfully. The practical demonstrated how binary trees organize data and support traversal and simple decision-support applications.
