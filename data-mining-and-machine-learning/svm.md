---
description: Support Vector Machines
---

# SVM

Before deep learning became popular on a large scale, support vector machines were the most popular machine learning method.

The support vector machine has a small amount of calculation, so it is still favored by devices that cannot run large memory and high calculation amount.

To illustrate SVM, we use the iris dataset as an example. (For the convenience of explaining the principle, I only extract two categories from it)

For visualization, I compressed the iris data set to two-dimensional data using principal component analysis (PCA).

```python
####################
# read data
####################

f = open('iris.csv', 'r')
lines = f.readlines()

data = []
label = []

for line in lines[ 1: ]:
    line = line.replace('\n', '').split(',')

    # Convert string data into float form
    data.append( list(map(float, line[ :-1 ])) )
    label.append( line[-1] )


# Converted into a numpy array, you can process the data like MATLAB.
import numpy as np

data = np.array(data)
label = np.array(label)



####################
# setosa & versicolor
####################

# Extract only two categories from it
data = data[ label != 'virginica' ]
label = label[ label != 'virginica' ]

# Replace the label with a number
for i in range(len(label)):
    if label[i] == 'setosa':
        label[i] = 0
    else:
        label[i] = 1

# convert string into int
label = label.astype(int) 



####################
# pca
####################

from sklearn.decomposition import PCA

pca = PCA( n_components = 2 ) # 2D data

# fit the model
pca.fit(data) 
print(pca.explained_variance_ratio_)

# transformed data
data = pca.fit_transform(data)



####################
# show data
####################

print('data:')
# View the dimensional information of the data
print(data.shape)
print(data)
print()
print('label:')
print(label.shape)
print(label)

import matplotlib.pyplot as plt

# visualizaion
plt.scatter(data[:, 0], data[:, 1], c = label)

plt.show()
```

![2D-data visualization](<../.gitbook/assets/image (12).png>)











## Statistics

Start time of this page: December 21, 2021

Completion time of this page: December 21, 2021
