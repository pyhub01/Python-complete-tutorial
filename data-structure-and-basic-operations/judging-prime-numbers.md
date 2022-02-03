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























## Statistics

Start time of this page: February 2, 2022

Completion time of this page: February 4, 2022
