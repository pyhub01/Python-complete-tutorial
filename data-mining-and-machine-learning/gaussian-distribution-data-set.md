---
description: test dataset
coverY: 0
---

# Gaussian distribution data set

I introduced some data sets before, but in many cases we need higher-dimensional data or we need lower-dimensional data. Sometimes we need data with a certain degree of relevance, so things like the iris data set cannot Meet our needs.

The Gaussian distribution is also called the normal distribution, and it is the most common distribution in our lives.

So when we encounter a model with an unknown distribution, we can use the normal distribution to fit this model. It can be fitted correctly in most cases.

![Gaussian distribution (normal distribution)](<../.gitbook/assets/image (15).png>)

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

![Plot three sigma normal distribution curves.](<../.gitbook/assets/image (16).png>)

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

![Two-dimensional normal distribution](<../.gitbook/assets/image (17).png>)

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

![Two independent two-dimensional Gaussian distributions are marked with different colors](<../.gitbook/assets/image (16) (1).png>)











## Statistics

Start time of this page: January 3, 2022

Completion time of this page: January 3, 2022
