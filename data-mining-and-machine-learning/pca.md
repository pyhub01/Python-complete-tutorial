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













## Statistics

Start time of this page: January 3, 2022

Completion time of this page: January 5, 2022
