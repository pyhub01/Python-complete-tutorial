---
description: Print format
coverY: 0
---

# 🚩 fancy print

In order to facilitate the debugging of the program, we write the fancy print function, this function can print the variable name and variable content, so that the output becomes simple and easy to understand.

```python
def fancy_print(name, content):
    print(name, end=' = ')
    print(content)
    print()

a = 5
fancy_print('a', a)

b = list(range(10))
fancy_print('b', b)
```

The output result is as follows.

```python
a = 5

b = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> 
```

In fact, we don't need to write a separate function to solve this problem, we can use the built-in print function of python to solve this problem:

```python
>>> a = 5
>>> print('a =', a)
a = 5

>>> b = 'hello'
>>> print('b =', b)
b = hello
>>> 
```

## Statistics

Start time of this page: December 19, 2021

Completion time of this page: December 19, 2021
