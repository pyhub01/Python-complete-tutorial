---
description: Preparation before machine learning
coverY: 0
---

# Data normalization

Data normalization is very important. This is the preparatory work before machine learning.

Suppose we have two sets of data, one is height in cm, and the other is gender (male is 1, female is 0)

The height of an adult is 160cm to 180cm, so if we do not normalize, then the height with a larger value will be considered very important by the machine, and the gender with a value of only 0-1 will be considered very unimportant by the machine.

But in fact, the average height of men is higher than the average height of women, which is exactly the opposite of the results obtained by the model. So data normalization is very important.

Similarly, data normalization can improve the training speed of the model in deep learning and avoid the problem of gradient dispersion caused by too large data differences.



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

The output result is as follows:

```python
minmax_normalization:
[0.03225806 0.         0.29032258 0.41935484 1.         0.87096774
 0.61290323]
>>> 
```

Maximum and minimum normalization can compress any data to Standardized data between 0-1.&#x20;

The idea is very simple: turn the smallest number in a set of data into 0, the largest number in a set of data into 1, and the other numbers in the data Scale according to the scale of the data.

In actual use, we generally use a function for data preprocessing (operations such as normalization), so the maximum and minimum normalization provided in this article uses a function.

sklearn provides functions to perform data preprocessing and normalization, but because the maximum and minimum normalization is too simple, we can use our own code.

Because numpy supports high-dimensional operations, if you need to normalize two-dimensional or high-dimensional data, this function can complete the task.

{% hint style="success" %}
The maximum and minimum normalization is very simple, and the amount of calculation is small, which can easily handle a large amount of data.

The maximum and minimum normalization does not destroy the data, and the data still maintains the original ratio, so this linear scaling is very suitable for machine learning, deep learning, and data visualization.
{% endhint %}

## <mark style="color:purple;">z-score normalization</mark>

```python
import numpy as np

def minmax_normalization(data):
    return (data-np.min(data)) / (np.max(data)-np.min(data))

def standardization(data):
    mu = np.mean(data, axis=0)
    sigma = np.std(data, axis=0)
    return (data - mu) / sigma

data = [160,159,168,172,190,186,178]

print('minmax_normalization:')
print(minmax_normalization(data))
print()

print('standardization:')
print(standardization(data))
```

The above program contains two kinds of normalization, and the running results are as follows:

```python
minmax_normalization:
[0.03225806 0.         0.29032258 0.41935484 1.         0.87096774
 0.61290323]

standardization:
[-1.1893789  -1.27890205 -0.47319376 -0.11510118  1.4963154   1.13822282
  0.42203768]
>>> 
```

Most of the data in the world conforms to the normal distribution, so if we encounter a data, we can assume that the data conforms to the normal distribution:

The z-score normalization is to turn this normal distribution that we assume into a standard normal distribution. (The normal distribution with mu=0 and gamma=1 is called the standard normal distribution)

{% hint style="success" %}
If your data presents a strong Gaussian distribution, z-score normalization is a good choice. If your data has nothing to do with the Gaussian distribution, then the result of z-score normalization is not very good, you should use the maximum and minimum normalization.

Z-score normalization is not a linear process, and the scale of data is different. So z-score normalization is not very suitable for deep learning.

If your data fits the Gaussian distribution, but this Gaussian distribution is an pressed oblong shape(Like a baguette), then using z-score normalization will speed up the process of deep learning gradient descent and improve the efficiency of gradient descent.
{% endhint %}

## Statistics

Start time of this page: January 6, 2022

Completion time of this page: January 7, 2022
