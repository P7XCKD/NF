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
### output
![image](.attachments/b5153b41d85349f949ac602d6d33f34b1cd17d53.png) 
![image](.attachments/6d525eb0d9248e81fe590af30666a1569aaf292a.png) 
![image](.attachments/ff53aa26ca683024c3126c1ecdef1afc0aa929b0.png) 
***
> [!attention] dont use delete as function name
> certain keywords are reserved using them...will give errors for example delete
