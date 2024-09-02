v1
```c
#include <stdio.h>

void swap(int* a, int* b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}


int partition(int arr[], int low, int high) {

    
    int pivot = arr[low];
    int i = low;
    int j = high;

    while (i < j) {

        
        while (arr[i] <= pivot && i <= high - 1) {
            i++;
        }

        
        while (arr[j] > pivot && j >= low + 1) {
            j--;
        }
        if (i < j) {
            swap(&arr[i], &arr[j]);
        }
    }
    swap(&arr[low], &arr[j]);
    return j;
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {

        
        int partitionIndex = partition(arr, low, high);

        
        quickSort(arr, low, partitionIndex - 1);
        quickSort(arr, partitionIndex + 1, high);
    }
}

int main() {
  
    int arr[] = { 19, 7, 15, 12, 16, 18, 4, 11, 13 };
    int n = sizeof(arr) / sizeof(arr[0]);

    printf("Original array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

        quickSort(arr, 0, n - 1);

    printf("\nSorted array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }

    return 0;
}
```

v2
```c
#include <stdio.h>
#include <conio.h>
#define size 100
int partition(int a[], int beg, int end);
void quick_sort(int a[], int beg, int end);
void main()
{
int arr[size], i, n;
printf("\n Enter the number of elements in the array: ");
scanf("%d", &n);
printf("\n Enter the elements of the array: ");
for(i=0;i<n;i++)
{
 scanf("%d", &arr[i]);
}
quick_sort(arr, 0, n-1);
printf("\n The sorted array is: \n");
for(i=0;i<n;i++)
printf(" %d\t", arr[i]);
getch();
}
int partition(int a[], int beg, int end)
{
int left, right, temp, loc, flag;
loc = left = beg;
right = end;
flag = 0;
while(flag != 1)
{
while((a[loc] <= a[right]) && (loc!=right))
right--;
if(loc==right)
 flag =1;
 else if(a[loc]>a[right])
 {
 temp = a[loc];
 a[loc] = a[right];
 a[right] = temp;
 loc = right;
 }
if(flag!=1)
 {
while((a[loc] >= a[left]) && (loc!=left))
left++;
 if(loc==left)
flag =1;
 else if(a[loc] <a[left])
 {
 temp = a[loc];
a[loc] = a[left];
a[left] = temp;
loc = left;
 }
 }
}
return loc;
}
void quick_sort(int a[], int beg, int end)
{
int loc;
if(beg<end)
{
 loc = partition(a, beg, end);
quick_sort(a, beg, loc-1);
quick_sort(a, loc+1, end);
}
}




```