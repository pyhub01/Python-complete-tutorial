---
coverY: 0
---

# some additions

## assignment symbol

```python
>>> a = 4
>>> a += 3
>>> a
7
>>> 
```

a += 3 and a = a + 3 have the same meaning. This is an auto-increment operation.

Unlike C++ or Java, there is no such way as a++ in python, if you want a to increment by 1, then you need a += 1

All operators support auto-increment:

```python
>>> a = 4

>>> a %= 2
>>> a
0

>>> a += 3
>>> a
3

>>> a -= 5
>>> a
-2

>>> a /= 4
>>> a
-0.5

>>> a *= 10
>>> a
-5.0

>>> a //= 6
>>> a
-1.0

>>> 
```

## if \_\_name\_\_ == '\_\_main\_\_':

```python
if __name__ == '__main__':
    print('hello world')
```

In Python, a <mark style="color:red;">**.py**</mark> file is a module. In general, the module name is the file name.

**\_\_name\_\_** holds the current module name. When the module is run directly, the module name is **\_\_main\_\_**.

So, **if \_\_name\_\_ == '\_\_ main\_\_':** means: when the module is run directly, the code block below this line will be run; when the module is imported (import), the code block will not be run.



So in the main file, **if \_\_name\_\_ == '\_\_main\_\_':** should be added, and all your execution code should be placed under this condition. Because it makes the program more concise.

So in the package file, **if \_\_name\_\_ == '\_\_main\_\_':** is not necessarily required, you can add the statement that tests the function in the package file to this condition to test the correctness of the package, but when the main program calls this package file, these test statements will not be executed.

## Statistics

Start time of this page: February 2, 2022

Completion time of this page: February 9, 2022
