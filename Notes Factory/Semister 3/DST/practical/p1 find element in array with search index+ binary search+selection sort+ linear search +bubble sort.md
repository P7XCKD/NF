find element in an array at each phase using search index


```c
#include <stdio.h>

int main() {
    int n, i, search, found = 0;

    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    int arr[n];

    printf("Enter the elements of the array:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("The elements of the array are:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    printf("Enter the element to search for: ");
    scanf("%d", &search);

    for (i = 0; i < n; i++) {
        if (arr[i] == search) {
            printf("Element %d found at index %d\n", search, i);
            found += 1;
        }
    }

    if (found == 0) {
        printf("Element %d not found in the array\n", search);
    }

    return 0;
}
```

insert an element in array

```c
#include <stdio.h>

int main() {
    int n, i, search, found = 0;

    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    int arr[n];

    printf("Enter the elements of the array:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("The elements of the array are:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    } 
    printf("\n");

    int element;
    printf("Enter the element to insert: ");
    scanf("%d", &element);

    int position;
    printf("Enter the position to insert the element (0 to %d): ", n);
    scanf("%d", &position);

    if (position < 0 || position > n) {
        printf("Invalid position to insert\n");
        return 1;
    }
    else {
    for (i = n; i > position; i--) {
        arr[i] = arr[i - 1];
    }

    arr[position] = element;

    n++;
    }
    printf("Array after insertion:\n");
    for (i = 0; i < n; i++) {
        printf("%d \n", arr[i]);
    }

    return 0;
}

```
delete an element in array

```c
#include <stdio.h>

int main() {
    int n, i, search, found = 0;

    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    int arr[n];

    printf("Enter the elements of the array:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("The elements of the array are:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    int index;
    printf("Enter the index to delete (0 to %d): ", n - 1);
    scanf("%d", &index);

    if (index < 0 || index >= n) {
        printf("Invalid index to delete\n");
        return 1;
    }
    else{
    for (i = index; i < n - 1; i++) {
        arr[i] = arr[i + 1];
    }

    n--; 
    }
    printf("Array after deletion:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    return 0;
}
```
binary search
```c
        #include <stdio.h>

int main() {
    int n, i, j, temp, search, found = 0;

    printf("enter the no of elements : ");
    scanf("%d", &n);

    int arr[n];

    printf("Enter the elements :\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
// sortingf part
    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }

    printf("sorted array in ascending order:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    printf("enter the element to search: ");
    scanf("%d", &search);

    int left = 0, right = n - 1, mid;
    while (left <= right) {
        mid = left + (right - left) / 2;

        if (arr[mid] == search) {
            printf(" found %d at index %d\n", search, mid);
            found += 1;
            break;
        } else if (arr[mid] < search) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }

    if (found == 0) {
        printf("element %d not found \n", search);
    }

    return 0;
}

```
selection sort
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
linear search code
```c
#include <stdio.h>

void ls(int data[], int n, int item, int *loc) {
    data[n] = item;
    int loc_var = 1;
    while (data[loc_var - 1] != item) {
        loc_var++;
    }
    if (loc_var == n + 1) {
        loc_var = 0;
    }
    *loc = loc_var;
}

int main() {
    int data[100], n, item, loc;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter elements:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d", &data[i]);
    }
    printf("Enter item to search: ");
    scanf("%d", &item);
    ls(data, n, item, &loc);
    if (loc == 0) {
        printf("Item not found.\n");
    } else {
        printf("Item found at position: %d\n", loc);
    }
    return 0;
}
```
bubble sort
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