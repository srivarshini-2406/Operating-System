# EXPERIMENT 10

## Description

Paging and logical-to-physical address translation.

## C Program

```c
#include <stdio.h>

int main() {
    int ps, np, pt[20], la, p, o, pa;

    scanf("%d%d", &ps, &np);

    for (int i = 0; i < np; i++) {
        scanf("%d", &pt[i]);
    }

    scanf("%d", &la);

    p = la / ps;
    o = la % ps;

    if (p >= np) {
        printf("Invalid Logical Address\n");
        return 0;
    }

    pa = pt[p] * ps + o;

    printf("Page Number : %d\n", p);
    printf("Offset : %d\n", o);
    printf("Frame Number : %d\n", pt[p]);
    printf("Physical Address : %d\n", pa);

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

read -p "Page size: " ps
read -p "Page number: " p
read -p "Frame number: " f
read -p "Offset: " o

echo "Physical Address : $((f * ps + o))"
```

## Sample Input

```text
100 4
5 2 8 1
250
```

## Sample Output

```text
Page Number : 2
Offset : 50
Frame Number : 8
Physical Address : 850
```
