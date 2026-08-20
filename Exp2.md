# EXPERIMENT 2

## Description

Basic arithmetic and number-manipulation programs: sum of odd numbers, arithmetic calculator, largest digit, and reverse of a number.

## C Program

```c
#include <stdio.h>

int main() {
    int n, i, sum = 0, num, digit, largest = 0, rev = 0, a, b;
    char op;

    printf("Enter n: ");
    scanf("%d", &n);

    for (i = 1; i <= n; i++)
        if (i % 2)
            sum += i;

    printf("Sum of odd numbers = %d\n", sum);

    printf("Enter two numbers and operator: ");
    scanf("%d %d %c", &a, &b, &op);

    if (op == '+')
        printf("Result = %d\n", a + b);
    else if (op == '-')
        printf("Result = %d\n", a - b);
    else if (op == '*')
        printf("Result = %d\n", a * b);
    else if (op == '/')
        printf("Result = %d\n", a / b);

    printf("Enter number: ");
    scanf("%d", &num);

    int temp = num;

    while (temp > 0) {
        digit = temp % 10;

        if (digit > largest)
            largest = digit;

        rev = rev * 10 + digit;
        temp /= 10;
    }

    printf("Largest digit = %d\n", largest);
    printf("Reverse = %d\n", rev);

    return 0;
}
```

## Bash Program

```bash
#!/bin/bash

read -p "Enter n: " n

sum=0

for ((i=1; i<=n; i+=2))
do
    ((sum+=i))
done

echo "Sum of odd numbers = $sum"

read -p "Enter number: " num

rev=$(echo "$num" | rev)

echo "Reverse = $rev"
```

## Sample Input

```text
10
5 3 +
4821
```

## Sample Output

```text
Sum of odd numbers = 25
Result = 8
Largest digit = 8
Reverse = 1284
```
