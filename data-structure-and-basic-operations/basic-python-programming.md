---
coverY: 0
---

# basic python programming

```python
print('12345')

a = 1 + 2
b = a
print(b)
```

Python is a simple and convenient language. If you want to program in python, you first need to create a new notepad file and change the suffix to .py. In this way, you have created a new python script, and then you only need to write the python code into this script file to run it.

For example, the result of running the above code is:

```python
12345
3
>>> 
```

## tab

In C or C++ or Java, logic uses curly braces ({}) to enclose a block of code. In python, use tab, if you don't use tab correctly, you will get an error.

```python
add_sum = 0
for i in range(10):
    add_sum += i
    print(add_sum)
```

The above for loop code block is **grouped** using tab indentation.

If you don't use tab, then python will pop up a prompt box to report an error before running.

The result of the above code is:

```python
0
1
3
6
10
15
21
28
36
45
>>> 
```

This is the program to solve 0+1+2+3+4+5+6+7+8+9.

```python
add_sum = 0
for i in range(10):
    add_sum += i
print(add_sum)
```

If you use the above code, then the for loop only includes the code to solve the sum, not the printing code. The printing code is outside the loop, so it will only be printed once, which is the final result:

```parigp
45
>>> 
```

## python line / block

Each instruction in python is called a line of python.

Each of the following sentences is a python line.

```python
print('12345')

a = 1 + 2

b = a

print(b)
```

In C or C++ or Java, a semicolon (;) is required at the end of each statement, but not in python, but if you add a semicolon, no error will be reported.

```python
>>> print('12345');
12345

>>> a = 1 + 2;

>>> b = a;

>>> print(b);
3
>>> 
```



Each paragraph of code indented with tabs is called a python block.

```python
for i in range(10):
    add_sum += i
```

The above is a python code block composed of a for loop.

```python
def fib(n):
    if n <= 2:
        return 1
    else:
        return fib(n-1)+fib(n-2)

for i in range(1, 10):
    print(i, fib(i))
```

Above are two python code blocks, above is a python function code block, below is a python for loop code block.

These two python code blocks can output the results of the first 9 items of the Fibonacci sequence.

```python
1 1
2 1
3 2
4 3
5 5
6 8
7 13
8 21
9 34
>>> 
```



When writing programs, we should make the function of each code block clear, so that our programming will be more efficient with less effort.

## Blank line

Blank lines that you can use in python make your program more legible. Normally blank lines are used between two code blocks, you can blank one or more lines to make the division before the code block clearer.

```python
def fib(n):
    if n <= 2:
        return 1
    else:
        return fib(n-1)+fib(n-2)

# The blank lines above separate the code blocks
for i in range(1, 10):
    print(i, fib(i))
```

{% hint style="danger" %}
<mark style="color:red;">**Don't abuse blank lines as it will make your code fragmented!**</mark>
{% endhint %}

## python comments

When programming, we write a lot of code, and we may confuse the meaning of the code ourselves. So comments are very important.

When we check the previous program, it will be very convenient if there are comments (explaining the meaning of code and variables).

There are three ways to comment in python:

```python
# name of student

name = 'tom'
```

The pound sign (#) is a comment method that comes with python, and the content after # will be automatically skipped by the program (these comments are for humans, and the machine does not need to understand the meaning)

```python
'name of student'
"name of student"

name = 'tom'
```

The second way of commenting is to write a string, which is not assigned to any variable and has no meaning. The python garbage collection system will recycle this string, so writing it this way will not put a memory load on the python program.

The contents of the string have no effect on the program, so this method is used as a comment in many languages (such as cmd, bash, VB)

```python
'''
name of student
a string stored in mysql
'''
"""
name of student
a string stored in mysql
"""

name = 'tom'
```

The way of three quotation marks can also be used for python comments. Similarly, the three quotation marks are a string, but it is not assigned to any variable, so this string will not affect the operation of the program, and the garbage collection system of python will recycle it. This string, so there is no need to consider the memory impact of this string.

The advantage of using triple quotes over pound signs and single quotes is that triple quotes support multiple lines, so you can write multi-line comments.



```python
####################
# Fibonacci
####################
def fib(n):
    if n <= 2:
        return 1
    else:
        return fib(n-1)+fib(n-2)
```

You can use the above methods to make your comments more prominent.

## operator

### arithmetic operators

Python provides operators for various calculations:

```python
>>> 1 + 2
3
# The addition operator can compute addition

>>> 1 - 3
-2
# The subtraction operator can compute the subtraction

>>> 1 / 3
0.3333333333333333
# The division operator computes division 
# (unlike C, python can generate decimals automatically)

>>> 7 * 8
56
# The multiplication operator calculates multiplication 
# (python supports large number operations, 
# you don't need to worry about overflow)

>>> 5 % 2
1
# Use percent sign for remainder

>>> 25 // 3
8
>>> -25 // 3
-9
# 25/3=8.333, // is the round down operator

>>> 2 ** 10
1024

>>> 
```















## Statistics

Start time of this page: January 11, 2022

Completion time of this page: January 11, 2022
