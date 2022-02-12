---
description: Receiver Operating Characteristic Curve
coverY: 0
---

# ROC and AUC

Receiver Operating Characteristic Curve (ROC) originated in World War II.

![radar](<../.gitbook/assets/image (21) (1) (1).png>)

Radar can detect objects. Radar was not very accurate during World War II, so the difference between an eagle and an airplane is not very big.

Whether the object on the radar is an eagle or an airplane can only be judged by the radar soldier.

Some radar soldiers are more sensitive and mistake the eagle for an aircraft.

Some radar soldiers are less sensitive and mistake an aircraft for the eagle.

This is very troublesome, so scientists have developed a method that allows radar soldiers, whether sensitive or not, to correctly identify radar objects.

The method used is Receiver Operating Characteristic Curve.

Let's use sklearn to give an example:

{% embed url="https://scikit-learn.org/stable/auto_examples/model_selection/plot_roc.html" %}
sklearn
{% endembed %}

```python
import numpy as np
import matplotlib.pyplot as plt

from sklearn.model_selection import train_test_split

from sklearn import svm, datasets
from sklearn.metrics import roc_curve, auc

from tensorflow.keras.utils import to_categorical



# import iris data
iris = datasets.load_iris()
x = iris.data
y = iris.target

# The error rate of the iris data set is too low,
# add some random numbers to increase the error rate
n_samples, n_features = x.shape
x = np.c_[ x, np.random.randn(n_samples, 200 * n_features) ]

# shuffle and split training and test sets
x_train, x_test, y_train, y_test = train_test_split( x, y, test_size = 0.5 )



# Learn to predict each class against the other
clf = svm.SVC( kernel = 'linear', probability = True )
clf.fit( x_train, y_train )

y_pred = clf.predict_proba( x_test )
y_real = to_categorical( y_test )



# Compute ROC curve and ROC area for each class
fpr = dict()
tpr = dict()
roc_auc = dict()

n_classes = len(np.unique(y))

for i in range(n_classes):
    fpr[i], tpr[i], _ = roc_curve( y_real[:, i], y_pred[:, i] )
    roc_auc[i] = auc( fpr[i], tpr[i] )



plt.plot( fpr[0], tpr[0], color = 'darkorange', lw = 2, label = 'ROC curve (area = %0.2f)' % roc_auc[0] )
plt.plot( [0, 1], [0, 1], color = 'navy', lw = 2, linestyle = '--' )
plt.xlim( [0.0, 1.0] )
plt.ylim( [0.0, 1.05] )

plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.title('Receiver operating characteristic example')

plt.legend(loc = 'lower right')
plt.show()
```

The results obtained are as follows:

![ROC and AUC](<../.gitbook/assets/image (10) (1).png>)

In the ROC curve, the horizontal axis is False positive, and the vertical axis is True positive. It can be seen that the ROC curve is a chart for discussing Positive.

The area under the yellow curve is AUC (area under curve). The larger the area, the better the model.

The blue dotted line refers to: If the model is random (50% correct). So any meaningful model should be above the blue dotted line.

## How is the ROC curve drawn?

The drawing of ROC curve requires the probability of model prediction. For example:

```python
pred = [0.2, 0.3, 0.8, 0.4, 0.7, 0.1, 0,  1,  0.5]
true = [1  , 1  , 1  , 0,   0,   0,   0,  0,  0  ]
```

pred is the probability of each test set sample predicted by the model, and true is the actual label of this test set sample.

First, we need to arrange the tags of pred according to size:

```python
pred = [1,  0.8, 0.7, 0.5, 0.4, 0.3, 0.2, 0.1, 0]
true = [0,  1  , 0  , 0  , 0  , 1  , 1  , 0  , 0]
```

Then the position of true needs to be changed with pred.

We define a threshold, such as 0.5. We think that if this threshold is exceeded, the record corresponding to pred is 1, and if it is less than the threshold, the corresponding record is 0.

Then the corresponding label of pred should be: (maximum likelihood)

```python
pred  = [1,  0.8, 0.7, 0.5, 0.4, 0.3, 0.2, 0.1, 0]
label = [1,  1  , 1  , 1  , 0  , 0  , 0  , 0  , 0]
true  = [0,  1  , 0  , 0  , 0  , 1  , 1  , 0  , 0]
```

If label and true are the same, we draw one unit upward, if label and true are different, we draw one unit to the right.

![ROC](<../.gitbook/assets/image (6).png>)

From this we can draw the ROC curve of this model.

We can see that this model is a bad model, because this model has a lower accuracy than random.

In other words, if we believe the prediction results of this model in reverse, we will have better accuracy.😅



Because ROC curve drawing only considers True positive and False positive, so if the number of positive and negative in a sample is different, ROC can still reflect the effect of the model well.

Back to our radar soldier issue:

We prepare 50 radar images, which may contain eagles or airplanes. Then let the radar soldier to distinguish, the radar soldier will give the probability result of the eagle or the aircraft, we use the result given by the radar soldier to compare with the real label to draw the Receiver Operating Characteristic Curve.

In this way, the data of each radar soldier can draw his own Receiver Operating Characteristic Curve. From the curve, we can see the area under curve of each radar soldier. The larger the indicator, the better.

From this curve, we can also have a basic judgment on whether the radar soldier is more sensitive (easy to think of a bird as an airplane) or less sensitive (easy to think of an airplane as a bird).

ROC curve is one of the most widely used model evaluation methods. There are many applications in psychology, genetic biology, product quality, etc.

## Statistics

Start time of this page: December 30, 2021

Completion time of this page: January 4, 2022
