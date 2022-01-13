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



### recursive method

Obviously this problem can be solved recursively: if we want to know the value of the fourth term of the Fibonacci sequence, we need to know the value of the second and third terms of the Fibonacci sequence, where the second term is 1 , if we want to know the value of the third term of the Fibonacci sequence, we need to know the value of the first and second terms of the Fibonacci sequence, both of which are 1. So the recursive program is written:

```python
def fib(n):
    if n <= 2:
        return 1
    else:
        return fib(n-1) + fib(n-2)
```

I can add an output to the function so we can see exactly what terms are computed by the function:

```python
def fib(n):
    print(n, end=' ')
    if n <= 2:
        return 1
    else:
        return fib(n-1) + fib(n-2)
```

We can call fib(10) to see exactly how much this function computes:

```python
10 9 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 
2 3 2 1 4 3 2 1 2 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 
8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 2 3 
2 1 4 3 2 1 2 
>>> 
```

We can call fib(15) to see exactly how much this function computes:

```python
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 
1 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 
2 1 2 3 2 1 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 
3 2 1 2 3 2 1 4 3 2 1 2 9 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 
2 3 2 1 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 
5 4 3 2 1 2 3 2 1 10 9 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 
3 2 1 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 
4 3 2 1 2 3 2 1 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6
 5 4 3 2 1 2 3 2 1 4 3 2 1 2 11 10 9 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 
 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 7 6 5 4 3 2 1 2 3 
 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 
 4 3 2 1 2 3 2 1 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 9 8 7 6 5 4 3 2 1 2 3 
 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 7 6 5 
 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 12 11 10 9 8 7 6 5 4 3 2
  1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2
   7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 8 7 6 5 4 3 2 1 
   2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 
   9 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 
   2 3 2 1 4 3 2 1 2 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 
   1 10 9 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3
    2 1 2 3 2 1 4 3 2 1 2 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2
     3 2 1 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 
     3 2 1 2 3 2 1 4 3 2 1 2 13 12 11 10 9 8 7 6 5 4 3 2 1 2 3 2 1 4 
     3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 7 6 5 4 
     3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 8 7 6 5 4 3 2 1 2 3 2 
     1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 9 8 
     7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 2 
     3 2 1 4 3 2 1 2 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 
     1 10 9 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4
      3 2 1 2 3 2 1 4 3 2 1 2 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2
       1 2 3 2 1 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 
       6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 11 10 9 8 7 6 5 4 3 2 1 2 3 2 1 
       4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 7 6 
       5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 8 7 6 5 4 3 2 1 
       2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 4 3 2 1 2 3 2 1 4 3 2 
       1 2 9 8 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 3 2 1 2 3 2 1 6 5 
       4 3 2 1 2 3 2 1 4 3 2 1 2 7 6 5 4 3 2 1 2 3 2 1 4 3 2 1 2 5 4 
       3 2 1 2 3 2 1 
>>> 
```

The complexity of computing the Fibonacci sequence using recursion increases exponentially with N! This is something that computers can't afford! If we want to calculate the 100th term of the Fibonacci sequence, then I am afraid it will take several days and dozens of gigabytes of memory.



Python provides us with a way to quickly make recursion easy: lru\_cache, which can memorize results that have already been generated, so that Python doesn't need to recompute what has already been computed. Especially useful when generating Fibonacci sequences:

```python
from functools import lru_cache

@lru_cache
def fib(n):
    print(n, end=' ')
    if n <= 2:
        return 1
    else:
        return fib(n-1) + fib(n-2)
```

We still run fib(15), and the output is very different from before:

```python
15 14 13 12 11 10 9 8 7 6 5 4 3 2 1 
>>> 
```

Because of the memory with lru\_cache, the program only calculates 15 times, and the result of each time is saved in a python array.



We can even calculate the 100th term of the Fibonacci sequence like this, which must be an astronomical number:

```python
from functools import lru_cache

@lru_cache
def fib(n):
    print(n, end=' ')
    if n <= 2:
        return 1
    else:
        return fib(n-1) + fib(n-2)



print()
print()
print()
print(fib(100))
```

The calculation results are as follows:

```python
100 99 98 97 96 95 94 93 92 91 90 89 88 87 86 85 84 83 
82 81 80 79 78 77 76 75 74 73 72 71 70 69 68 67 66 65 
64 63 62 61 60 59 58 57 56 55 54 53 52 51 50 49 48 47 
46 45 44 43 42 41 40 39 38 37 36 35 34 33 32 31 30 29 
28 27 26 25 24 23 22 21 20 19 18 17 16 15 14 13 12 11 
10 9 8 7 6 5 4 3 2 1 

354224848179261915075
```



We can also try subsequent items, such as the 1000th item, but python has a recursion depth limit, and an error will be reported if this limit is exceeded:

```python
Traceback (most recent call last):
  File "xxx.py", line 20, in <module>
    print(fib(1000))
  File "xxx.py", line 9, in fib
    return fib(n-1) + fib(n-2)
  File "xxx.py", line 9, in fib
    return fib(n-1) + fib(n-2)
  File "xxx.py", line 9, in fib
    return fib(n-1) + fib(n-2)
  [Previous line repeated 509 more times]
RecursionError: maximum recursion depth exceeded
>>> 
```

Use the following statement to set the recursion limit to 10000 so that calculating the 1000th term of the Fibonacci sequence will not exceed the python limit.

```python
import sys
sys.setrecursionlimit(10000)
```

The complete recursive program looks like this:

```python
import sys
sys.setrecursionlimit(10000)

from functools import lru_cache

@lru_cache
def fib(n):
    # print(n, end=' ')
    if n <= 2:
        return 1
    else:
        return fib(n-1) + fib(n-2)

print(fib(1000))
```

The result is a fairly large number:

```python
4346655768693745643568852767504062580256466051737178040248172908953655
5417949051890403879840079255169295922593080322634775209689623239873322
471161642996440906533187938298969649928516003704476137795166849228875
>>> 
```

And you will find that the calculation speed is extremely fast after using lru\_cache, and it basically does not take time.

### loop method

There are three ways to calculate the Fibonacci sequence in python. The circular method ranks in the middle. Whether it is the difficulty of this method or the amount of calculation, the circular method performs well.

```python
def fib(n):
    a = 1
    b = 1
    for _ in range(n-1):
        a, b = b, a + b

    return a



for i in range(1, 11):
    print(fib(i))
```

The above function can calculate the result of the first ten terms of the Fibonacci sequence:

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

In each calculation, b is equal to the sum of the two items, and a is equal to b, so it is like pulling a zipper(Climb up step by step.) to calculate the Fibonacci sequence.

















## Statistics

Start time of this page: January 13, 2022

Completion time of this page: January 13, 2022
