---
description: Principal component analysis
coverY: 0
---

# PCA

In the last chapter we explained what projection is, and in this chapter we will explain what PCA is.



In the previous chapter, I explained how to generate a Gaussian two-dimensional distribution:

```python
import numpy as np
import matplotlib.pyplot as plt

# Set a random seed
# So the result of each run is the same
np.random.seed(42)

mu = [0, 0]
sigma = [ [10, 8], [8, 10] ]
point = np.random.multivariate_normal(mu, sigma, 1000)

plt.scatter( point[ :, 0 ], point[ :, 1 ],
             alpha = 0.5
             )

plt.show()
```

![Two-dimensional Gaussian distribution of 1000 points](<../.gitbook/assets/image (18).png>)

We now make a straight line and draw the projection of each point to this straight line:

```python
import numpy as np
import matplotlib.pyplot as plt

# Set a random seed
# So the result of each run is the same
np.random.seed(42)

mu = [0, 0]
sigma = [ [10, 8], [8, 10] ]
point = np.random.multivariate_normal(mu, sigma, 1000)

plt.scatter( point[:,0], point[:,1],
             alpha = 0.5
             )



x = np.arange(-12, 12, 0.1)
y = 2 * x
plt.plot(x, y, lw=3, c='#ff7f0e')



plt.xlim(-12, 12)
plt.ylim(-12, 12)

plt.show()
```

![Draw a straight line](<../.gitbook/assets/image (16).png>)

Because 1000 points are too dense, I reduced the number of points to 200 and made some beautifications on the interface:

```python
import numpy as np
import matplotlib.pyplot as plt

# Set a random seed
# So the result of each run is the same
np.random.seed(42)

mu = [0, 0]
sigma = [ [10, 8], [8, 10] ]
point = np.random.multivariate_normal(mu, sigma, 200)

plt.scatter( point[:,0], point[:,1],
             alpha = 0.3 )



x = np.arange(-12, 12, 0.1)
y = 2 * x
plt.plot(x, y, lw=3, c='#ff7f0e')

a = np.array([x[0], y[0]])
for i in range(point.shape[0]):
    b = point[i,:]
    projection = a * np.dot(b, a) / np.linalg.norm(a)**2
    plt.plot( [b[0], projection[0]],
              [b[1], projection[1]],
              c='#2ca02c', alpha=0.5 )

plt.axis('square')
plt.xlim(-12, 12)
plt.ylim(-12, 12)

plt.show()
```

![projection](<../.gitbook/assets/image (19).png>)

We can change the slope of this line, and the result of the projection will change accordingly, for example:

```python
y = -x
```

![Result 1](<../.gitbook/assets/image (15).png>)

```python
y = x
```

![Result 2](<../.gitbook/assets/image (17).png>)

We call the result above as result 1, and the result below as result 2.

I now want to compress this two-dimensional Gaussian distribution into one-dimensional data. Do you think I keep the projection of result 1 more reflecting the real situation or the projection of keeping result 2 more reflecting the real situation?

Our data is a positive correlation (x increases with y will also increase), if we keep the result 1, then the data becomes a negative correlation, then the second result is more representative.

So does the projection of result 2 best reflect the characteristics of the data?

We can rotate this line to make the projection of each point more dispersed on this line. When we adjust to a certain position, these points reach the most dispersed, then this is the best position.

There are some complicated mathematical algorithms involved, and I won’t describe them here. Those who are interested can read the description of PCA in the machine learning book.

Let's talk about how to use python's sklearn library to instantiate PCA.

{% embed url="https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html" %}
instruction
{% endembed %}

```python
import numpy as np
import matplotlib.pyplot as plt

# Set a random seed
# So the result of each run is the same
np.random.seed(42)

mu = [0, 0]
sigma = [ [10, 8], [8, 10] ]
point = np.random.multivariate_normal(mu, sigma, 200)

plt.scatter(point[:,0], point[:,1])



from sklearn.decomposition import PCA

pca_clf = PCA(n_components = 2)
pca_clf.fit(point)
print(pca_clf.explained_variance_ratio_)

pca_data = pca_clf.fit_transform(point)
print(pca_data)

plt.scatter(pca_data[:,0], pca_data[:,1])

plt.show()
```

![Drawing result](<../.gitbook/assets/image (11).png>)

```python
[0.89874751 0.10125249]

[[-2.08302664e+00 -2.28111353e-01]
 [-2.69843058e+00  2.12801965e+00]
 [ 1.01615694e+00 -3.96801699e-01]
 [-6.66173935e+00  1.10171260e+00]
 [ 2.02621253e+00  6.90889329e-01]
 [ 1.98528998e+00 -7.34692054e-01]
 [-1.02907466e+00 -2.74976196e+00]
 [ 7.33561835e+00 -9.28392805e-01]
 [ 4.32790039e+00  3.43406757e-01]
 [ 3.85719196e+00 -2.09341737e+00]
 [-6.19495530e+00 -3.07965098e-01]
 ...
```

In this program, I used sklearn's pca function to perform principal component analysis on the data.

The input data is two-dimensional, and PCA model analyzes two-dimensional (you can only analyze and output one-dimensional, n\_components = 2 can be changed to n\_components = 1, and the reduction of n\_components will only reduce the dimensionality of the output result, but it will not change the result Value)

Then use this model to fit\_transform the two-dimensional Gaussian distribution data and plot it.

The blue point in the above figure is the original data, and the orange point is the data after PCA.

In the orange data, the x-axis is its principal component, and the y-axis is its second component.

<mark style="color:purple;">**You will find that the working method of PCA is to rotate the coordinate axis to a certain angle, so that the data can be displayed as much as possible on the new coordinate axis of this angle.**</mark>

Let's look at the output of the command line:&#x20;

The content of the first line is: \[0.89874751 0.10125249], This is the output of the line of code print(pca\_clf.explained\_variance\_ratio\_).&#x20;





















## Statistics

Start time of this page: January 3, 2022

Completion time of this page: January 5, 2022
