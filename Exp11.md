# EXPERIMENT 11

## Description

Memory allocation using First Fit, Best Fit and Worst Fit.

## C Program

```c
#include <stdio.h>

int main() {
    int b[20], p[20];
    int n, m, i, j, idx;

    scanf("%d%d", &n, &m);

    for (i = 0; i < n; i++) {
        scanf("%d", &b[i]);
    }

    for (i = 0; i < m; i++) {
        scanf("%d", &p[i]);
    }

    for (i = 0; i < m; i++) {
        idx = -1;

        for (j = 0; j < n; j++) {
            if (b[j] >= p[i]) {
                idx = j;
                break;
            }
        }

        if (idx != -1) {
            printf("Process %d -> Block %d\n", i + 1, idx + 1);
            b[idx] -= p[i];
        }
        else {
            printf("Process %d -> Not Allocated\n", i + 1);
        }
    }

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

echo "First Fit Memory Allocation"
echo "Blocks: 100 500 200 300 600"
echo "Processes: 212 417 112 426"
```

## Sample Input

```text
5 4
100 500 200 300 600
212 417 112 426
```

## Sample Output

```text
Process 1 -> Block 2
Process 2 -> Block 5
Process 3 -> Block 2
Process 4 -> Not Allocated
```
