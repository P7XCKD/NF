INSERTION IN ARRAY:
```c
#include <stdio.h>

int main() {
    int n, i;

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
DELETION IN ARRAY:
```c
#include <stdio.h>

int main() {
    int n, i;

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
    else {
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

LINEAR SEARCH:
```c
#include <stdio.h>

int main() {
    int size, target, found = 0;

    printf("Enter the number of elements: ");
    scanf("%d", &size);

    int arr[size];

    printf("Enter %d elements:\n", size);
    for (int i = 0; i < size; i++) {
        scanf("%d", &arr[i]);
    }

    printf("Enter the element to search: ");
    scanf("%d", &target);

    printf("Element found at indices: ");
    for (int i = 0; i < size; i++) {
        if (arr[i] == target) {
            printf("%d ", i);
            found = 1;
        }
    }

    if (!found) {
        printf("Element not found in the array");
    }

    printf("\n");
    return 0;
}
|``



BINARY SEARCH:
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
            found++;
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

BUBBLE SORT:
```c
#include <stdio.h>

int main() {
    int n, i, j, temp;

    printf("Enter the number of elements in the array: ");
    scanf("%d", &n);

    int arr[n];

    printf("Enter the elements of the array:\n");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }

    printf("Sorted array in ascending order:\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}
```

SELECTION SORT:
```c
#include <stdio.h>

int min(int *arr,int k,int n);

void main() {
    int n, k, i, temp, loc;

    printf("Enter number of the elements : ");
    scanf("%d", &n);
    int arr[n];

    for (i = 1; i <= n; i++) {
        printf("Enter %d element :", i);
        scanf("%d", &arr[i]);
    }

    for (k = 1; k <= n; k++) {
        loc = min(arr, k, n);
        temp = arr[loc];
        arr[loc] = arr[k];
        arr[k] = temp;
        for (i = 1; i <= n; i++) {
            printf("%d , ", arr[i]);
        }
        printf("\n");
    }
    printf("Sorted Array : \n");
    for (i = 1; i <= n; i++) {
        printf("%d ,", arr[i]);
    }
}

int min(int *arr, int k, int n) {
    int min = k;
    for (min = k; k <= n; k++) {
        if (arr[min] > arr[k]) {
            min = k;
        }
    }
    return min;
}
```
INSERTION SORT:
```c
#include <stdio.h>

int main() {
    int a[100], n, k, temp, ptr;

    printf("Enter number of elements: ");
    scanf("%d", &n);

    for (int i = 0; i < n; i++) {
        printf("Enter Element[%d]: ", i);
        scanf("%d", &a[i]);
    }

    for (k = 1; k < n; k++) {
        temp = a[k];
        ptr = k - 1;

        while (ptr >= 0 && temp < a[ptr]) {
            a[ptr + 1] = a[ptr];
            ptr = ptr - 1;
        }
        a[ptr + 1] = temp;

        printf("Elements after Pass %d:\n", k);
        for (int u = 0; u < n; u++) {
            printf("%d ", a[u]);
        }
        printf("\n");
    }

    printf("Sorted array:\n");
    for (int j = 0; j < n; j++) {
        printf("Element %d is: %d\n", j, a[j]);
    }

    return 0;
}
```

QUICK SORT:
```c
#include <stdio.h>
#include <conio.h>
#define size 100

int partition(int a[], int beg, int end);
void quick_sort(int a[], int beg, int end);

void main() {
    int arr[size], i, n;

    printf("\n Enter the number of elements in the array: ");
    scanf("%d", &n);
    printf("\n Enter the elements of the array: ");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    quick_sort(arr, 0, n - 1);
    printf("\n The sorted array is: \n");
    for (i = 0; i < n; i++)
        printf(" %d\t", arr[i]);
    getch();
}

int partition(int a[], int beg, int end) {
    int left, right,