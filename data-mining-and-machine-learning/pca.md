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





































## Statistics

Start time of this page: January 3, 2022

Completion time of this page: January 5, 2022
