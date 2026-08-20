# EXPERIMENT 4

## Description

CPU scheduling using First Come First Serve (FCFS).

## C Program

```c
#include <stdio.h>

int main() {
    int n, i, bt[20], wt[20] = {0}, tat[20];
    int tw = 0, tt = 0;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &bt[i]);
    }

    for (i = 1; i < n; i++) {
        wt[i] = wt[i - 1] + bt[i - 1];
    }

    for (i = 0; i < n; i++) {
        tat[i] = wt[i] + bt[i];
        tw += wt[i];
        tt += tat[i];
    }

    printf("Average Waiting Time = %.2f\n", (float)tw / n);
    printf("Average Turnaround Time = %.2f\n", (float)tt / n);

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

read -p "Number of processes: " n
read -a bt

wt=0
total=0

for ((i=0; i<n; i++))
do
    total=$((total + wt))
    wt=$((wt + bt[i]))
done

echo "FCFS scheduling completed"
```

## Sample Input

```text
3
5 3 8
```

## Sample Output

```text
Average Waiting Time = 4.33
Average Turnaround Time = 9.67
```
