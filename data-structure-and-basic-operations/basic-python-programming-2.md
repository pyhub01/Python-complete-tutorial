---
description: function
coverY: 0
---

# basic python programming 2

In today's content I will introduce functions.

```python
def test_func(name):
    print('name = ', name)
    return 'test func ok!'
```

A function should contain three parts: the function header, which should contain the def keyword, the function name, and the variables that need to be passed in.

The inside of the function should contain what the function needs to write in.

The final return result (this is optional, you can do not write it)

A function written in python will not be executed. The following statement will execute this function.

```python
>>> res = test_func('tom')
name =  tom

>>> res
'test func ok!'

>>> 
```



Functions do not necessarily need to pass in variables:

```python
def hello():
    print('hello world')
```

The above is the definition of the function, and the following is the execution statement of the function:

```python
>>> hello()
hello world
>>> 
```

You will find that functions do not necessarily need to pass in parameters and return values.



```python
def hello():
    print('hello world')
    return 'this is a return'
    print('123')

# execute the func
hello()
```

The execution result is as follows:

```python
hello world
>>> 
```

You will find that when the function executes to the return statement, the following content will not be executed (when the function executes to the return statement, the function has ended)























## Statistics

Start time of this page: January 12, 2022

Completion time of this page: January 12, 2022
