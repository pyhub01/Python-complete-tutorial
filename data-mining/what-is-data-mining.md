---
description: Introduction to iris data set
coverY: 0
---

# 3 What is data mining

Data mining is to find some patterns from the data.



For example, here is a piece of data about income and outlay

```python
income = [1200, 1400, 1600, 1800, 2000, 2200, 2400]
outlay = [1000, 1240, 1320, 1500, 1790, 1924, 2218.75]
```

Each income corresponds to an outlay

If we use the following procedure, we can draw a clear diagram of the relationship between income and expenditure:

```python
income = [1200, 1400, 1600, 1800, 2000, 2200, 2400]
outlay = [1000, 1240, 1320, 1500, 1790, 1924, 2218.75]

import matplotlib.pyplot as plt

plt.plot(income, outlay)

plt.title('The relationship between income and outlay')
plt.xlabel('income')
plt.ylabel('outlay')

plt.grid()
plt.show()
```

![The relationship between income and outlay](<../.gitbook/assets/image (3).png>)









## Statistics

Start time of this page: December 19, 2021

Completion time of this page: December 19, 2021
