---
description: Prime Number Algorithm
coverY: 0
---

# Judging prime numbers

Prime numbers are very important in computer science. In the famous RSA protocol, it is done by factoring large integers. Its difficulty determines the reliability of the RSA algorithm.

In Goldbach's conjecture, the calculation of prime numbers is also very important. In future section, we will study how to prove Goldbach's conjecture on finite sets.

## what is prime number

The opposite of prime numbers is composite numbers.

A prime number refers to a number that is factored. If the factor is only 1 and itself, then the number is a prime number.

For example, the smallest prime number and the only even prime number is 2, because 2=1\*2, only 1 and itself are factors.

Then 3 and 5 and 7 and 11 are also prime numbers.

We see 4=2\*2, so 4 is a sum, then there are 6, 8, 9, 10, 12 and so on.

According to the above method, it is easy to write a program to calculate the prime numbers:

## first try

In the first attempt we didn't consider efficiency, we just wrote a program that would work.

```python
def prime_detect_v1(num):
    for i in range(2, num):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

for i in range(2, 20):
    print(i, end='\t')
    print(prime_detect_v1(i))
```

The program is very simple. If a number is not divisible by all numbers less than itself, then the number is a prime number, otherwise a composite number.

```python
2	prime number
3	prime number
4	composite number
5	prime number
6	composite number
7	prime number
8	composite number
9	composite number
10	composite number
11	prime number
12	composite number
13	prime number
14	composite number
15	composite number
16	composite number
17	prime number
18	composite number
19	prime number
>>> 
```

We simply run it and the program is correct.

## second attempt

In the first attempt we only considered correctness, this version we consider efficiency:

The most time-consuming thing in determining prime function is the loop. If we can reduce the number of loops, then the efficiency of our program can increase.

If there is a number 29, and we want to determine whether it is a prime number or not, do we need to try from 2 all the way to 28? No, because if numbers up to (square 29)+1 are not divisible by 29, then neither can numbers over (square 29)+1.

```python
def prime_detect_v1(num):
    for i in range(2, num):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

import math

def prime_detect_v2(num):
    for i in range( 2, int(math.sqrt(num))+1 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

for i in range(2, 30):
    print(i, end='\t')
    # print(prime_detect_v1(i))
    print(prime_detect_v2(i))
```

```python
2	prime number
3	prime number
4	composite number
5	prime number
6	composite number
7	prime number
8	composite number
9	composite number
10	composite number
11	prime number
12	composite number
13	prime number
14	composite number
15	composite number
16	composite number
17	prime number
18	composite number
19	prime number
20	composite number
21	composite number
22	composite number
23	prime number
24	composite number
25	composite number
26	composite number
27	composite number
28	composite number
29	prime number
>>> 
```

Such a method reduces a considerable amount of computation.

## third attempt

The second attempt reduced the computational load by a considerable amount, so can we go further?

YES!

We know that all even numbers except 2 are not prime numbers, so it is very simple, we can exclude all even numbers except 2.

```renpy
def prime_detect_v1(num):
    for i in range(2, num):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

import math

def prime_detect_v2(num):
    for i in range( 2, int(math.sqrt(num))+1 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

def prime_detect_v3(num):
    if num == 2:
        return 'prime number'
    if num % 2 == 0:
        return 'composite number'
    for i in range( 3, int(math.sqrt(num))+1, 2 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

for i in range(2, 30):
    print(i, end='\t')
    # print(prime_detect_v1(i))
    # print(prime_detect_v2(i))
    print(prime_detect_v3(i))
```

```python
2	prime number
3	prime number
4	composite number
5	prime number
6	composite number
7	prime number
8	composite number
9	composite number
10	composite number
11	prime number
12	composite number
13	prime number
14	composite number
15	composite number
16	composite number
17	prime number
18	composite number
19	prime number
20	composite number
21	composite number
22	composite number
23	prime number
24	composite number
25	composite number
26	composite number
27	composite number
28	composite number
29	prime number
>>> 
```

But since 2 is also the first number to be tested if you follow the normal process, this method does not change that much. Using this method reduces the amount of computation by about half.

## fourth attempt

In the third attempt, we ruled out all multiples of 2, so can we do the same for multiples of 3? Of course it is possible.

Any natural number can always be expressed in one of the following six forms: 6n, 6n+1, 6n+2, 6n+3, 6n+4, 6n+5 (n=0,1,2...)

We can find that, apart from 2 and 3, only numbers of the form 6n+1 and 6n+5 can be prime numbers. And if numbers of the form 6n+1 and 6n+5 are not prime numbers, their factors will also contain numbers of the form 6n+1 or 6n+5, so the following algorithm can be obtained:

```python
def prime_detect_v1(num):
    for i in range(2, num):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

import math

def prime_detect_v2(num):
    for i in range( 2, int(math.sqrt(num))+1 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

def prime_detect_v3(num):
    if num == 2:
        return 'prime number'
    if num % 2 == 0:
        return 'composite number'
    for i in range( 3, int(math.sqrt(num))+1, 2 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

def prime_detect_v4(num):
    if num == 2 or num == 3:
        return 'prime number'
    if num % 6 != 1 and num % 6 != 5:
        return 'composite number'
    for i in range( 5, int(math.sqrt(num))+1, 6 ):
        if num % i == 0 or num % (i + 2) == 0:
            return 'composite number'
    return 'prime number'

for i in range(2, 50):
    print(i, end='\t')
    # print(prime_detect_v1(i))
    # print(prime_detect_v2(i))
    # print(prime_detect_v3(i))
    print(prime_detect_v4(i))

```

```python
2	prime number
3	prime number
4	composite number
5	prime number
6	composite number
7	prime number
8	composite number
9	composite number
10	composite number
11	prime number
12	composite number
13	prime number
14	composite number
15	composite number
16	composite number
17	prime number
18	composite number
19	prime number
20	composite number
21	composite number
22	composite number
23	prime number
24	composite number
25	composite number
26	composite number
27	composite number
28	composite number
29	prime number
30	composite number
31	prime number
32	composite number
33	composite number
34	composite number
35	composite number
36	composite number
37	prime number
38	composite number
39	composite number
40	composite number
41	prime number
42	composite number
43	prime number
44	composite number
45	composite number
46	composite number
47	prime number
48	composite number
49	composite number
>>> 
```

This approach has reached the limit of artificial optimization, so we will not use the same method to optimize this program (you can add 5 or 7 optimization algorithms, but these optimizations decrease marginally as the number increases, and the code changes It is too complicated, so I will not continue to use this method to optimize)

## fifth attempt

The previous algorithm has reached the limit of optimization, so if we want to continue to optimize the program, we can only change the algorithm.

There are three different measures of <mark style="color:blue;">**Labor complexity**</mark> and <mark style="color:orange;">**space complexity**</mark> and <mark style="color:green;">**time complexity**</mark> in the program.

<mark style="color:blue;">**Labor complexity**</mark> <mark style="color:blue;"></mark><mark style="color:blue;">refers to the labor cost of writing a program. The simpler the program, the lower the labor complexity, and vice versa.</mark>

<mark style="color:blue;">We use python because the</mark> <mark style="color:blue;"></mark><mark style="color:blue;">**Labor complexity**</mark> <mark style="color:blue;"></mark><mark style="color:blue;">of python is very low, so many python programs do not care so much about the time complexity or space complexity, because in scientific research, most programs do not run many times, and the length of time to write code is long. Much larger than the running time, and writing the program quickly is the most important.</mark>

<mark style="color:orange;">**Space complexity**</mark> <mark style="color:orange;"></mark><mark style="color:orange;">refers to the memory and disk size occupied by a program. The larger the space complexity, the larger the disk and memory size occupied by the program.</mark>

<mark style="color:green;">**Time complexity**</mark> <mark style="color:green;"></mark><mark style="color:green;">refers to the length of the running time of the program. In theory, we can calculate the time complexity of the program running (check algorithm books for details, and mathematics is not explained here). However, due to the multi-level cache mechanism of the computer and the connection mechanism of the memory, the time complexity is complicated. It is difficult to predict correctly (we are only predicting a trend), so the time complexity of a program is often calculated by running the program thousands of times (most programs run for a very short time, and the measured results are inaccurate) and measure the actual time divided by number of times the programming runs.</mark>

































## Statistics

Start time of this page: February 2, 2022

Completion time of this page: February 4, 2022
