# p2 dst 27/07/2024

insertion sort
```C
#include <stdio.h>

int main() {
    int arr[10];
    int n, i, j, loc, temp;

    printf("Enter the no. of elements:-");
    scanf("%d", &n);
    printf("Enter the elements:-");
    for (i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("Print the unsorted array:-");
    for (i = 0; i < n; i++) {
        printf("%d\n", arr[i]);
    }

    for (i = 1; i < n; i++) {
        loc = i;
        temp = arr[i];
        for (j = i - 1; j >= 0; j--) {
            if (temp < arr[j]) {
                loc = j;
                arr[j + 1] = arr[j];
            }
        }
        arr[loc] = temp;
    }

    printf("\nPrint the sorted array:-");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    return 0;
}