---
description: Parallel coordinates
coverY: 0
---

# 4 Parallel coordinates

When you are trying to find the relationship between multiple variables, Parallel coordinates is a good choice.

Parallel coordinates can clearly observe the distribution of data. For example, we can run Parallel coordinates on the iris data set.

![iris dataset with parallel\_coordinates](<../.gitbook/assets/image (9).png>)

```python
import seaborn
iris_data = seaborn.load_dataset('iris')
 
from pandas.plotting import parallel_coordinates
parallel_coordinates( iris_data, 'species',
                      color = ('#55627080', '#4ECDC480', '#C7F46480')
                      )

import matplotlib.pyplot as plt
# Mandatory run display interface
plt.show()
```

After running Parallel coordinates on the iris data set, you can clearly observe the relationship between sepal\_length, sepal\_width, petal\_length, petal\_width and species.&#x20;

For example, the petal\_length of virginica is larger than the other two varieties. Then when you encounter an iris plant in the future, if its petal\_length is larger, then it is likely to be a virginica.

## Statistics

Start time of this page: December 20, 2021

Completion time of this page: December 20, 2021
