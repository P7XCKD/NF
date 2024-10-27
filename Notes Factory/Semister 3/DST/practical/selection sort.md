```c
#include<stdio.h>
void main()
{
    int n,k,i,temp,loc;
    printf("Enter number of the elements : ");
    scanf("%d",&n);
    int arr[n];
    for (i=1;i<=n;i++)
    {
        printf("Enter %d element :",i);
        scanf("%d",&arr[i]);
    }

    for(k=1;k<=n;k++)
    {
        loc = min(arr,k,n);
        temp = arr[loc];
        arr[loc] = arr[k];
        arr[k] = temp;
        for (i=1;i<=n;i++)
        {
            printf("%d , ",arr[i]);

        }
        printf("\n");
    }
    printf("Sorted Array : \n");
    for (i=1;i<=n;i++)
    {
        printf("%d ,",arr[i]);

    }
}
int min(int *arr,int k,int n)
{

    int min = k;
    for(min=k;k<=n;k++)
    {
        if(arr[min]>arr[k])
        {
            min = k;
        }
    }
    return min;
}
```