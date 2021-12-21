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





































## Statistics

Start time of this page: December 21, 2021

Completion time of this page: December 21, 2021
