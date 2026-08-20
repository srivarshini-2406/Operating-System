# EXPERIMENT 3

## Description

Process creation and basic process management using `fork`, `wait`, and process identification.

## C Program

```c
#include <stdio.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    pid_t p = fork();

    if (p == 0) {
        printf("Child Process: PID=%d\n", getpid());
    }
    else {
        wait(NULL);
        printf("Parent Process: PID=%d\n", getpid());
    }

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

echo "Parent Process: $$"

(
    echo "Child Process: $BASHPID"
) &

wait
```

## Sample Input

```text
No input required.
```

## Sample Output

```text
Child Process: PID=<child_pid>
Parent Process: PID=<parent_pid>
```
