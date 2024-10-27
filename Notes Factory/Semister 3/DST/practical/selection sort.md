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
### Algorithm: Finding Minimum Element in a Subarray  
**Procedure**: **MIN(A, K, N, LOC)**  
- **Description**:
  - **A** is an array with **N elements**.
  - This procedure finds the **location LOC** of the smallest element in the subarray **A[K], A[K+1], …, A[N]**.

---

1. **Initialize Minimum and Location Pointers**  
   - **Set MIN := A[K]** and **LOC := K**

2. **Find the Smallest Element**  
   - For **J = K + 1** to **N**, repeat:
     - If **MIN > A[J]**, then:
       - **Set MIN := A[J]** and **LOC := J**
   - **End of loop**

3. **Return**  

---

### Algorithm: Selection Sort  
**Procedure**: **SELECTION(A, N)**  
- **Description**:
  - **A** is an array with **N elements**.
  - This algorithm sorts **A** by repeatedly finding the minimum element from the unsorted part and swapping it with the first unsorted element.

---

1. **Repeat for Each Position**  
   - For **K = 1, 2, …, N - 1**, repeat Steps 2 and 3:

2. **Find the Minimum in the Subarray**  
   - Call **MIN(A, K, N, LOC)** to get the location **LOC** of the smallest element in the subarray **A[K], A[K+1], …, A[N]**.

3. **Swap Elements**  
   - **Set TEMP := A[K]**, **A[K] := A[LOC]**, and **A[LOC] := TEMP**

   - **End of loop**

4. **Exit**