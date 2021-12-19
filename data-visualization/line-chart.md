---
description: line chart
---

# 4 line chart

The line chart is to use lines to represent data. It is generally used to see the trend of the data, whether it is a positive ratio (increasing) or an inverse ratio (decreasing)

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
