---
description: Introduction to iris data set
coverY: 0
---

# 3 What is data mining

Data mining is to find out some patterns from the data.



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

In this graph, we will find that when income increases, expenditures will increase accordingly.&#x20;

This is a common sense of life, that is, when we earn more, we are more inclined to consume more, we earn less, we don't have so much money to consume.&#x20;

We can dig out the above content from this data.



This is data mining. We find some patterns hidden in the data, and you will find that python is born for data mining. Then we will explain more in the next chapter.

## Statistics

Start time of this page: December 19, 2021

Completion time of this page: December 19, 2021
