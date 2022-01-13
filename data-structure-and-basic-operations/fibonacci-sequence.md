---
coverY: 0
---

# Fibonacci sequence

In a previous lesson I explained how to use recursion to calculate the Fibonacci sequence:

```python
def fib(n):
    if n <= 2:
        return 1
    else:
        return fib(n-1) + fib(n-2)



for i in range(1, 11):
    print(fib(i))
```

The result obtained is as follows:

```python
1
1
2
3
5
8
13
21
34
55
>>> 
```

## What is Fibonacci?

In the Middle Ages, Fibonacci discovered an interesting mathematical problem, if we start with a pair of bunnies, it will take a month for the pair to grow up, after which they will breed to produce another pair of bunnies. The pair of bunnies will then spend a month growing up, and the larger rabbit will continue to breed the bunnies as they grow older. Fibonacci assumes that rabbits don't die, so there is a Fibonacci model:

![Fibonacci Rabbit Problem](<../.gitbook/assets/image (17).png>)

The first and second numbers in the Fibonacci sequence are 1, and the third number is equal to the sum of the first and second numbers. The fourth number is equal to the sum of the second and third numbers. And so on, each term is equal to the sum of the previous two.

















## Statistics

Start time of this page: January 13, 2022

Completion time of this page: January 13, 2022
