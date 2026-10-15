<div align = "center">

<a href="https://ibb.co/0y4jv78d" align="center"><img src="https://i.ibb.co/8gvDtCTS/image.png" alt="image" align="center"></a>
</div>


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

### Aim:

To implement Singly Linked List

### Objective:

- To understand the concept and structure of a Singly Linked List.
- To learn how nodes are created and linked dynamically using pointers.
- To implement insertion, deletion, and traversal operations.
- To understand dynamic memory allocation and how linked lists differ from arrays.
- To implement a real-world application using a Singly Linked List.

### Software Used:

- Turbo C / Turbo C++
- DOSBox

### Theory:

A **Singly Linked List** is a linear data structure in which elements, called nodes, are connected using pointers. Each node contains two parts: a data field and a pointer to the next node. The last node points to `NULL`.

Unlike arrays, linked lists do not require contiguous memory locations. Memory is allocated dynamically whenever a new node is created.

The first node is accessed using a pointer called `HEAD`. Basic operations include insertion, deletion, traversal, and searching. A singly linked list supports traversal only in the forward direction.

### Program 1: AI Use Case – Heatwave Alert Management Using Singly Linked List

This program simulates an AI-assisted heatwave alert system. It stores temperature readings in a linked list and classifies them into alert levels using predefined rules.

- Temperature below 40°C: Normal
- Temperature from 40°C to below 43°C: Yellow Alert
- Temperature from 43°C to below 45°C: Orange Alert
- Temperature of 45°C or above: Red Alert



```c
#include <stdio.h>
#include <conio.h>
#include <stdlib.h>

typedef struct node
{
    int temperature;
    struct node *next;
} node;

node *head = NULL;

void display()
{
    node *p;

    if(head == NULL)
    {
        printf("\nNo readings available.\n");
        return;
    }

    printf("\nHeatwave Alert Report:\n");

    for(p = head; p != NULL; p = p->next)
    {
        printf("Temperature: %d C - ", p->temperature);

        if(p->temperature >= 45)
            printf("Red Alert\n");
        else if(p->temperature >= 43)
            printf("Orange Alert\n");
        else if(p->temperature >= 40)
            printf("Yellow Alert\n");
        else
            printf("Normal\n");
    }
}

void createList()
{
    node *p, *last = NULL;
    int n, i, temp;

    printf("Enter number of readings: ");
    scanf("%d", &n);

    for(i = 0; i < n; i++)
    {
        printf("Enter temperature: ");
        scanf("%d", &temp);

        p = (node *)malloc(sizeof(node));

        p->temperature = temp;
        p->next = NULL;

        if(head == NULL)
            head = p;
        else
            last->next = p;

        last = p;
    }

    display();
}

void insertBeg()
{
    node *p;
    int temp;

    printf("Enter temperature: ");
    scanf("%d", &temp);

    p = (node *)malloc(sizeof(node));

    p->temperature = temp;
    p->next = head;
    head = p;

    printf("Reading added successfully.\n");

    display();
}

void deleteBeg()
{
    node *p;

    if(head == NULL)
    {
        printf("No readings available.\n");
        return;
    }

    p = head;

    printf("Deleted temperature: %d\n", p->temperature);

    head = head->next;
    free(p);

    display();
}

void main()
{
    int choice;

    do
    {
        printf("\n1. Create Readings");
        printf("\n2. Add Reading");
        printf("\n3. Delete First Reading");
        printf("\n4. Exit");
        printf("\nEnter choice: ");
        scanf("%d", &choice);

        switch(choice)
        {
            case 1:
                createList();
                break;

            case 2:
                insertBeg();
                break;

            case 3:
                deleteBeg();
                break;

            case 4:
                printf("Program exited.");
                break;

            default:
                printf("Invalid choice.");
        }

    } while(choice != 4);

    getch();
}
````

### Output:




![image](.attachments/862c62b4d198404539bf05ecc93e4b86fc3ff8df.png) 

![image](.attachments/a91165c65aa4387b6d56069e82aeaec932418c92.png) 

### Program 2: Basic Singly Linked List
> [!attention] Limitations
delete operation only deletes the element at the begining
> likewise for insert operation
> 

```c
#include <stdio.h>
#include <conio.h>
#include <stdlib.h>

typedef struct node
{
    int data;
    struct node *next;
} node;

node *head = NULL;

void createList()
{
    node *p, *last = NULL;
    int n, i;

    printf("Enter number of nodes: ");
    scanf("%d", &n);

    for(i = 0; i < n; i++)
    {
        p = (node *)malloc(sizeof(node));

        printf("Enter data: ");
        scanf("%d", &p->data);

        p->next = NULL;

        if(head == NULL)
            head = p;
        else
            last->next = p;

        last = p;
    }
}

void insertBeg()
{
    node *p;

    p = (node *)malloc(sizeof(node));

    printf("Enter data to insert: ");
    scanf("%d", &p->data);

    p->next = head;
    head = p;
}

void deleteBeg()
{
    node *p;

    if(head == NULL)
    {
        printf("Empty Linked List\n");
        return;
    }

    p = head;
    printf("Deleted element: %d\n", p->data);

    head = head->next;
    free(p);
}

void printList()
{
    node *p;

    if(head == NULL)
    {
        printf("Empty Linked List\n");
        return;
    }

    printf("Linked List: ");

    for(p = head; p != NULL; p = p->next)
        printf("%d ", p->data);

    printf("\n");
}

void main()
{
    int choice;

    do
    {
        printf("\n1. Create a List");
        printf("\n2. Insert a Node");
        printf("\n3. Delete a Node");
        printf("\n4. Print the Existing List");
        printf("\n5. Exit");
        printf("\nEnter your choice: ");
        scanf("%d", &choice);

        switch(choice)
        {
            case 1:
                createList();
                break;
            case 2:
                insertBeg();
                break;
            case 3:
                deleteBeg();
                break;
            case 4:
                printList();
                break;
            case 5:
                printf("Program Finished.");
                break;
            default:
                printf("Please enter a valid choice.");
        }
    } while(choice != 5);

    getch();
}
```

### Output:



![image](.attachments/54c01fbe38e6772ef670d4a0cba505cbb30518a0.png) 
![image](.attachments/3df1cd9e4401ec174a4237b09ed22f66bc8e872e.png) 
![image](.attachments/83cc4453b3697dde1f6cfeef22176248d4c61a9d.png) 

### Outcome:

The singly linked list was implemented successfully. Node creation, insertion, deletion, and traversal operations were performed. A rule-based heatwave alert application was also demonstrated using a singly linked list.

### Conclusion:

Thus, the implementation of a Singly Linked List was studied successfully. The practical demonstrated dynamic memory allocation, pointer-based connections, and basic linked-list operations, along with a real-world heatwave alert management use case.

