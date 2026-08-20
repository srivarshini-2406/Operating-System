# EXPERIMENT 6

## Description

Mutual exclusion using semaphore in C and a lock-file mechanism in Bash.

## C Program

```c
#include <stdio.h>
#include <unistd.h>
#include <semaphore.h>
#include <sys/mman.h>
#include <sys/wait.h>

int main() {
    sem_t *s = mmap(
        NULL,
        sizeof(sem_t),
        PROT_READ | PROT_WRITE,
        MAP_SHARED | MAP_ANONYMOUS,
        -1,
        0
    );

    sem_init(s, 1, 1);

    if (fork() == 0) {
        sem_wait(s);

        printf("Child entering critical section\n");
        sleep(1);
        printf("Child leaving critical section\n");

        sem_post(s);
        return 0;
    }

    sem_wait(s);

    printf("Parent entering critical section\n");
    sleep(1);
    printf("Parent leaving critical section\n");

    sem_post(s);

    wait(NULL);
    sem_destroy(s);

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

lock=/tmp/oslab.lock

while [ -e "$lock" ]
do
    sleep 1
done

touch "$lock"

echo "Entering Critical Section"

sleep 2

echo "Leaving Critical Section"

rm -f "$lock"
```

## Sample Input

```text
No input required.
```

## Sample Output

```text
Child entering critical section
Child leaving critical section
Parent entering critical section
Parent leaving critical section
```
