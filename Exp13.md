# EXPERIMENT 13

## Description

File organization techniques: Sequential, Direct (Random), and Indexed organization.

## C Program

```c
#include <stdio.h>

struct student {
    int regno;
    char name[20];
};

int main() {
    struct student s[3];
    int key, i;

    for (i = 0; i < 3; i++) {
        scanf("%d%s", &s[i].regno, s[i].name);
    }

    scanf("%d", &key);

    for (i = 0; i < 3; i++) {
        if (s[i].regno == key) {
            printf("Record Found\n");
            printf("Reg No : %d\n", s[i].regno);
            printf("Name : %s\n", s[i].name);
            return 0;
        }
    }

    printf("Record Not Found\n");

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

printf "101 Arun\n102 Kumar\n103 Ravi\n" > index.txt

read -p "Register Number: " key

grep "^$key" index.txt || echo "Record Not Found"
```

## Sample Input

```text
101 Arun
102 Kumar
103 Ravi
102
```

## Sample Output

```text
Record Found
Reg No : 102
Name : Kumar
```
