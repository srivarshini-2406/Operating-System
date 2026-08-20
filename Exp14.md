# EXPERIMENT 14

## Description

File allocation strategies: Sequential, Indexed, and Linked allocation.

## C Program

```c
#include <stdio.h>

int main() {
    int n, b[20], i;

    scanf("%d", &n);

    for (i = 0; i < n; i++)
        scanf("%d", &b[i]);

    printf("Linked Allocation: ");

    for (i = 0; i < n; i++) {
        printf("%d", b[i]);

        if (i < n - 1)
            printf(" -> ");
    }

    printf(" -> NULL\n");

    return 0;
}
