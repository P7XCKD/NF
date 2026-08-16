### static 
```c
#include<stdio.h>

void main() {
    int index, numProcesses, processSizes[5], blockCount = 1, allocatedBlocks[5];
    
    printf("Enter number of processes\n");
    scanf("%d", &numProcesses);
    
    if (numProcesses <= 5) {
        printf("Enter size of each process\n");
        
        for (index = 0; index < numProcesses; index++) {
            scanf("%d", &processSizes[index]);
            
            if (processSizes[index] <= 4) {
                printf("Process[%d] allocated to block %d\n", index + 1, blockCount);
                printf("Bytes remaining: %d\n", 4 - processSizes[index]);
                
                allocatedBlocks[blockCount - 1] = blockCount;
                blockCount++;
            } else {
                printf("Process can't be allocated\n");
            }
        }
        
        printf("\nProcesses completed:\n");
        for (index = 0; index < blockCount - 1; index++) {
            printf("Process[%d]\n", allocatedBlocks[index]);
        }
    } else {
        printf("Enter processes less than or equal to 5\n");
    }
}

```
***

### dynamic
```c
#include<stdio.h>

void main() {
    int totalMemory, numProcesses, index;
    printf("Enter memory size\n");
    scanf("%d", &totalMemory);
    
    printf("Enter no. of processes\n");
    scanf("%d", &numProcesses);
    
    int processSizes[numProcesses];
    for (index = 0; index < numProcesses; index++) {
        printf("Enter size of process %d: ", index + 1);
        scanf("%d", &processSizes[index]);
    }
    
    printf("\n");
    for (index = 0; index < numProcesses; index++) {
        if (processSizes[index] <= totalMemory) {
            printf("Process %d occupied: %d\n", index + 1, processSizes[index]);
            totalMemory = totalMemory - processSizes[index];
            printf("Bytes remaining: %d \n\n", totalMemory);
        } else {
            printf("Insufficient memory\n\n");
        }
    }
}

```