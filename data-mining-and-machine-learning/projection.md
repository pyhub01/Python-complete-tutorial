---
description: projection in math
coverY: 0
---

# projection

![orthogonal projection](<../.gitbook/assets/image (11) (1).png>)

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.array( [1, -2] )
y = np.array( [2, 4] )

a = x * np.dot(x, y) / np.linalg.norm(x)**2
b = y - a

plt.plot( [0, x[0]],
          [0, x[1]], lw = 5 )
plt.plot( [0, y[0]],
          [0, y[1]], lw = 5 )

plt.plot( [0, a[0]],
          [0, a[1]] )
plt.plot( [0, b[0]],
          [0, b[1]] )

plt.axis('square')
plt.xlim(-3, 5)
plt.ylim(-3, 5)
plt.show()
```

As shown in the figure, this program draws the projection and parallel lines of the orange vector on the blue vector.

Projection is a very important content in machine learning and data mining.

## Statistics

Start time of this page: December 29, 2021

Completion time of this page: December 31, 2021
