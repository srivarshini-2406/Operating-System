# EXPERIMENT 5

## Description

Inter-process communication using pipes.

## C Program

```c
#include <stdio.h>
#include <unistd.h>
#include <string.h>

int main() {
    int fd[2];
    char msg[] = "Hello from parent";
    char buf[100] = {0};

    pipe(fd);

    if (fork() == 0) {
        close(fd[1]);
        read(fd[0], buf, 99);
        printf("Child received: %s\n", buf);
    }
    else {
        close(fd[0]);
        write(fd[1], msg, strlen(msg) + 1);
    }

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

msg="Hello from parent"

echo "$msg" | while read x
do
    echo "Child received: $x"
done
```

## Sample Input

```text
No input required.
```

## Sample Output

```text
Child received: Hello from parent
```
