Start implementation of fcfc

1.you can use queue
2.take arrival time in sequence
3.calculate all parameters


```c
#include <stdio.h>

int main() {
    int n;

    // Input the number of processes
    printf("Enter the number of processes: ");
    scanf("%d", &n);

    if (n <= 0) {
        printf("Invalid number of processes.\n");
        return -1;
    }

    // Arrays to hold the process data
    int pID[n], aT[n], bT[n], wT[n], tAT[n], cT[n];

    // Input Arrival Time and Burst Time for each process
    for (int i = 0; i < n; i++) {
        pID[i] = i + 1; // Process ID
        printf("Enter Arrival Time and Burst Time for Process %d: ", i + 1);
        scanf("%d%d", &aT[i], &bT[i]);

        if (bT[i] <= 0) {
            printf("Burst time must be greater than 0.\n");
            return -1;
        }
    }

    // Sort processes by Arrival Time
    for (int i = 0; i < n - 1; i++) {
        for (int j = i + 1; j < n; j++) {
            if (aT[i] > aT[j]) {
                // Swap arrival time
                int temp = aT[i];
                aT[i] = aT[j];
                aT[j] = temp;

                // Swap burst time
                temp = bT[i];
                bT[i] = bT[j];
                bT[j] = temp;

                // Swap process ID
                temp = pID[i];
                pID[i] = pID[j];
                pID[j] = temp;
            }
        }
    }

    // Calculate Waiting Time and Completion Time
    wT[0] = 0;                          // Waiting time for the first process is 0
    cT[0] = aT[0] + bT[0];              // Completion time of the first process

    for (int i = 1; i < n; i++) {
        wT[i] = (cT[i - 1] > aT[i]) ? cT[i - 1] - aT[i] : 0; // Waiting time
        cT[i] = aT[i] + wT[i] + bT[i];                       // Completion time
    }

    // Calculate Turnaround Time
    for (int i = 0; i < n; i++) {
        tAT[i] = cT[i] - aT[i]; // Turnaround Time = Completion Time - Arrival Time
    }

    // Print process details
    int totalWaitingTime = 0, totalTurnaroundTime = 0;
    printf("\nPID\tArrival\tBurst\tWaiting\tTurnaround\tCompletion\n");
    for (int i = 0; i < n; i++) {
        totalWaitingTime += wT[i];
        totalTurnaroundTime += tAT[i];
        printf("%d\t%d\t%d\t%d\t%d\t\t%d\n", pID[i], aT[i], bT[i], wT[i], tAT[i], cT[i]);
    }

    // Print average times
    printf("\nAvg Waiting Time: %.2f\n", (float)totalWaitingTime / n);
    printf("Avg Turnaround Time: %.2f\n", (float)totalTurnaroundTime / n);

    return 0;
}
```



***
```c
#include<stdio.h>

int main()
{
    int bt[20], p[20], wt[20], tat[20], i, j, n, total = 0, totalT = 0, pos, temp;
    float avg_wt, avg_tat;

    printf("Enter number of processes: ");
    scanf("%d", &n);

    printf("\nEnter Burst Time:\n");
    for(i = 0; i < n; i++)
    {
        printf("p%d: ", i + 1);
        scanf("%d", &bt[i]);
        p[i] = i + 1;  // Process ID
    }

    // Sorting by Burst Time
    for(i = 0; i < n; i++)
    {
        pos = i;
        for(j = i + 1; j < n; j++)
        {
            if(bt[j] < bt[pos])
                pos = j;
        }

        temp = bt[i];
        bt[i] = bt[pos];
        bt[pos] = temp;

        temp = p[i];
        p[i] = p[pos];
        p[pos] = temp;
    }

    wt[0] = 0; // Waiting time for the first process is 0

    // Calculating Waiting Time
    for(i = 1; i < n; i++)
    {
        wt[i] = 0;
        for(j = 0; j < i; j++)
            wt[i] += bt[j];

        total += wt[i];  // Accumulating total waiting time
    }

    avg_wt = (float)total / n;  // Average waiting time

    printf("\nProcess\t Burst Time\tWaiting Time\tTurnaround Time");
    for(i = 0; i < n; i++)
    {
        tat[i] = bt[i] + wt[i];  // Turnaround time = Burst time + Waiting time
        totalT += tat[i];        // Accumulating total turnaround time

        printf("\np%d\t\t %d\t\t %d\t\t\t%d", p[i], bt[i], wt[i], tat[i]);
    }

    avg_tat = (float)totalT / n;  // Average turnaround time

    printf("\n\nAverage Waiting Time = %f", avg_wt);
    printf("\nAverage Turnaround Time = %f", avg_tat);

    return 0;
}
```