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
# The two * are power operators, which can calculate exponentiation.

>>> 
```

### comparison operator

Comparison operators are used to compare the size of numeric values.

```python
>>> i = 5
# variable equals to 5

>>> i < 3
False
# Is the variable less than 3? False

>>> i > 2
True
# Is the variable greater than 2? True

>>> i == 5
True
# Is the variable equal to 5? Yes

>>> i != 5
False
# Is the variable not equal to 5? False

>>> i >= 5
True
# Is the variable greater than or equal to 5? Yes

>>> i <= 3
False
# Is the variable less than or equal to 3? No

>>> 
```

### assignment operator

Like C++, python supports assignment to self-increment operations:

```python
>>> test = 4
>>> test = test + 5
>>> test
9

>>> test_1 = 4
>>> test_1 += 5
>>> test_1
9

>>> 
```

You will find that **i=i+5** and **i+=5** mean the same thing.



All operations support the increment operator:

```python
>>> i = 1
>>> i += 1
>>> i
2

>>> i -= 3
>>> i
-1

>>> i *= 5
>>> i
-5

>>> i /= 2
>>> i
-2.5

>>> i **= 9
>>> i
-3814.697265625

>>> 
```

The new version of python also has a walrus operator (:=), but this operator is rarely used in companies and programs for compatibility reasons, so I won't discuss it here.

### bitwise operators

Bit manipulation is very important in computers, but it doesn't seem to be very important in a high level language like python.

Basic bitwise operations include AND, OR, NOT, XOR, left shift, right shift, etc.:

```python
>>> a = 0b100011101
>>> b = 0b101101111

>>> a & b
269
>>> bin(a & b)
'0b100001101'

>>> 
```

Use the 0b keyword to enter a binary number (each digit can only have 0 or 1)

Use the bin function to output numbers in binary form.

Binary AND means that if the corresponding position of the two numbers is 1, then output 1, if not, then output 0.



Binary or means that if the corresponding positions of the two numbers are not both 0, then output 1, if both are 0, output 0.

```python
>>> bin(a | b)
'0b101111111'
>>> 
```



Binary XOR means that if the corresponding positions of the two numbers are the same, the output is 0, and if the corresponding positions of the two numbers are different, the output is 1.

```python
>>> bin(a ^ b)
'0b1110010'
>>> 
```



Binary not means that if the original value of this bit is 1, output 0, if the original value of this bit is 0, output 1.

Because the highest bit of a is 1, a will become a negative number after the NOT gate operation.

```python
>>> bin(~a)
'-0b100011110'
>>> 
```



Shifting left and right in the computer is to move the number to the left or right in the memory. Because the computer is binary, the whole number is doubled by moving one bit to the left (equivalent to multiplying by 2), and moving one bit to the right. The whole number is reduced by a factor of two (equivalent to dividing by 2)

```python
>>> a << 4
4560

>>> a >> 2
71

>>> a
285

>>> 
```



It is not recommended to use bit operations here, because using bit operations in python is not really bit operations, and does not save time than operations such as addition and subtraction (it does save time in Java)

And bit operations have potential hidden dangers (data overflow problem)

Here are the classic usage of bit manipulation:

```python
>>> a = 5
>>> b = 17

>>> a = a ^ b
>>> b = a ^ b
>>> a = a ^ b

>>> a
17
>>> b
5

>>> 
```

The value of two numbers can be simply exchanged through the XOR operation. In Java, you need to pay special attention to the problem of incorrect results caused by negative overflow, but there is no such problem in python.

{% hint style="danger" %}
<mark style="color:red;">**It's worth noting that using the above code in python is not a good option as native code in python is more efficient.**</mark>
{% endhint %}

```python
>>> a
17
>>> b
5

>>> a, b = b, a
# best efficient of switching 2 number

>>> a
5
>>> b
17

>>> 
```

Because python stores label pointers, swapping two numbers using python's built-in method is just exchanging the pointers of the two numbers, which is more efficient.

### Logical Operators

```python
>>> True and False
False
>>> True and True
True
>>> False and False
False
>>> False and True
False

>>> 0 and 30
0
>>> 1 and 30
30
>>> 5 and 30
30

>>> 
```

Logical operations are Boolean algebra operations. There are only two kinds of values in Boolean algebra, True and False. where False is 0 and True can be any value other than 0.

The above code is the usage of AND.

```
>>> True or False
True

>>> not False
True
>>> not True
False
>>> 
```

The above is the usage of or and not.

### member operator

```python
>>> 5 in [1,2,3,4,5]
True
>>> 6 in [1,2,3,4,5]
False

>>> 5 not in [1,2,3,4,5]
False
>>> 6 not in [1,2,3,4,5]
True
```

The member operators are in and not in, which respectively measure whether one content is in another.

## Statistics

Start time of this page: January 11, 2022

Completion time of this page: January 11, 2022
