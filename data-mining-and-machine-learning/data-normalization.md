---
description: Preparation before machine learning
coverY: 0
---

# Data normalization

Data normalization is very important. This is the preparatory work before machine learning.

Suppose we have two sets of data, one is height in cm, and the other is gender (male is 1, female is 0)

The height of an adult is 160cm to 180cm, so if we do not normalize, then the height with a larger value will be considered very important by the machine, and the gender with a value of only 0-1 will be considered very unimportant by the machine.

But in fact, the average height of men is higher than the average height of women, which is exactly the opposite of the results obtained by the model. So data normalization is very important.

There are many data normalization schemes, each of which has a different focus. Today only two schemes are introduced, and these two schemes are the most widely used.

## <mark style="color:purple;">**Max min normalization**</mark>

```python
import numpy as np

def minmax_normalization(data):
    return (data-np.min(data)) / (np.max(data)-np.min(data))

data = [160,159,168,172,190,186,178]
print('minmax_normalization:')
print(minmax_normalization(data))
```















## Statistics

Start time of this page: January 6, 2022

Completion time of this page: January 7, 2022
