---
description: basic logic
coverY: 0
---

# basic python programming 3

In today's tutorial I'll cover basic logic and loops:

## Conditional control

The if statement is used for conditional control in python.

```python
for i in range(10):
    print(i, end='\t')
    if i == 3:
        print('this is 3')
    elif i == 5:
        print('this is 5')
    elif i == 7:
        print('this is 7')
    else:
        print('not important')
```

You can see how the if statement is used: first, the if is followed by the judgment condition, and the two = means to judge whether i is equal to 3. If i is equal to 3, then this executes the following code, if i is not equal to three, the following code is not going to be executed.

```python
0	not important
1	not important
2	not important
3	this is 3
4	not important
5	this is 5
6	not important
7	this is 7
8	not important
9	not important
```

elif is the abbreviation of else if. If the statement in if is not executed, then if the condition in elif is true, the statement in elif is executed.

If there is an else statement, the else statement will be executed if the previous conditions are not met.

```python
a = 3

if a == 3:
    print('if')
elif a == 3:
    print('elif')
```

It's worth noting that if and elif will only be executed once.

```python
if
>>> 
```

The following is the simplest form of an if statement:

```python
a = 3

if a == 3:
    print('if')
```

you can add else

```python
a = 3

if a == 3:
    print('if')
else:
    print('other number')
```

So in the if statement, you can just write the if statement, you can also combine if and elif, or you can combine if and else, the most complete if statement includes if, elif and else.



Small exercise: Leap year judgment.

{% hint style="success" %}
<mark style="color:green;">**Determine if a year is a leap year.**</mark>&#x20;

Since 1984, astronomy has adopted the Julian year (not to be confused with the Julian calendar in the calendar) as a unified year time unit, which is specified as an exact 365.25 days, with an error of 1 day every 3000 years compared with the tropical year. In the modern Gregorian calendar, a normal year has 365 days, and a leap year has 366 days.

In the Gregorian calendar, most of the years that are divisible by 4 are leap years, but years that are divisible by 100 but not divisible by 400 are not leap years. For example, 1900 is a normal year, and 2000 is a leap year.
{% endhint %}

```python
for year in [1990, 2000, 2004, 2006, 3000]:
    
    print(year, end='\t')
    
    if year % 4 != 0:
        print('not a leap year!')
    elif year % 100 == 0 and year % 400 != 0:
        print('not a leap year!')
    else:
        print('leap year!')
```

```python
1990	not a leap year!
2000	leap year!
2004	leap year!
2006	not a leap year!
3000	not a leap year!
>>> 
```

The above is a way of writing leap year detection program.

```python
for year in [1990, 2000, 2004, 2006, 3000]:
    
    print(year, end='\t')
    """
    if year % 4 != 0:
        print('not a leap year!')
    elif year % 100 == 0 and year % 400 != 0:
        print('not a leap year!')
    else:
        print('leap year!')
    """
    if year % 400 == 0 or (year % 4 == 0 and year % 100 != 0):
        print('leap year!')
    else:
        print('not a leap year!')
```

We commented out the previous method, and the new method can also judge leap years.

The first method first determines all normal years, and then the remaining years are leap years. The second method first determines all leap years, and then the rest are normal years.

{% hint style="danger" %}
<mark style="color:red;">**The if statement uses Boolean algebra.**</mark>

So when we reverse the logic, we run into the De Morgan formula problem.

A simple example is:

In a computer test, the scores range from 0 to 100. Now the number of people with scores from 60 to 80 is counted. The statistical method is to select the number of people with scores **greater than** 60 **and** scores **less than** 80.

If we want to count people other than the above scores, we need to count the number of people whose scores are **less than or equal to** 60 **or** whose scores are **greater than or equal to** 80.

When reversing the logic, not only reverse the **and** and **or**, but also **reverse the logical sign** (greater than becomes less than or equal, greater than or equal to less than, less than becomes greater than or equal, less than or equal to greater than) This is De Morgan formula.

This is reflected in the above example of judging leap years in ordinary years.
{% endhint %}

<mark style="color:red;">****</mark>

If statements can be nested:

```python
a = 10

if a > 3:
    print('a > 3')
    if a > 5:
        print('a > 5')
        if a > 7:
            print('a > 7')
            if a > 9:
                print('a > 9')
                if a > 11:
                    print('a > 11')
                else:
                    print('a < 11')
```

```python
a > 3
a > 5
a > 7
a > 9
a < 11
>>> 
```

It is possible to use multiple levels of if for nesting, but doing so clutters up the code, so don't do it if it's not necessary.

## loops

There are two kinds of loop statements in python, while and for.

### while loops

For code clarity, the while loop is only used as an infinite loop.

An infinite loop is a loop that does not stop. This loop will continue to run until an error occurs in the program or is terminated manually or a **break** statement is read.

In a computer program, if a program is terminated, the program will return to the operating system, but if there is no operating system in an embedded device or a microcontroller, the program must be written as an infinite loop, otherwise the program in the microcontroller will run away ( go where it shouldn't).

```python
i = 0

while True:
    i += 1
    print(i)
    if i > 10:
        break
```

This is a complete while program. In most cases, while is an infinite loop, and there will be no **break** out of the process.

```python
1
2
3
4
5
6
7
8
9
10
11
>>> 
```

### break

break can terminate the loop. There is usually a judgment condition before the break (otherwise, the loop will be terminated as soon as it reaches the break, and the loop will be meaningless)

Check the program just now, break is executed when i is greater than 10, so when i is equal to 11, that is, when i is greater than 10, the loop is aborted.

### continue

Continue is another loop control condition other than break.

If the program executes to continue, the current round of the loop is terminated and the loop will enter the next round.

```python
for i in range(10):

    if i == 4:
        continue

    print(i)
```

When the program runs to 4, the program enters the continue state, then this round of 4 is skipped, as in the following output.

```python
0
1
2
3
5
6
7
8
9
>>> 
```

### for loops

In order to make the program look simple, in general, the while loop is only used as an infinite loop, and the for loop assumes other loop tasks.

```python
for each in ['a', 'c', 'f', 'k']:
    print(each)
```

```python
a
c
f
k
>>> 
```

You will see that the **for** loop prints each item in the list.



Loops can be controlled more easily with ranges:

```python
for num in range(10):
    print(num)
```

```python
0
1
2
3
4
5
6
7
8
9
>>> 
```

This way we can print out the numbers in the range.



Python is a flexible language, so we can use for to construct arrays:

```python
>>> [i for i in range(10)]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> 
```

We can also add calculations to it:

```python
>>> [i**2 for i in range(10)]
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>>> 
```

Similarly we can construct dictionaries using this method:

```python
>>> {i:i**2 for i in range(10)}
{0: 0, 1: 1, 2: 4, 3: 9, 4: 16, 5: 25, 6: 36, 7: 49, 8: 64, 9: 81}
>>> 
```

A basic operation is: if we need to manually write an FFT (fast Fourier transform) program, then a large amount of sin and cos data needs to be calculated, but we can calculate it in advance and call these data later. Because it takes a lot of time to calculate functions like sin, but it takes almost no time to call, we can do the repeated calculation in advance, so that there is no need to repeat the calculation.

```python
>>> import math
>>> math.sin(1/2*math.pi)
1.0
>>> sin_table = {i/16:math.sin(i/16*math.pi) for i in range(16)}
>>> sin_table
{0.0: 0.0, 0.0625: 0.19509032201612825, 0.125: 0.3826834323650898, 0.1875: 0.5555702330196022, 0.25: 0.7071067811865476, 0.3125: 0.8314696123025452, 0.375: 0.9238795325112867, 0.4375: 0.9807852804032304, 0.5: 1.0, 0.5625: 0.9807852804032304, 0.625: 0.9238795325112867, 0.6875: 0.8314696123025453, 0.75: 0.7071067811865476, 0.8125: 0.5555702330196022, 0.875: 0.3826834323650899, 0.9375: 0.1950903220161286}
>>> 
```

Note that sin and cos in the math library in python use radians, so your data should also be in radians.

The cos table can also be calculated using a similar method.



{% hint style="success" %}
<mark style="color:green;">**After these chapters, you have mastered the Turing-complete python language, and you can start practicing programming!**</mark>
{% endhint %}

## Statistics

Start time of this page: January 13, 2022

Completion time of this page: January 13, 2022
