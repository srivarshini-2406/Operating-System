# EXPERIMENT 7

## Description

Deadlock avoidance using Banker's Algorithm and safe-sequence detection.

## C Program

```c
#include <stdio.h>

int main() {
    int n, m;
    int a[10][10], mx[10][10], need[10][10];
    int av[10], fin[10] = {0}, seq[10];
    int i, j, k, c = 0, found;

    scanf("%d%d", &n, &m);

    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            scanf("%d", &a[i][j]);
        }
    }

    for (i = 0; i < n; i++) {
        for (j = 0; j < m; j++) {
            scanf("%d", &mx[i][j]);
            need[i][j] = mx[i][j] - a[i][j];
        }
    }

    for (j = 0; j < m; j++) {
        scanf("%d", &av[j]);
    }

    while (c < n) {
        found = 0;

        for (i = 0; i < n; i++) {
            if (!fin[i]) {
                for (j = 0; j < m && need[i][j] <= av[j]; j++);

                if (j == m) {
                    for (k = 0; k < m; k++) {
                        av[k] += a[i][k];
                    }

                    fin[i] = 1;
                    seq[c++] = i;
                    found = 1;
                }
            }
        }

        if (!found) {
            break;
        }
    }

    if (c < n) {
        printf("System is NOT in Safe State\n");
    }
    else {
        printf("System is in Safe State\n");
        printf("Safe Sequence: ");

        for (i = 0; i < n; i++) {
            printf("P%d ", seq[i]);
        }

        printf("\n");
    }

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

echo "Banker's Algorithm - Safe State Demonstration"
echo "Enter safe sequence (process numbers):"

read -a seq

echo -n "Safe Sequence: "

for p in "${seq[@]}"
do
    echo -n "P$p "
done

echo
```

## Sample Input

```text
5 3
0 1 0
2 0 0
3 0 2
2 1 1
0 0 2
7 5 3
3 2 2
9 0 2
2 2 2
4 3 3
3 3 2
```

## Sample Output

```text
System is in Safe State
Safe Sequence: P1 P3 P4 P0 P2
```
