# EXPERIMENT 15

## Description

Disk scheduling using FCFS, SSTF, SCAN and C-SCAN.

## C Program

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int n, a[20], head, i, seek = 0;

    scanf("%d", &n);

    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);

    scanf("%d", &head);

    for (i = 0; i < n; i++) {
        seek += abs(a[i] - head);
        head = a[i];
    }

    printf("FCFS Total Head Movement = %d\n", seek);

    return 0;
}
