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

### Strategy 1: One-to-many method

For example, if we first classify 0 from 10 handwritten digits, then we classify 0 into one category, and the remaining 123456789 into one category to construct an svm. Then we classify 1 from 10 handwritten digits, then we divide 1 into one category, and the remaining 023456789 into one category, and so on, until we separate all 10 categories.

The advantage of this is that for the k classification problem, we only need to construct k svms, and the amount of calculation is small. Of course, the disadvantage is obvious, that is, the accuracy rate is relatively low.





## Statistics

Start time of this page: December 20, 2021

Completion time of this page: December 28, 2021
