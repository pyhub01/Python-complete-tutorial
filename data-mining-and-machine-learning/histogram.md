---
description: Frequency distribution
coverY: 0
---

# Histogram

The histogram can very vividly show the frequency distribution of data.

For example, the following is the temperature data of a certain place (a total of 100 data, temperature in degrees Celsius)

```python
[27.3 29.5 26.4 24.  26.9 24.7 23.1 28.9 28.2 21.2 24.3 23.7 19.8 25.5
 24.6 16.1 21.9 25.7 25.2 26.1 26.2 24.4 25.8 20.7 22.3 18.9 25.2 27.7
 24.1 22.  26.2 25.5 20.1 24.  22.5 29.9 26.7 25.1 25.  26.7 28.  21.6
 24.5 25.6 22.9 24.5 22.3 21.3 25.1 23.4 18.2 26.5 24.4 26.6 21.6 19.5
 18.2 25.4 25.1 22.6 26.8 24.5 22.1 26.3 27.  24.7 23.5 26.4 24.8 24.6
 24.1 18.8 23.6 20.3 25.3 23.3 20.8 21.7 22.2 25.9 24.2 23.4 23.6 26.1
 24.9 23.7 26.9 20.5 31.1 24.8 29.2 20.8 25.3 23.4 25.7 23.2 28.7 26.
 19.6 25.3]
```

We plot this data into a histogram as shown below:

```python
temperature = [
    27.3, 29.5, 26.4, 24. , 26.9, 24.7, 23.1, 
    28.9, 28.2, 21.2, 24.3, 23.7, 19.8, 25.5,
    24.6, 16.1, 21.9, 25.7, 25.2, 26.1, 26.2, 
    24.4, 25.8, 20.7, 22.3, 18.9, 25.2, 27.7,
    24.1, 22. , 26.2, 25.5, 20.1, 24. , 22.5, 
    29.9, 26.7, 25.1, 25. , 26.7, 28. , 21.6,
    24.5, 25.6, 22.9, 24.5, 22.3, 21.3, 25.1, 
    23.4, 18.2, 26.5, 24.4, 26.6, 21.6, 19.5,
    18.2, 25.4, 25.1, 22.6, 26.8, 24.5, 22.1, 
    26.3, 27. , 24.7, 23.5, 26.4, 24.8, 24.6,
    24.1, 18.8, 23.6, 20.3, 25.3, 23.3, 20.8, 
    21.7, 22.2, 25.9, 24.2, 23.4, 23.6, 26.1,
    24.9, 23.7, 26.9, 20.5, 31.1, 24.8, 29.2, 
    20.8, 25.3, 23.4, 25.7, 23.2, 28.7, 26. ,
    19.6, 25.3
    ]

import matplotlib.pyplot as plt

plt.hist(temperature, bins=20, facecolor='blue', edgecolor='black', alpha=0.7)

plt.xlabel('temperature')
plt.ylabel('frequency')

plt.title('Temperature detection distribution')

plt.show()
```

![Histogram](<../.gitbook/assets/image (10) (1).png>)

From this figure, we can clearly see the distribution of the data.

The temperature in this area is mostly between 24-26 degrees Celsius, which is comfortable. Occasionally there will be some low temperatures, and you need to prepare a few coats to keep warm.

## Statistics

Start time of this page: December 21, 2021

Completion time of this page: December 21, 2021
