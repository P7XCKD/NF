Start implementation of fcfc

1.you can use queue
2.take arrival time in sequence
3.calculate all parameters

``` not verified the below code```
```c
#include <stdio.h>
#include <stdlib.h>

// Structure to represent a process
typedef struct {
    int process_id;
    int arrival_time;
    int burst_time;
    int completion_time;
    int waiting_time;
    int turnaround_time;
} Process;

// Function to calculate completion, turnaround, and waiting times for all processes
void calculate_times(Process processes[], int n) {
    int current_time = 0;

    for (int i = 0; i < n; i++) {
        if (processes[i].arrival_time > current_time) {
            current_time = processes[i].arrival_time;
        }

        processes[i].completion_time = current_time + processes[i].burst_time;
        processes[i].turnaround_time = processes[i].completion_time - processes[i].arrival_time;
        processes[i].waiting_time = processes[i].turnaround_time - processes[i].burst_time;

        current_time = processes[i].completion_time;
    }
}

// Function to print details of all processes
void print_processes(Process processes[], int n) {
    printf("Process ID\tArrival Time\tBurst Time\tCompletion Time\tTurnaround Time\tWaiting Time\n");
    for (int i = 0; i < n; i++) {
        printf("%d\t\t%d\t\t%d\t\t%d\t\t%d\t\t\t%d\n",
               processes[i].process_id,
               processes[i].arrival_time,
               processes[i].burst_time,
               processes[i].completion_time,
               processes[i].turnaround_time,
               processes[i].waiting_time);
    }
}

// Function to calculate average turnaround time
float calculate_average_turnaround_time(Process processes[], int n) {
    int total_turnaround_time = 0;
    for (int i = 0; i < n; i++) {
        total_turnaround_time += processes[i].turnaround_time;
    }
    return (float)total_turnaround_time / n;
}

// Function to calculate average waiting time
float calculate_average_waiting_time(Process processes[], int n) {
    int total_waiting_time = 0;
    for (int i = 0; i < n; i++) {
        total_waiting_time += processes[i].waiting_time;
    }
    return (float)total_waiting_time / n;
}

// Function to sort processes by arrival time
void sort_processes_by_arrival_time(Process processes[], int n) {
    for (int i = 0; i < n - 1; i++) {
        for (int j = i + 1; j < n; j++) {
            if (processes[i].arrival_time > processes[j].arrival_time) {
                Process temp = processes[i];
                processes[i] = processes[j];
                processes[j] = temp;
            }
        }
    }
}

int main() {
    int n;

    // Input the number of processes
    printf("Enter the number of processes: ");
    scanf("%d", &n);

    if (n <= 0) {
        printf("Invalid number of processes.\n");
        return -1;
    }

    // Allocate memory for processes
    Process *processes = (Process *)malloc(n * sizeof(Process));

    // Input arrival time and burst time for each process
    for (int i = 0; i < n; i++) {
        processes[i].process_id = i + 1;
        printf("\nEnter arrival time and burst time for process %d: ", i + 1);
        scanf("%d %d", &processes[i].arrival_time, &processes[i].burst_time);

        if (processes[i].burst_time <= 0) {
            printf("Burst time must be greater than 0.\n");
            free(processes);
            return -1;
        }
    }

    // Sort processes by arrival time
    sort_processes_by_arrival_time(processes, n);

    // Calculate times for all processes
    calculate_times(processes, n);

    // Print process details
    print_processes(processes, n);

    // Calculate and print average turnaround and waiting times
    float avg_turnaround_time = calculate_average_turnaround_time(processes, n);
    printf("\nAverage Turnaround Time: %.2f\n", avg_turnaround_time);

    float avg_waiting_time = calculate_average_waiting_time(processes, n);
    printf("\nAverage Waiting Time: %.2f\n", avg_waiting_time);

    // Free the allocated memory
    free(processes);

    return 0;
}
```