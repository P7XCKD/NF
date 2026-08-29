```c
#include<stdio.h>
#include<conio.h>

int q[10], front = -1, rear = -1, i, n, x, choice;

void insert();
void deletei();
void display();

void main()
{
    printf("enter the size of queue (max = 10): ");
    scanf("%d",&n);

    do
    {
        printf("\n q operations:\n");
        
        printf("1. insert \t 2. delete \t 3. display \n 4.exit \n");
        printf("\n enter your choice:");
        scanf("%d",&choice);

        switch(choice)
        {
            case 1:
                insert();
                break;

            case 2:
                deletei();
                break;

            case 3:
                display();
                break;

            case 4:
                printf("program exit");
                break;

            default:
                printf("1. insert \t 2. delete \t 3. display \n 4.exit \n");
                break;
        }
    } while(choice != 4);
}

void insert()
{
    if(rear >= n - 1)
    {
        printf("overflow\n");
    }
    else
    {
        printf("enter the element to insert:");
        scanf("%d",&x);

        rear++;
        q[rear] = x;

        if(front == -1)
        {
            front = 0;
        }
    }
}

void display()
{
    if(front == -1)
    {
        printf("underflow");
    }
    else
    {
        printf("element in q are\n");

        for(i=front; i<=rear; i++)
        {
            printf("%d ",q[i]);
        }

        printf("\n");
    }
}

void deletei()
{
    if(front == -1)
    {
        printf("underflow\n");
    }
    else
    {
        printf("deleted element is %d\n",q[front]);
        front++;

        if(front > rear)
        {
            front = -1;
            rear = -1;
        }
    }
}


```

***
> [!attention] dont use delete as function name
> certain keywords are reserved using them...will give errors for example delete
