---
description: Support Vector Machines
coverY: 0
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

\[0.90505321 0.07466183] is the parameter of pca. The first dimension occupies 0.90505321 of the information of all dimensions, and the second dimension occupies 0.07466183 of the information of all dimensions, so the iris data set actually only needs one dimension to retain 0.90505321 Information which is nearly all the information.

```python
[0.90505321 0.07466183]

data:
(100, 2)
[[-1.65441341  0.20660719]
 [-1.63509488 -0.2988347 ]
 [-1.82037547 -0.27141696]
 [-1.66207305 -0.43021683]
 [-1.70358916  0.21574051]
 [-1.29703913  0.67110413]
 [-1.76606724 -0.19879839]
 [-1.58304007  0.05695841]
 [-1.78011362 -0.70206111]
 [-1.59834072 -0.23099112]
 [-1.5040071   0.54413365]
 [-1.56084249 -0.08355705]
 [-1.70082554 -0.36233771]
 [-2.12344152 -0.66329534]
 [-1.68576136  1.05876217]
 [-1.45785007  1.26053039]
 [-1.64475545  0.7077085 ]
 [-1.6210485   0.20442802]
 [-1.21649679  0.79551434]
 [-1.58454944  0.41972344]
 [-1.27971892  0.30138495]
 [-1.53437452  0.34272876]
 [-2.18076848 -0.01038384]
 [-1.25991144  0.02298539]
 [-1.30005525 -0.11101033]
 [-1.42887098 -0.25145471]
 [-1.42938118  0.04344897]
 [-1.53511858  0.26313827]
 [-1.60523766  0.19747386]
 [-1.55958823 -0.29887024]
 [-1.51041248 -0.30800356]
 [-1.38684727  0.31532879]
 [-1.66934352  0.71421048]
 [-1.64262045  0.99304445]
 [-1.59834072 -0.23099112]
 [-1.81020731 -0.06521932]
 [-1.6118795   0.478487  ]
 [-1.59834072 -0.23099112]
 [-1.8838527  -0.61809451]
 [-1.55067433  0.12264059]
 [-1.74034333  0.14789693]
 [-1.70045202 -1.07830004]
 [-1.91747271 -0.4684635 ]
 [-1.37946137  0.11390614]
 [-1.20346821  0.3809399 ]
 [-1.63409572 -0.36669605]
 [-1.53098526  0.41275152]
 [-1.76581214 -0.34625023]
 [-1.53637284  0.47845147]
 [-1.65315915 -0.008706  ]
 [ 2.28000436  0.90198599]
 [ 1.94531662  0.52401592]
 [ 2.47167169  0.74100695]
 [ 1.30393971 -0.69034944]
 [ 2.13185147  0.28128499]
 [ 1.71926659 -0.23066302]
 [ 2.10336394  0.51266789]
 [ 0.38433694 -0.93903186]
 [ 2.0806774   0.42614102]
 [ 1.08603828 -0.58116204]
 [ 0.65780086 -1.19091389]
 [ 1.55632065  0.07342729]
 [ 1.38248373 -0.43021653]
 [ 2.03914265  0.08639985]
 [ 0.88772911 -0.13916986]
 [ 1.93892988  0.65757723]
 [ 1.72001065 -0.15107253]
 [ 1.3206313  -0.19665446]
 [ 2.04868517 -0.35550349]
 [ 1.14902656 -0.46152682]
 [ 2.14436985  0.16161423]
 [ 1.41408418  0.07782117]
 [ 2.37833723 -0.10197916]
 [ 1.98922283  0.01594269]
 [ 1.75515866  0.32222994]
 [ 1.92337414  0.51707954]
 [ 2.36944197  0.46220852]
 [ 2.57740909  0.52131765]
 [ 1.86628364  0.03684068]
 [ 0.78350107 -0.28224559]
 [ 1.04654173 -0.59287341]
 [ 0.92624775 -0.58154315]
 [ 1.21350295 -0.18271062]
 [ 2.45484304 -0.16987605]
 [ 1.65527915 -0.2824369 ]
 [ 1.81559853  0.40873904]
 [ 2.23308203  0.62794478]
 [ 1.91058202 -0.20149637]
 [ 1.30556451 -0.11010982]
 [ 1.27031971 -0.54071843]
 [ 1.56786112 -0.50032813]
 [ 1.93540356  0.17036645]
 [ 1.31724204 -0.26667722]
 [ 0.43351269 -0.94816519]
 [ 1.44292361 -0.34370743]
 [ 1.39149443 -0.05139956]
 [ 1.44166934 -0.12839424]
 [ 1.69042716  0.19086557]
 [ 0.20483609 -0.70757789]
 [ 1.37155027 -0.19405865]]

label:
(100,)
[0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0
 0 0 0 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1]
>>> 
```



So we start to explain what svm is.

{% embed url="https://scikit-learn.org/stable/auto_examples/svm/plot_separating_hyperplane.html#sphx-glr-auto-examples-svm-plot-separating-hyperplane-py" %}
Reference program
{% endembed %}

The first thing: use sklearn to build an svm on the data set:

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
plt.scatter( data[:, 0], data[:, 1],
             c = label, cmap = 'tab10'
             )

# plt.show()



####################
# svm
####################

from sklearn import svm

clf = svm.SVC( kernel='linear' )
clf.fit( data, label) 

xlim = [ min(data[:, 0]), max(data[:, 0]) ]
ylim = [ min(data[:, 1]), max(data[:, 1]) ] 


xx = np.linspace(xlim[0], xlim[1], 10)
yy = np.linspace(ylim[0], ylim[1], 10)
YY, XX = np.meshgrid(yy, xx)


xy = np.vstack([XX.ravel(), YY.ravel()]).T
Z = clf.decision_function(xy).reshape(XX.shape)

ax = plt.gca()

# plot decision boundary and margins
ax.contour( XX, YY, Z,
            cmap = 'tab10',
            levels = [-1, 0, 1],
            alpha = 0.5,
            linestyles = ['--', '-', '--']
            )

plt.show()
```

![Linear svm](<../.gitbook/assets/image (6).png>)

SVM is a classifier and one of the best classifiers for supervised learning.

The basic idea of SVM is to draw a line to separate two different data. For example, in the picture: the brown line separates the blue and green dots.

The SVM algorithm ensures that the points on both sides are separated by this line to the greatest extent: that is, the points on both sides are the farthest away from this line.

So SVM adjusts the slope and position of this line so that the point on both sides which closest to this line(Use dashed lines to indicate) are the farthest from this line. Just as shown in the picture.

We call the distance between the dotted line and the SVM dividing line margen. The purpose of the SVM trainer is to maximize the margen of the training set data.









## Statistics

Start time of this page: December 21, 2021

Completion time of this page: December 22, 2021