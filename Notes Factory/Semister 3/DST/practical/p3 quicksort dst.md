v1 pre-defined input
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

v2 user input
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

### Algorithm: QUICK(A, N, BEG, END, LOC)

- **Description**: 
  - Here, **A** is an array with **N elements**.
  - **BEG** and **END** contain the boundary values of the sublist within **A** where the procedure applies.
  - **LOC** keeps track of the position of the **first element (A[BEG])** during the procedure.
  - **LEFT** and **RIGHT** represent the unscanned list boundaries.

---

1. **Initialize**  
   - Set **LEFT := BEG**, **RIGHT := END**, and **LOC := BEG**.

---

2. **Scan from Right to Left**  
   - (a) **While A[LOC] ≤ A[RIGHT] and LOC ≠ RIGHT**:
       - Set **RIGHT := RIGHT – 1**.
       - **End of loop**
   - (b) If **LOC = RIGHT**, then **Return**.
   - (c) If **A[LOC] > A[RIGHT]**, then:
     - (i) **Interchange A[LOC] and A[RIGHT]**:
       - **TEMP := A[LOC], A[LOC] := A[RIGHT], A[RIGHT] := TEMP**
     - (ii) Set **LOC := RIGHT**
     - (iii) **Go to Step 3**
     - **End of If structure**

---

3. **Scan from Left to Right**  
   - (a) **While A[LEFT] ≤ A[LOC] and LEFT ≠ LOC**:
       - Set **LEFT := LEFT + 1**
       - **End of loop**
   - (b) If **LOC = LEFT**, then **Return**.
   - (c) If **A[LEFT] > A[LOC]**, then:
     - (i) **Interchange A[LEFT] and A[LOC]**:
       - **TEMP := A[LOC], A[LOC] := A[LEFT], A[LEFT] := TEMP**
     - (ii) Set **LOC := RIGHT**
     - (iii) **Go to Step 2**
     - **End of If structure**

---

### Algorithm: Quicksort for Array A with N Elements

1. **Initialize**: Set **TOP := NULL**

2. **Push boundary values of A onto stacks** (for lists with 2 or more elements)
   - If **N > 1**, then:
     - Set **TOP := TOP + 1**
     - **LOWER[1] := 1**, **UPPER[1] := N**

3. **Repeat Steps 4 to 7 while TOP ≠ NULL**

4. **Pop sublist from Stacks**
   - Set **BEG := LOWER[TOP]**, **END := UPPER[TOP]**
   - Set **TOP := TOP – 1**

5. **Call QUICK(A, N, BEG, END, LOC)**

6. **Push Left sublist onto stacks** (if it has 2 or more elements)
   - If **BEG < LOC – 1**, then:
     - Set **TOP := TOP + 1**
     - **LOWER[TOP] := BEG**
     - **UPPER[TOP] := LOC – 1**
     - **End of If structure**

7. **Push Right sublist onto stacks** (if it has 2 or more elements)
   - If **LOC + 1 < END**, then:
     - Set **TOP := TOP + 1**
     - **LOWER[TOP] := LOC + 1**
     - **UPPER[TOP] := END**
     - **End of If structure**

8. **Exit**