---
description: The most important concept
coverY: 0
---

# Mean median mode

## mean

The mean(average) is to add all the values together and divide by the number of samples.

Calculating the average in python is very simple.

We only need to use numpy's built-in functions.

```python
data = [
    0, 0, 1, 2, 2, 2, 2, 3, 3, 3,
    5, 5, 5, 5, 5, 5, 5, 5, 5, 5,
    7, 7, 8, 8, 9, 9, 9, 10
    ]

print('data = ', end='')
print(data)
print()

import numpy as np

print('mean = ', end='')
print(np.mean(data))
```

The results of this program are as follows:

```python
data = [
    0, 0, 1, 2, 2, 2, 2, 3, 3, 3, 
    5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 
    7, 7, 8, 8, 9, 9, 9, 10
    ]

mean = 4.821428571428571
>>> 
```

## median

The number in the middle of the sorted data is median.

We still use the previous data, this time we will find the median.

We only need to use numpy's built-in functions.

```python
data = [
    0, 0, 1, 2, 2, 2, 2, 3, 3, 3,
    5, 5, 5, 5, 5, 5, 5, 5, 5, 5,
    7, 7, 8, 8, 9, 9, 9, 10
    ]

print('data = ', end='')
print(data)
print()

import numpy as np

print('mean = ', end='')
print(np.mean(data))

print('median = ', end='')
print(np.median(data))
```

The results of this program are as follows:

```python
data = [0, 0, 1, 2, 2, 2, 2, 3, 3, 3, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 7, 7, 8, 8, 9, 9, 9, 10]

mean = 4.821428571428571
median = 5.0
>>> 
```

## mode

Mode refers to the number with the largest number in a set of data.

Obviously, the most numerous number in this set of data is 5.

The solution of the mode is also very simple. We only need to use scipy's built-in functions.

```python
data = [
    0, 0, 1, 2, 2, 2, 2, 3, 3, 3,
    5, 5, 5, 5, 5, 5, 5, 5, 5, 5,
    7, 7, 8, 8, 9, 9, 9, 10
    ]

print('data = ', end='')
print(data)
print()

import numpy as np

print('mean = ', end='')
print(np.mean(data))

print('median = ', end='')
print(np.median(data))

from scipy import stats

print('mode = ', end='')
print(stats.mode(data)[0][0])
```

The result of the operation is:

```python
data = [0, 0, 1, 2, 2, 2, 2, 3, 3, 3, 5, 5, 5, 5, 5, 5, 5, 5, 5, 5, 7, 7, 8, 8, 9, 9, 9, 10]

mean = 4.821428571428571
median = 5.0
mode = 5
>>> 
```

## Summarize

Mean median mode is the most commonly used method in data analysis. They are very simple but also very effective. All data mining engineers should keep in mind and master these three methods.

## Statistics

Start time of this page: December 20, 2021

Completion time of this page: December 20, 2021
