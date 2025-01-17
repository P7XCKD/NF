non premtive FCFS Priority Code 

```c
#include <stdio.h>

#define MAX_PROCESSES 100

int main() {
    int n;

    printf("Enter the number of processes: ");
    scanf("%d", &n);

    if (n > MAX_PROCESSES) {
        printf("Error: Number of processes exceeds limit.\n");
        return 1;
    }

    int arrival[MAX_PROCESSES], burst[MAX_PROCESSES], priority[MAX_PROCESSES];
    int completion[MAX_PROCESSES] = {0};
    int turnaround[MAX_PROCESSES], waiting[MAX_PROCESSES], response[MAX_PROCESSES];

    for (int i = 0; i < n; i++) {
        printf("Enter the arrival time, burst time, and priority for process %d: ", i + 1);
        scanf("%d %d %d", &arrival[i], &burst[i], &priority[i]);
    }

    int current_time = 0;
    int completed = 0;

    while (completed < n) {
        int highest_priority = -1;
        int highest_priority_index = -1;

        for (int i = 0; i < n; i++) {
            if (arrival[i] <= current_time && completion[i] == 0) {
                if (highest_priority == -1 || priority[i] < highest_priority) {
                    highest_priority = priority[i];
                    highest_priority_index = i;
                }
            }
        }

        if (highest_priority_index == -1) {
            current_time++;
        } else {
            completion[highest_priority_index] = current_time + burst[highest_priority_index];
            turnaround[highest_priority_index] = completion[highest_priority_index] - arrival[highest_priority_index];
            waiting[highest_priority_index] = turnaround[highest_priority_index] - burst[highest_priority_index];
            response[highest_priority_index] = current_time - arrival[highest_priority_index];
            current_time = completion[highest_priority_index];
            completed++;
        }
    }

    printf("\nPID\tAT\tBT\tPrio\tCT\tTAT\tWT\tRT\n");
    for (int i = 0; i < n; i++) {
        printf("%d\t%d\t%d\t%d\t%d\t%d\t%d\t%d\n", i + 1, arrival[i], burst[i], priority[i], completion[i], turnaround[i], waiting[i], response[i]);
    }

    float avg_tat = 0, avg_wt = 0;
    for (int i = 0; i < n; i++) {
        avg_tat += turnaround[i];
        avg_wt += waiting[i];
    }
    printf("\nAverage Turnaround Time (TAT): %.2f\n", avg_tat / n);
    printf("Average Waiting Time (WT): %.2f\n", avg_wt / n);

    return 0;
}