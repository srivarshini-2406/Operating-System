# EXPERIMENT 8

## Description

Deadlock detection using Allocation, Request and Available matrices.

## C Program

```c
#include <stdio.h>

int main() {
    int n, m;
    int a[10][10], r[10][10], w[10];
    int f[10] = {0};
    int i, j, k, found, dead = 0;

    scanf("%d%d", &n, &m);

    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            scanf("%d", &a[i][j]);
        }
    }

    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            scanf("%d", &r[i][j]);
        }
    }

    for (j = 0; j < m; j++) {
        scanf("%d", &w[j]);
    }

    do {
        found = 0;

        for (i = 0; i < n; i++) {
            if (!f[i]) {
                for (j = 0; j < m && r[i][j] <= w[j]; j++);

                if (j == m) {
                    for (k = 0; k < m; k++) {
                        w[k] += a[i][k];
                    }

                    f[i] = 1;
                    found = 1;
                }
            }
        }
    } while (found);

    printf("Deadlocked Processes: ");

    for (i = 0; i < n; i++) {
        if (!f[i]) {
            printf("P%d ", i);
            dead = 1;
        }
    }

    if (!dead) {
        printf("None");
    }

    printf("\n");

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

echo "Enter deadlocked process numbers (if any):"

read p

if [ -z "$p" ]
then
    echo "No Deadlock Detected"
else
    echo "Deadlocked Processes: $p"
fi
```

## Sample Input

```text
3 2
1 0
0 1
1 1
0 1
1 0
1 1
1 1
```

## Sample Output

```text
Deadlocked Processes: P2
```
