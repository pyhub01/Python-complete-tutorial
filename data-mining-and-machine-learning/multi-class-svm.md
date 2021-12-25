---
description: Expansion of the two classification problem
coverY: 0
---

# Multi-class SVM

In real life, most problems are multi-categorized, For example, the iris data set contains three types of data.

Another example is:

```python
from tensorflow.keras.datasets import mnist

(x_train, y_train), (x_test, y_test) = mnist.load_data()

import matplotlib.pyplot as plt

for i in range(1, 21):
    plt.subplot(4, 5, i)
    plt.imshow(x_train[i])
    plt.title('label={}'.format(y_train[i]))
    plt.axis('off')

plt.tight_layout()
plt.show()
```

![mnist data set, handwritten digit recognition](<../.gitbook/assets/image (12).png>)

The mnist data set is a handwritten digit recognition data set, which is much larger than the iris data set. We will often use this data set later.

For example, the handwritten number 4, the mnist data set contains thousands of data of handwritten 4.

![Handwriting 4](<../.gitbook/assets/image (7) (1).png>)

There are 10 kinds of handwritten numbers, so we need to classify these 10 kinds of numbers, but SVM can only classify two kinds of data at a time, what should we do?

### Strategy 1: One-to-many

For example, we firstly classify 0 from 10 handwritten digits: we classify 0 into one category, and the remaining 123456789 into another category to construct an svm. Then we classify 1 from 10 handwritten digits: we divide 1 into one category, and the remaining 023456789 into another category, and so on, until we separate all 10 categories.

The advantage of this is that for the k classification problem, we only need to construct k svms, and the amount of calculation is small. Of course, the disadvantage is obvious, that is, the accuracy rate is relatively low.

### Strategy 2: One-to-One

We perform SVM on any two classes: 0 and 1, 0 and 2, 0 and 3, 0 and 4, 0 and 5, 0 and 6, 0 and 7, 0 and 8, 0 and 9, 1 and 2, 1 and 3, 1 and 4, . . . , 8 and 7, 8 and 8, 8 and 9.

Afterwards, voting is used in these SVMs to determine which category an area belongs to.

In this way, we need to build k\*(k-1)/2 SVMs, which is a considerable computational overhead, especially when the number of categories is large. The characteristics of SVM predestined that SVM is difficult to perform multi-process calculation (SVM is difficult to calculate in parallel). We can only use one core of the CPU to run one SVM, so large calculations are often fatal. (It takes several hours to complete the classification)

The accuracy of this method is very good, so python's svm uses this method by default.

### Strategy 3: Hierarchical Support Vector Machine

The hierarchical classification method first divides all categories into two sub-categories, and then further divides the sub-categories into two sub-categories, and so on until a single category is obtained.

This method will be covered later in the graph theory chapter.

### Other strategies

Directed acyclic graph SVM and error correction coding SVMs which perform binary coding on categories are also implementation methods, but they are rarely used, so the analysis is not carried out.

{% hint style="success" %}
<mark style="color:green;">**good news**</mark>

The svm in the sklearn library implements one-to-one svm as built-in, so you only need to send the category into it and it will work normally!
{% endhint %}

## Test multi-class SVM on mnist

```python
from tensorflow.keras.datasets import mnist

(x_train, y_train), (x_test, y_test) = mnist.load_data()

# flatten
x_train = x_train.reshape( x_train.shape[0], -1 )
x_test = x_test.reshape( x_test.shape[0], -1 )

# reduce data size
train_set_size = 1000
x_train = x_train[ :train_set_size, : ]
y_train = y_train[ :train_set_size ]

test_set_size = 20
x_test = x_test[ :test_set_size, : ]



from sklearn import svm
import numpy as np

clf = svm.SVC( kernel = 'linear' )
clf.fit( x_train, y_train )

print('train finished!')
print()

x_pred = clf.predict( x_test )

print('x_pred[ :20 ] =', x_pred[ :test_set_size ])
print('y_test[ :20 ] =', y_test[ :test_set_size ])
```

First, we first read the mnist data set. The dimensions of the mnist data set are:

```python
>>> x_train.shape
(60000, 28, 28)
>>> y_train.shape
(60000,)

>>> x_test.shape
(10000, 28, 28)
>>> y_test.shape
(10000,)
>>> 
```

So we need to flatten the data into one dimension(as SVM can only process 1D data), because the SVM calculation is very slow, so I only take 1000 handwritten digits of total 60000 as the training set, and 20 handwritten digits of total 10000 as the test set. Then use the training set to train our linear SVM model, and finally use our linear SVM to predict our test set.

The results of the program are as follows:

```python
train finished!

x_pred[ :20 ] = [7 2 1 0 4 1 4 9 2 9 0 6 9 0 1 5 9 7 3 4]
y_test[ :20 ] = [7 2 1 0 4 1 4 9 5 9 0 6 9 0 1 5 9 7 3 4]
>>> 
```



## Statistics

Start time of this page: December 20, 2021

Completion time of this page: December 28, 2021
