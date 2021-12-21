---
description: Distance and correlation
coverY: 0
---

# Correlation algorithm

I now have two sets of data. I want to know how they are related. What should I do?

For example, the following two sets of data.

```python
a = [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ]
b = [ 1, 1, 2, 4, 5, 6, 8, 8, 9, 9  ]
```

## Euclidean distance

The simplest thing that can be thought of is distance. If the distance between the two data is very close, then the two data are very close, if the distance between the two data is very far, then the two data are far apart.

```python
import matplotlib.pyplot as plt

a = [1, 2]
b = [5, 4]

plt.plot( [ a[0], b[0] ],
          [ a[1], b[1] ] )

plt.scatter( [ a[0], b[0] ],
             [ a[1], b[1] ] )

plt.xlim(0, 6)
plt.ylim(0, 5)

plt.xlabel('x')
plt.ylabel('y')

plt.title('Euclidean distance')

plt.grid()
plt.show()
```

![Euclidean distance](<../.gitbook/assets/image (3).png>)

The length of the line segment in the figure is the Euclidean distance.

```python
a = [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ]
b = [ 1, 1, 2, 4, 5, 6, 8, 8, 9, 9  ]

dist = 0
for i in range(len(a)):
    dist += (a[i] - b[i]) ** 2
dist = dist ** 0.5

print(dist)
```

The above code is the calculation method of Euclidean distance, and the results obtained are as follows:

```python
2.0
>>> 
```

We can use numpy's own function to calculate Euclidean distance.

```python
import numpy as np

a = np.array( [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ] )
b = np.array( [ 1, 1, 2, 4, 5, 6, 8, 8, 9, 9  ] )

dist = np.linalg.norm( a - b )
print(dist)
```

Can get the same result

```python
2.0
>>> 
```

{% hint style="danger" %}
In particular, linalg is a linear algebra library, we will often use it in subsequent programs.
{% endhint %}

## Cosine distance

The cosine distance can measure the angle between two vectors. If the angle is small, the two vectors are relatively close. If the angle is large, the distance between the two vectors is large.

```python
import matplotlib.pyplot as plt

a = [1, 2]
b = [5, 4]

plt.plot( [ a[0], 0 ],
          [ a[1], 0 ] )

plt.plot( [ 0, b[0] ],
          [ 0, b[1] ], '#1f77b4' ) # color: matplotlib blue

plt.scatter( [ a[0], b[0] ],
             [ a[1], b[1] ] )

plt.xlim(0, 6)
plt.ylim(0, 5)

plt.xlabel('x')
plt.ylabel('y')

plt.title('Cosine distance')

plt.grid()
plt.show()
```

![Cosine distance](<../.gitbook/assets/image (11).png>)

The angle between the two vectors is the cosine distance.

The formula of the cosine distance is very complicated. Fortunately, scipy has created a library for us to calculate the cosine distance, which only needs to be called:

```python
import numpy as np

a = np.array( [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ] )
b = np.array( [ 1, 1, 2, 4, 5, 6, 8, 8, 9, 9  ] )

from scipy.spatial import distance

dist = distance.cosine( a, b )
print(dist)

# The smaller the distance, the higher the similarity
similarity = 1 - dist
print(similarity)
```

It shows that the directionality of these two data is quite consistent.

```python
0.005152370287896502
0.9948476297121035
>>> 
```

{% hint style="success" %}
If the cosine similarity between two vectors is positive, it means that the two vectors are in the same direction (positive correlation). If it is negative, then it means that the two vectors are in opposite directions (negative correlation). The absolute value of the cosine similarity of the two vectors The larger the value, the closer the angle of the two vectors, and the closer the cosine similarity of the two vectors is to 0, indicating that the two vectors are closer to unrelated (perpendicular to each other).
{% endhint %}

## Pearson Correlation Coefficient

Pearson's correlation coefficient is a linear correlation coefficient.

At the end, I will explain the comparison of these types of correlation coefficients with you.

In scipy, there is a Pearson correlation coefficient library, which can be easily used by just calling it.

```python
import numpy as np

a = np.array( [ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 ] )
b = np.array( [ 1, 1, 2, 4, 5, 6, 8, 8, 9, 9  ] )

from scipy.stats import pearsonr

pearsonr = pearsonr(a, b)
print(pearsonr)
```

The output obtained is as follows:

```python
(0.9808651973571281, 5.731479081203351e-07)
>>> 
```

The first of these is the Pearson correlation coefficient

```python
(0.9808651973571281, 5.731479081203351e-07)
>>> pearsonr[0]
0.9808651973571281
>>> 
```

Pearson correlation coefficient can be extracted through index



















## Statistics

Start time of this page: December 21, 2021

Completion time of this page: December 21, 2021
