
---

Experiment 10: Creation and Traversing a Linked List
```c
#include<stdio.h>
#include<stdlib.h>

struct Node
{
   int data;
   struct Node *next;
};

struct Node * createNodes(struct Node *s)
{
    int n;
    printf("Enter the node value\n");
    scanf("%d",&n);
    struct Node * temp = (struct Node *)malloc(sizeof(struct Node));
    temp->data =n;
    temp->next=NULL;
    struct Node * start = s;
    if(start==NULL)
     {
        start=temp;
        printf("First Node Created\n");
        return start;
     }
     struct Node * travel = s;
     while(travel->next!=NULL)
     {
     	travel=travel->next;
     }
     travel->next =temp;
     return start;
}

void displayNode(struct Node *s)
{
    struct Node *travel=s;
    if(travel==NULL)
    {
    	printf("List is empty\n");
    	return;
    }
    while(travel!=NULL)
    {
    	printf("%d\n",travel->data);
    	travel=travel->next;
    }
}

int main()
{
    int i,n;
    struct Node *start = NULL;
    printf("How many nodes you want to create?\n");
    scanf("%d",&n);
    for(i=1;i<=n;i++)
    {
        start=createNodes(start);
	}
    printf("The list of nodes is as follows:\n");
    displayNode(start);
    return 0;
}

```
---

Experiment 11: Perform Various Operations on a Linked List (Insertion and Deletion)
```c
#include<stdio.h>
#include<stdlib.h>

struct Node
{
   int data;
   struct Node *next;
};

struct Node * insertNode(struct Node *s)
{
    printf("Welcome to insert node operation\n");
    int num,choice;
    struct Node * temp = (struct Node *)malloc(sizeof(struct Node));
    printf("Enter the node value\n");
    scanf("%d",&temp->data);
    temp->next=NULL;
    struct Node *start=s;
    struct Node *travel=s;
    printf("Enter the options for the following choices:\n");
    printf("1-insert at the beginning\n");
    printf("2-insert at the end\n");
    printf("3-insert after specified node data\n");
    scanf("%d",&choice);
    switch(choice)
    {
    case 1:
            temp->next=start;
            start=temp;
            break;
    case 2:
            while(travel->next!=NULL)
            {
                travel=travel->next;
            }
            travel->next =temp;
            break;
    case 3:
            printf("Enter the data part after which you want to enter the new node\n");
            scanf("%d",&num);
            while(travel->data!=num && travel->next!=NULL)
            {
                travel=travel->next;
            }
            if(travel->data==num)
            {
                temp->next=travel->next;
                travel->next=temp;
            }
            else
            {
                printf("As desired node not found, we can not add the new node\n");
                free(temp);
            }
            break;
    default:
             printf("Invalid Option\n");
             free(temp);
             break;
    }

     return start;
}

struct Node * delNode(struct Node * s)
{
     int num;
     struct Node * travel = s;
     struct Node * start=s;
     if(travel==NULL)
     {
         printf("Linked List is empty\n");
         return NULL;
     }
     printf("enter the node data to be deleted\n");
     scanf("%d",&num);
     struct Node * prev=s;
     while(travel->data!=num && travel->next!=NULL)
     {
         prev=travel;
         travel=travel->next;
     }
     if(travel->data==num)
     {
         if(travel==s)
         {
             start=travel->next;
         }
         else
         {
             prev->next=travel->next;
         }
         free(travel);
     }
     else
     {
         printf("Desired node not found so delete operation failed!!!\n");
     }
     return start;
}

void displayNode(struct Node *s)
{
    struct Node *travel=s;
    if(travel==NULL)
    {
    	printf("List is empty\n");
    	return;
    }
    while(travel!=NULL)
    {
    	printf("%d\n",travel->data);
    	travel=travel->next;
    }
}

int main()
{
    struct Node *start = NULL;

    // calling insertion operation
    start=insertNode(start);
    printf("The list of nodes is as follows:\n");
    displayNode(start);

    start=delNode(start);
    printf("The list of nodes is as follows:\n");
    displayNode(start);
    
    return 0;
}

```
---


### Experiment 10: Creation and Traversing a Linked List

#### Input:
How many nodes you want to create?  
3  
Enter the node value  
10  
First Node Created  
Enter the node value  
20  
Enter the node value  
30  

#### Output:
The list of nodes is as follows:  
10  
20  
30  

---

### Experiment 11: Perform Various Operations on a Linked List (Insertion and Deletion)

#### Insertion:

##### Input:
Welcome to insert node operation  
Enter the node value  
40  
Enter the options for the following choices:  
1-insert at the beginning  
2-insert at the end  
3-insert after specified node data  
2  

##### Output:
The list of nodes is as follows:  
40  

---

#### Deletion:

##### Input:
enter the node data to be deleted  
40  

##### Output:
The list of nodes is as follows:  
List is empty