---
description: test dataset
coverY: 0
---

# Gaussian distribution data set

I introduced some data sets before, but in many cases we need higher-dimensional data or we need lower-dimensional data. Sometimes we need data with a certain degree of relevance, Sometimes we need a specific sample size, so things like the iris data set cannot Meet our needs.

The Gaussian distribution is also called the normal distribution, and it is the most common distribution in our lives.

So when we encounter a model with an unknown distribution, we can use the normal distribution to fit this model. It can be fitted correctly in most cases.

![Gaussian distribution (normal distribution)](<../.gitbook/assets/image (15) (1).png>)

The above is the probability distribution function(PDF) of the normal distribution.

This curve is very similar to a bell, so the normal distribution curve is also called a bell curve.

```python
import numpy as np
import matplotlib.pyplot as plt

sigma = 1
mu = 2

x = np.arange(mu - 3*sigma, mu + 3*sigma, 0.01)
y = 1/(2*np.pi*sigma**2) * np.e**(-(x-mu)**2/(2*sigma**2))

plt.plot(x, y)
plt.grid()
plt.show()
```

![Plot three sigma normal distribution curves.](<../.gitbook/assets/image (16) (1).png>)

If you have taken a course in probability and statistics, then you should know some properties of the normal distribution: for example, we have a class, and the height of the students in the class conforms to the normal distribution. We know that the average height of the students in the class is 170cm, and the standard deviation (sigma) of the students' height in the class is 5cm, then according to the nature of the normal distribution: 68.3% of the students are between 165-175cm in height. 95.5% of students are between 160-180cm tall. 99.7% of the students are between 155-185cm in height.

About the one-dimensional normal distribution, you know these is enough in using.

Let's see the two-dimensional normal distribution:

```python
import numpy as np
from scipy.stats import multivariate_normal

import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D



clf = multivariate_normal( mean = [0, 0],
                           cov = [ [1, 0], [0, 1] ]
                           )

div = 100
XX, YY = np.meshgrid(np.linspace(-2, 2, div), np.linspace(-2, 2, div))
Z = clf.pdf( np.dstack([XX, YY]) ).reshape(div, div)



fig = plt.figure()
ax = Axes3D(fig, auto_add_to_figure = False)
fig.add_axes(ax)

ax.plot_surface( XX, YY, Z,
                 rstride = 1, cstride = 1,
                 cmap = 'rainbow',
                 )

ax.set_xlabel('x')
ax.set_ylabel('y')
ax.set_zlabel('z')
plt.show()
```

![Two-dimensional normal distribution](<../.gitbook/assets/image (17) (1) (1) (1) (1).png>)

You will find that the profile of a two-dimensional normal distribution is a one-dimensional normal distribution (we just finished)

The mean represents the position of the image, the front is the x coordinate, and the back is the y coordinate.

If I modify the mean, the following changes will occur: (pay attention to the coordinate axis does not change)

```python
clf = multivariate_normal( mean = [0.5, 1],
                           cov = [ [1, 0], [0, 1] ]
                           )
```

![Modify mean](<../.gitbook/assets/image (4).png>)

You will find that when I modify the mean, there is no change in the graph itself, only the position of the graph has changed.

When I modify the covariance matrix, the changes are more diverse. There are three situations:

```python
clf = multivariate_normal( mean = [0, 0],
                           cov = [ [3, 0], [0, 1] ]
                           )
```

![Modify the upper left coefficient of the covariance matrix](<../.gitbook/assets/image (13) (1).png>)

When I modify the upper left coefficient of the covariance matrix, you will find that the distribution becomes wider on the x-axis.

```python
clf = multivariate_normal( mean = [0, 0],
                           cov = [ [1, 0], [0, 3] ]
                           )
```

![Modify the lower right coefficient of the covariance matrix](<../.gitbook/assets/image (17) (1) (1) (1).png>)

When I modify the lower right coefficient of the covariance matrix, you will find that the distribution becomes wider on the y-axis.

{% hint style="danger" %}
**\[ \[1, 2],**

&#x20; **\[3, 4] ]**

The above is a 2\*2 matrix.

Among them, 1 is the upper left corner element, 4 is the lower right corner element, 1 and 4 are the main diagonal of this matrix, and 2 and 3 are the sub-diagonal of this matrix.

In the covariance matrix, the value of the side diagonal(2 and 3) is the same. If the value of the sub-diagonal of your covariance matrix is different, an error will be reported.

**The meaning of the covariance matrix: Element 1 represents the variance of the x-axis, element 4 represents the variance of the y-axis,  and elements 2 and 3 represent the covariance of x and y.**

The larger the variance, the more scattered the data, and the smoother the PDF image should be. The smaller the variance, the more concentrated the data, and the steeper the PDF image should be.



**Also need to pay attention: the covariance cannot be greater than the variance, because this is impossible.**
{% endhint %}



```python
clf = multivariate_normal( mean = [0, 0],
                           cov = [ [1, 0.2], [0.3, 1] ]
                           )
```

If the subdiagonal values of the covariance matrix are different, then python will report an error.

```python
Traceback (most recent call last):
  File "xxx.py", line 9, in <module>
    clf = multivariate_normal( mean = [0, 0],
  File "C:\Users\Administrator\AppData\Local\Programs\Python\Python38\lib\site-packages\scipy\stats\_multivariate.py", line 361, in __call__
    return multivariate_normal_frozen(mean, cov,
  File "C:\Users\Administrator\AppData\Local\Programs\Python\Python38\lib\site-packages\scipy\stats\_multivariate.py", line 736, in __init__
    self.cov_info = _PSD(self.cov, allow_singular=allow_singular)
  File "C:\Users\Administrator\AppData\Local\Programs\Python\Python38\lib\site-packages\scipy\stats\_multivariate.py", line 160, in __init__
    raise ValueError('the input matrix must be positive semidefinite')
ValueError: the input matrix must be positive semidefinite
>>> 
```

Let's try to modify the subdiagonal of the covariance matrix:

```python
clf = multivariate_normal( mean = [0, 0],
                           cov = [ [1, 0.8], [0.8, 1] ]
                           )
```

![Related variables](<../.gitbook/assets/image (17) (1) (1).png>)

When the subdiagonal of the covariance matrix is 0, the two variables are not correlated, that is to say, when x changes, y is not affected, and the two variables x and y are independent of each other.

When the subdiagonal line of the covariance matrix is not 0, the two variables are correlated, which means that when x changes, y will change with x, and there is a correlation between the two variables x and y, which is shown in the graph: the graph is no longer parallel to the x-axis or the y-axis, but has an angle with the x-axis and the y-axis. .

```python
import numpy as np
import matplotlib.pyplot as plt

mu = [0, 0]
sigma = [ [20, 5], [5, 10] ]
point = np.random.multivariate_normal(mu, sigma, 1000)

plt.scatter( point[:,0], point[:,1],
             alpha = 0.5
             )

plt.show()
```

Use this simple code to plot a two-dimensional Gaussian distribution:

![Two-dimensional Gaussian distribution](<../.gitbook/assets/image (22).png>)

When constructing the data set, we need some sampling points. At this time, we can use Gaussian distribution to generate these points.

The graphs we have drawn before are all PDFs, which are probability distribution graphs. In this graph, a larger value means that the probability of a point in this place is greater, and a smaller value means that the probability of a point in this place is smaller.

So when we draw 1000 points, more points will fall in places with higher probability, and fewer points will fall in places with lower probability.

The above is the method of constructing a two-dimensional Gaussian distribution.

But in most cases, our model requires multiple types of labeled point sets for training, so the following program can generate multiple labeled point sets:

```python
import numpy as np
import matplotlib.pyplot as plt

mu_1 = [0, 0]
sigma_1 = [ [20, 5], [5, 1] ]
point_1 = np.random.multivariate_normal(mu_1, sigma_1, 1000)

mu_2 = [0, 5]
sigma_2 = [ [20, 5], [5, 1] ]
point_2 = np.random.multivariate_normal(mu_2, sigma_2, 1000)

points = np.vstack( (point_1, point_2) )
labels = np.hstack( ([0]*1000, [1]*1000) )

plt.scatter( points[:,0], points[:,1],
             c = labels,
             alpha = 0.5
             )

plt.show()
```

The two independent Gaussian distributions drawn are shown in the figure:

![Two independent two-dimensional Gaussian distributions are marked with different colors](<../.gitbook/assets/image (16) (1) (1).png>)

In the above figure, we draw a two-dimensional point set of multiple labels, and different labels with different colors.

In actual machine learning and deep learning, generating a Gaussian point set is a very good method to test the model, so you should be proficient in the method of generating a Gaussian point set.

This chapter describes the method of generating a two-dimensional Gaussian point set. In the following chapters, if necessary, I will explain the method of generating a higher-dimensional Gaussian point set.

## Statistics

Start time of this page: January 3, 2022

Completion time of this page: January 3, 2022
