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

In a computer test, the scores range from 0 to 100. Now the number of people with scores from 60 to 80 is counted. The statistical method is to select the number of people with scores greater than 60 and scores less than 80.
{% endhint %}

<mark style="color:red;">****</mark>

If statements can be nested:





## loops

There are two kinds of loop statements in python, while and for.















## Statistics

Start time of this page: January 13, 2022

Completion time of this page: January 13, 2022
