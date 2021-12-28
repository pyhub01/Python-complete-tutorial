---
description: Slow lookup Data structures
coverY: 0
---

# Data structure without hash table

## <mark style="color:purple;">number</mark>

The number types are divided into the following categories:

```python
>>> type(2)
<class 'int'>

>>> type(2.3)
<class 'float'>

>>> type(True)
<class 'bool'>

>>> type(1+2j)
<class 'complex'>
```

**int** represents an integer number, and **float** represents a floating point number, which is a decimal number. **bool** represents the boolean type, which contains two types of **True** and **False**. The last type is a **complex** number, which contains real and imaginary parts. The unit of imaginary number is represented by j.

We can assign a number to a variable:

```python
>>> a = 2

>>> a
2
```

Enter the variable name after the **>>>** symbol, and the value of the variable can be displayed on the screen, like **>>> a**.

In this case, the value of variable a is 2.

{% hint style="success" %}
<mark style="color:green;">**About variables**</mark>
{% endhint %}

1. The first character must be a letter in the alphabet or an underscore \_.
2. The other parts of the Variable consist of letters, numbers, and underscores.
3. Variable are case sensitive.
4. Variable names should not use Python reserved words.

To explain the firstand second one, for example, **abc** can be a variable name, **\_abc** can also be a variable name, **studnt\_id** can also be a variable name, but <mark style="color:red;">**2021\_weeks**</mark> cannot be a variable name, because a variable name cannot start with a number.

To explain the third point: **time** and **Time** and **TIME** are three different variables, because variable names are case sensitive.

To explain the fourth item, if the variable name is the same as the reserved word in python, then this python reserved word is invalid, which is equivalent to modifying python itself. This is possible, but it is strongly not recommended. Python reserved words can be viewed using the following methods:

```python
>>> import keyword
>>> keyword.kwlist
['False', 'None', 'True', 'and', 'as', 'assert', 'async', 'await', 
'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 
'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 
'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 
'with', 'yield']
>>>
```

{% hint style="success" %}
<mark style="color:green;">**About '='**</mark>
{% endhint %}

In programming languages, **=** means assignment, not equality in mathematics.

For example, a=3 means to assign 3 to a.\
b=a means to assign a to b.\
a=a+1 means to assign a+1 to a, that is, to increase a by 1.

The demonstration program is as follows:

```python
>>> a = 3
>>> a
3
>>> a = a + 1
>>> a
4
>>> b = 5
>>> b
5
>>> b = a
>>> b
4
>>> 
```

## <mark style="color:purple;">string</mark>

```python
>>> 'hello world'
'hello world'
>>> type('hello world')
<class 'str'>
>>> 
```

The string can use single quotation marks ('...') or double quotation marks ("...") to indicate, a multi-line string uses three single quotation marks ("'...''') or three Multiple quotation marks ("""...""") to indicate.

```python
>>> 'hello'
'hello'

>>> "world"
'world'

>>> '''good
morning
'''
'good\nmorning\n'

>>> """
good
night
"""
'\ngood\nnight\n'
```

Among them, \n means newline.

### <mark style="color:orange;">String index</mark>

The string is composed of characters, and the character at the corresponding position can be extracted by the string index. It is important that the string index starts from 0.

For convenience, we use the string '123456' (note: the string in the quotation marks is not a number) to illustrate

```python
>>> test = '123456'
>>> test
'123456'

>>> test[0]
'1'
>>> test[1]
'2'
>>> test[2]
'3'
>>> test[3]
'4'
>>> test[4]
'5'
>>> test[5]
'6'
>>> test[6]
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
    test[6]
IndexError: string index out of range
>>> 
```

We assign the string to a variable, and then index the variable. When the Index is exceeded the length of the string(array out of bounds), python will report an error.

{% hint style="danger" %}
One advantage of using python is that python will report an array out-of-bounds error.

This is not reminded in the C language, C++ and Java. The array beyond the boundary may cause serious consequences, may modify the memory that is not intended to be modified, or leak important data to the hacker.
{% endhint %}

{% hint style="info" %}
<mark style="color:blue;">**Index value can be negative**</mark>
{% endhint %}

Let's still use string '123456' as an example to try what happens with negative indexes:

```python
>>> test = '123456'
>>> test
'123456'

>>> test[-1]
'6'
>>> test[-2]
'5'
>>> test[-3]
'4'
>>> test[-4]
'3'
>>> test[-5]
'2'
>>> test[-6]
'1'
>>> test[-7]
Traceback (most recent call last):
  File "<pyshell#123>", line 1, in <module>
    test[-7]
IndexError: string index out of range
>>> 
```

We found that when a negative number is used as an index value, it will index from the end of the string forward.

When the index exceeds the length of the string, an error will still be reported.

{% hint style="success" %}
<mark style="color:green;">**Indexes are used in python strings, lists, tuples, and sets. The rules for indexing in python are the same.**</mark>
{% endhint %}

### <mark style="color:orange;">**String slice**</mark>

String slicing is very important. When we want to extract the key information of a string, slicing can help us extract part of it:

```python
>>> text = 'name:Tom'
>>> text[5:]
'Tom'
>>> 
```

The string slice is like this: <mark style="color:blue;">**string name**</mark>\*\* \[ <mark style="color:red;">**start position**</mark> : <mark style="color:green;">**end position**</mark> ]\*\*

```python
>>> text = 'name:Tom'
>>> text[2:6]
'me:T'
>>> 
```

When the <mark style="color:red;">**start position**</mark> is empty, it means to start cutting from the beginning of the string:

```python
>>> text = 'name:Tom'
>>> text[:5]
'name:'
>>> 
```

When the <mark style="color:green;">**end position**</mark> is empty, it means to keep to the end of the string:

```python
>>> text = 'name:Tom'
>>> text[5:]
'Tom'
>>> 
```

Python's slicing principle is <mark style="color:red;">**left-closed**</mark> and <mark style="color:green;">**right-opened**</mark>, which means that the <mark style="color:red;">**start position**</mark> is included in the slicing result and the <mark style="color:green;">**end position**</mark> is not included in the splicing result.

An example is:

```python
>>> text = '0123456789'

>>> text[1:3]
'12'
>>> text[:3]
'012'
>>> text[3:]
'3456789'
>>> text[:-1]
'012345678'
>>> text[-3:-1]
'78'
>>> 
```

The elements on the left edge of the slice will be kept, and the elements on the right edge of the slice will be discarded.

{% hint style="success" %}
<mark style="color:green;">**Slices are used in python strings, lists, tuples, and sets. The rules for slicing in python are the same.**</mark>
{% endhint %}

## <mark style="color:purple;">list</mark>

Lists are one of the most commonly used data types in python.

We can creat an empty list in the following two ways.

```python
>>> a = list()
>>> a
[]

>>> b = []
>>> b
[]
>>> 
```

The slice and index of the list are exactly the same as the string, so I won’t repeat them here. I will give a few examples:

```python
>>> a = list(range(10))
>>> a
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> a[0]
0
>>> a[5]
5
>>> a[-1]
9
>>> a[-9]
1
>>> a[-10]
0

>>> a[2:5]
[2, 3, 4]

>>> a[-5:-1]
[5, 6, 7, 8]
>>> 
```

{% hint style="success" %}
<mark style="color:green;">**range(...)**</mark>
{% endhint %}

The range(...) function is one of the most commonly used construction methods in python.

The range function will generate a sequence of numbers:

```python
>>> range(10)
range(0, 10)

>>> list(range(10))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> 
```

Range will generate a range type variable. If you force this range type variable into a list, then you can see the numbers contained in this range.

If you give only one parameter to the range function, then range will generate an integer sequence starting from 0 to this parameter minus 1.

This parameter must be an integer, otherwise an error will be reported.

```python
>>> range(4.5)
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
    range(4.5)
TypeError: 'float' object cannot be interpreted as an integer
>>> 
```

Range can also enter multiple parameters. The first parameter is the start point of the range(included), the second parameter is the end point of the range(not included), and the third parameter is the step length of the range (optional parameter)

```python
>>> list(range(5))
[0, 1, 2, 3, 4]

>>> list(range(10))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> list(range(3, 10))
[3, 4, 5, 6, 7, 8, 9]

>>> list(range(3, 10, 2))
[3, 5, 7, 9]

>>> list(range(10, 3))
[]

>>> list(range(10, 3, -1))
[10, 9, 8, 7, 6, 5, 4]
>>> 
```

The step length can be a negative number, then the sequence is a decreasing sequence, notice that the starting point must be greater than the ending point, otherwise the range function will return an empty list.

{% hint style="success" %}
<mark style="color:green;">**Forced type conversion**</mark>
{% endhint %}

\*\*Forced type conversion \*\*<mark style="color:green;">\*\*\*\*</mark> can convert a data structure of one type into a data structure of another type.

For example, **list(...)** can convert the data type in parentheses to list.

The type(...) function can return the type of a variable.

```python
>>> a = 2
>>> a
2
>>> type(a)
<class 'int'>

>>> a = str(a)
>>> type(a)
<class 'str'>
>>> a
'2'

>>> a = list(a)
>>> type(a)
<class 'list'>
>>> a
['2']
>>> 
```

Let's continue to explain the list:

#### <mark style="color:green;">append</mark>

The most important method in the list is append, This is a way to add variables to the end of the list.

```python
>>> a = []

>>> a.append(1)
>>> a
[1]

>>> a.append(2)
>>> a
[1, 2]

>>> a.append('hello')
>>> a
[1, 2, 'hello']

>>> a.append(['world', 5])
>>> a
[1, 2, 'hello', ['world', 5]]
>>> 
```

We can add any element to the end of the list, including numbers, strings, and even add a list, so that this list is nested into another list, as shown above.

#### <mark style="color:green;">pop</mark>

```python
>>> a = list(range(10))
>>> a
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> a.pop()
9
>>> a
[0, 1, 2, 3, 4, 5, 6, 7, 8]

>>> a.pop(8)
8
>>> a
[0, 1, 2, 3, 4, 5, 6, 7]

>>> a.pop(3)
3
>>> a
[0, 1, 2, 4, 5, 6, 7]

>>> a.pop(5)
6
>>> a
[0, 1, 2, 4, 5, 7]
>>> 
```

pop is one of the classic operations of the stack, which means to remove and output the last element from the stack

We can observe the pop operation from the above example. The pop operation of python also supports popping the element with the corresponding index. For example, pop(8) means popping the element with the index 8. The 8 here does not refer to the 8, but the 9th element (the index is 8)

## <mark style="color:purple;">tuple</mark>

Tuples are almost the same as lists, except that the contents of tuples cannot be changed, so tuples do not have methods such as append or pop that can change its elements.

Tuples are rarely used in python, because although the contents of tuples are immutable, variable names can be reassigned, which also destroys the immutable properties of tuples:

```python
>>> test = (1, 2, 3)
>>> test
(1, 2, 3)

>>> test[0]=5
Traceback (most recent call last):
  File "<pyshell#>", line 1, in <module>
    test[0]=5
TypeError: 'tuple' object does not support item assignment

>>> test = 'another content'
>>> test
'another content'
>>> 
```

Through the above program, you can change the content referred to by the variable name that originally pointed to the tuple.

This also makes tuples meaningless in python.

Unlike in C++:

```cpp
const int a = 3;
a = 5
// C++ does allow this happened
```

## Statistics

Start time of this page: December 19, 2021

Completion time of this page: December 30, 2021
