# p2 dst 27/07/2024

insertion sort
```C
#include<stdio.h>
int main(){
     int a[100];
     int n;
     int k;
     int temp;
     int ptr;
     printf("Enter number of elements: ");
     scanf("%d",& n);
     for(int i = 0; i <n ; i++){
        printf("Enter Element[%d]: ", i);
        scanf("%d", &a[i]);
     }
     for(k =0; k<n; k++){
        temp = a[k];
        ptr = k-1;
        while(temp < a[ptr]){
            a[ptr+1] = a[ptr];
            ptr = ptr-1;
        }
        a[ptr+1] = temp;
         printf("Elements after Pass %d: \n ", k);
        for(int u=0; u<n; u++){
           printf("%d ", a[u]);
            if(u >= n){
                break;
            }
        }
        printf("\n");
     }
     for(int j = 0; j <n; j++){
        printf("Element %d is: %d \n", j, a[j]);
     }
     return 0;
}


```