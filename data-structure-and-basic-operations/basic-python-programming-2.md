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



### Recursive execution of functions

Nesting yourself inside a function allows the function to run recursively:

```python
def add(num):

    print(num)
    
    if num > 10:
        # end the func
        return
    
    add(num + 1)



add(0)
```

This function calls itself internally, so the execution process of this function will become more complicated. The following is the result of running the above code:

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
10
11
>>> 
```

return is used to end the function, so when the return is reached, the function ends. This function increments the result by 1 each time until the result is greater than 10 and exits the function and ends the program.



The most classic example of recursion is the Fibonacci sequence.

The first and second numbers in the Fibonacci sequence are 1, and the third number is equal to the sum of the first and second numbers. The fourth number is equal to the sum of the second and third numbers. And so on, each term is equal to the sum of the previous two.

We can write a simple function to calculate the N-th term of the Fibonacci sequence:

```python
def fib(n):
    if n <= 2:
        return 1
    else:
        return fib(n-1)+fib(n-2)



print(fib(10))
```

Got the following result:

```python
55
>>> 
```



Of course, we can also write a loop to calculate the first 10 items of the Fibonacci sequence:

```python
def fib(n):
    if n <= 2:
        return 1
    else:
        return fib(n-1)+fib(n-2)



for i in range(10):
    print(fib(i))
```

The result obtained is as follows (the first row is the result of N=0)

```python
1
1
1
2
3
5
8
13
21
34
>>> 
```

Unfortunately, solving the Fibonacci sequence recursively is the most computationally expensive method, and the most computationally efficient method is the mathematical formula method, followed by the round-robin method.

If you calculate the 100th term of the Fibonacci sequence recursively, you may wait hours without results.

You will find that recursion is complex and error prone, and we will cover it in a separate chapter later.

## Statistics

Start time of this page: January 12, 2022

Completion time of this page: January 12, 2022
