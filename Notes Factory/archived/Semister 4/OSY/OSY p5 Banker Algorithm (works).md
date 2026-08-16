### bankers algorithm pre defined input
```c
#include <stdio.h>

int main()
{
    // P0, P1, P2, P3, P4 are the Process names here

    int n, m, i, j, k;
    n = 5; // Number of processes
    m = 3; // Number of resources
    int alloc[5][3] =
    {
        {1, 1, 2},
        {2, 1, 2},
        {4, 0, 1},
        {0, 2, 0},
        {1, 1, 2}
    };

    int max[5][3] =
    {
        {4, 3, 3},
        {3, 2, 2},
        {9, 0, 2},
        {7, 5, 3},
        {1, 1, 2}
    };
    int avail[3] = {2, 1, 0};

    // Printing the Allocation, Max, and Available matrices
    printf("Allocation Matrix:\n");
    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            printf("%d ", alloc[i][j]);
        }
        printf("\n");
    }

    printf("\nMax Matrix:\n");
    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            printf("%d ", max[i][j]);
        }
        printf("\n");
    }

    // Printing the Available Matrix (as a row vector)
    printf("\nAvailable Resources:\n");
    for (i = 0; i < m; i++) {
        printf("%d ", avail[i]);
    }
    printf("\n");

    // Calculate the Need matrix
    int f[n], ans[n], ind = 0;
    for (k = 0; k < n; k++) {
        f[k] = 0;
    }
    int need[n][m];
    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            need[i][j] = max[i][j] - alloc[i][j];
        }
    }

    // Printing the Need Matrix
    printf("\nNeed Matrix:\n");
    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            printf("%d ", need[i][j]);
        }
        printf("\n");
    }

    // Safe Sequence Calculation
    int y = 0;
    for (k = 0; k < 5; k++) {
        for (i = 0; i < n; i++) {
            if (f[i] == 0) {
                int flag = 0;
                for (j = 0; j < m; j++) {
                    if (need[i][j] > avail[j]) {
                        flag = 1;
                        break;
                    }
                }

                if (flag == 0) {
                    ans[ind++] = i;
                    for (y = 0; y < m; y++) {
                        avail[y] += alloc[i][y];
                    }
                    f[i] = 1;

                    // Printing the Available Resources after allocation
                    printf("\nAvailable Resources after P%d allocation:\n", i);
                    for (y = 0; y < m; y++) {
                        printf("%d ", avail[y]);
                    }
                    printf("\n");
                }
            }
        }
    }

    int flag = 1;
    for (i = 0; i < n; i++) {
        if (f[i] == 0) {
            flag = 0;
            printf("The following system is not safe\n");
            break;
        }
    }

    if (flag == 1) {
        printf("Following is the SAFE Sequence\n");
        for (i = 0; i < n - 1; i++)
            printf(" P%d ->", ans[i]);
        printf(" P%d", ans[n - 1]);
    }

    return (0);
}


```