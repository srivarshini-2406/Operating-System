# EXPERIMENT 12

## Description

Page replacement using FIFO, LRU and Optimal algorithms.

## C Program

```c
#include <stdio.h>

int main() {
    int a[50], f[10];
    int n, nf, i, j, k = 0;
    int fault = 0, hit;

    scanf("%d", &n);

    for (i = 0; i < n; i++) {
        scanf("%d", &a[i]);
    }

    scanf("%d", &nf);

    for (i = 0; i < nf; i++) {
        f[i] = -1;
    }

    for (i = 0; i < n; i++) {
        hit = 0;

        for (j = 0; j < nf; j++) {
            if (f[j] == a[i]) {
                hit = 1;
            }
        }

        if (!hit) {
            f[k] = a[i];
            k = (k + 1) % nf;
            fault++;
        }
    }

    printf("FIFO Page Faults = %d\n", fault);

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

echo "FIFO Page Replacement"
echo "Reference String: 7 0 1 2 0 3 0 4 2 3 0 3 2"
echo "Frames: 3"
```

## Sample Input

```text
13
7 0 1 2 0 3 0 4 2 3 0 3 2
3
```

## Sample Output

```text
FIFO Page Faults = 10
LRU Page Faults = 9
Optimal Page Faults = 7
```
