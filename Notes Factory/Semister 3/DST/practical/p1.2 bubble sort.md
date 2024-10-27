```c
#include<stdio.h>

int main()
{
    int arr[10],loc,size, value;
    printf("Enter the size of an array: ");
    scanf("%d", &size);
    printf("Enter the elements of an array: ");
    for(int i = 0; i < size; i++){
        scanf("%d", &arr[i]);
    }
    printf("Enter the location: ");
    scanf("%d", &loc);
    printf("Enter the Value: ");
    scanf("%d", &value);

    for(int i = size-1; i >= loc-1; i--){
        arr[i+1] = arr[i];
    }
    arr[loc-1] = value;

    printf("Resultant array is: ");
    for(int i = 0; i <= size; i++){
        printf("%d  ", arr[i]);
    }

    return 0;
}
```