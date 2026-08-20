# EXPERIMENT 9

## Description

Thread creation and concurrent execution using POSIX threads.

## C Program

```c
#include <stdio.h>
#include <pthread.h>
#include <unistd.h>

void *run(void *arg) {
    for (int i = 1; i <= 5; i++) {
        printf("Thread %ld: %d\n", (long)arg, i);
        sleep(1);
    }

    return NULL;
}

int main() {
    pthread_t t1, t2;

    pthread_create(&t1, NULL, run, (void *)1);
    pthread_create(&t2, NULL, run, (void *)2);

    pthread_join(t1, NULL);
    pthread_join(t2, NULL);

    printf("All Threads Completed\n");

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

f() {
    for i in 1 2 3 4 5
    do
        echo "Thread $1: $i"
        sleep 1
    done
}

f 1 &
f 2 &

wait

echo "All Threads Completed"
```

## Sample Input

```text
No input required.
```

## Sample Output

```text
Thread 1: 1
Thread 2: 1
Thread 1: 2
Thread 2: 2
...
All Threads Completed
```
