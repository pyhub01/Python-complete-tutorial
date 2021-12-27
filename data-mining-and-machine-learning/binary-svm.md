---
description: Support Vector Machines
coverY: 0
---

# binary SVM

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

![2D-data visualization](<../.gitbook/assets/image (12) (1) (1).png>)

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
clf.fit( data, label ) 

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

![Linear svm](<../.gitbook/assets/image (6) (1) (1) (1).png>)

SVM is a classifier and one of the best classifiers for supervised learning.

The basic idea of SVM is to draw a line to separate two different data. For example, in the picture: the brown line separates the blue and green dots.

The SVM algorithm ensures that the points on both sides are separated by this line to the greatest extent: that is, the points on both sides are the farthest away from this line.

So SVM adjusts the slope and position of this line so that the point on both sides which closest to this line(Use dashed lines to indicate) are the farthest from this line. Just as shown in the picture.

We call the distance between the dotted line and the SVM dividing line margen. The purpose of the SVM trainer is to maximize the margen of the training set data.

The algorithm of SVM is complicated, but fortunately sklearn includes libsvm, we can use linear svm and kernel svm very conveniently.

## XOR problem

Problems like the following that cannot be divided by a straight line are called XOR problems.

![XOR problems](<../.gitbook/assets/image (13) (1) (1) (1) (1).png>)

```python
x = [
    [1, 2], [2, -1], [-1, -2], [-2, 1],
    [2, 1], [1, -2], [-2, -1], [-1, 2],
    ]
    
y = [0, 0, 0, 0, 1, 1, 1, 1]

import numpy as np

x = np.array(x)
y = np.array(y)

import matplotlib.pyplot as plt

plt.figure( figsize=(6, 6) )

plt.scatter( x[:, 0], x[:, 1],
             c = y
             )

plt.grid()
plt.show()
```

The accuracy of dividing this problem with a straight line can never be higher than 50%.

SVM is a classifier based on a hyperplane, so SVM can draw a dividing line that is much more complicated than a straight line.

```python
x = [
    [1, 2], [2, -1], [-1, -2], [-2, 1],
    [2, 1], [1, -2], [-2, -1], [-1, 2],
    ]

y = [0, 0, 0, 0, 1, 1, 1, 1]

import numpy as np

x = np.array(x)
y = np.array(y)

import matplotlib.pyplot as plt

plt.figure( figsize=(6, 6) )

plt.scatter( x[:, 0], x[:, 1],
             c = y
             )

plt.grid()
# plt.show()

####################
# svm
####################

from sklearn import svm

clf = svm.SVC( kernel='linear',
               C = 1000
               )
clf.fit( x, y ) 



xx = np.linspace( min(x[:, 0])-1, max(x[:, 0])+1, 10 )
yy = np.linspace( min(x[:, 1])-1, max(x[:, 1])+1, 10 )
XX, YY = np.meshgrid(xx, yy)


ax = plt.gca()

Z = clf.predict( np.vstack([XX.ravel(), YY.ravel()]).T ).reshape(XX.shape)

out = ax.contourf( XX, YY, Z,
                   alpha = 0.5
                   )

plt.show()
```

![Resolution = 10](<../.gitbook/assets/image (11).png>)

![Resolution = 100](<../.gitbook/assets/image (6) (1) (1).png>)

![Resolution = 1000](<../.gitbook/assets/image (2) (1).png>)

![Resolution = 2000](<../.gitbook/assets/image (13) (1) (1) (1).png>)

We can see that linear SVM is racking it brains to solve this classification problem.

But this is basically futile, and you will find that SVM fantasizes out a pattern that does not exist in the first place. When we adjust C (penalty coefficient) too high, SVM has a strong overfitting problem.

In order to solve the XOR problem, if we make the dividing line of the SVM into a curve, then the problem is solved?

In the following example, I replaced the linear core with an rbf core.

```python
x = [
    [1, 2], [2, -1], [-1, -2], [-2, 1],
    [2, 1], [1, -2], [-2, -1], [-1, 2],
    ]

y = [0, 0, 0, 0, 1, 1, 1, 1]

import numpy as np

x = np.array(x)
y = np.array(y)

import matplotlib.pyplot as plt

plt.figure( figsize=(6, 6) )

plt.scatter( x[:, 0], x[:, 1],
             c = y
             )

plt.grid()
# plt.show()

####################
# svm
####################

from sklearn import svm

clf = svm.SVC( kernel = 'rbf',
               C = 1000
               )
clf.fit( x, y ) 



xx = np.linspace( min(x[:, 0])-1, max(x[:, 0])+1, 1000 )
yy = np.linspace( min(x[:, 1])-1, max(x[:, 1])+1, 1000 )
XX, YY = np.meshgrid(xx, yy)


ax = plt.gca()

Z = clf.predict( np.vstack([XX.ravel(), YY.ravel()]).T ).reshape(XX.shape)

out = ax.contourf( XX, YY, Z,
                   alpha = 0.1
                   )

plt.show()
```

![rbf core SVM](<../.gitbook/assets/image (1).png>)

The problem has been solved very well!

The area where the purple dot is located is divided into purple, and the area where the yellow dot is located is divided into yellow.

And you will find that the space between the yellow and purple points is very large, which means that the SVM is very adaptable. If the data has a certain range, it can still be in the correct position.

{% hint style="success" %}
<mark style="color:green;">**RBF kernel**</mark>
{% endhint %}

The RBF core is one of the most commonly used cores because of its simple principle and good effect.

If we draw the RBF core it looks like this:

```python
from matplotlib import pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

import numpy as np

fig = plt.figure()
ax = plt.axes( projection = '3d' )


minmax = 2
xx = np.arange( -minmax, minmax, minmax / 100 )
yy = np.arange( -minmax, minmax, minmax / 100 )
X, Y = np.meshgrid( xx, yy )
Z = np.e ** -( X**2 + Y**2 )


ax.plot_surface( X, Y, Z,
                 cmap = 'rainbow'
                 )

plt.title('rbf function')
plt.xlabel('x')
plt.ylabel('y')

plt.grid()
plt.show()
```

![RBF function](<../.gitbook/assets/image (13) (1) (1).png>)

The RBF function turns a linear function into a nonlinear result, which is very useful in machine learning. Because the world we live in is also non-linear.

For example, in SVM, we cannot use straight lines to divide regions, because the points are not on different sides of a picture, they may overlap(XOR problem), so these nonlinear functions are very useful.

### Other kernel

We use other kernels to show you the effect of nonlinear SVM:

{% hint style="success" %}
<mark style="color:green;">**sigmoid core**</mark>
{% endhint %}

![sigmoid](<../.gitbook/assets/image (13).png>)

```python
from matplotlib import pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

import numpy as np

fig = plt.figure()
ax = plt.axes( projection = '3d' )


minmax = 2
xx = np.arange( -minmax, minmax, minmax / 100 )
yy = np.arange( -minmax, minmax, minmax / 100 )
X, Y = np.meshgrid( xx, yy )
Z = 1 / ( 1 + np.e ** -( X - Y ))


ax.plot_surface( X, Y, Z,
                 cmap = 'rainbow'
                 )

plt.title('sigmoid function')
plt.xlabel('x')
plt.ylabel('y')

plt.grid()
plt.show()
```

What is drawn here is a two-dimensional sigmoid function. The sigmoid function is also a very commonly used function to turn linear results into nonlinearities.

```python
x = [
    [1, 2], [2, -1], [-1, -2], [-2, 1],
    [2, 1], [1, -2], [-2, -1], [-1, 2],
    ]

y = [0, 0, 0, 0, 1, 1, 1, 1]

import numpy as np

x = np.array(x)
y = np.array(y)

import matplotlib.pyplot as plt

plt.figure( figsize=(6, 6) )

plt.scatter( x[:, 0], x[:, 1],
             c = y
             )

plt.grid()
# plt.show()

####################
# svm
####################

from sklearn import svm

clf = svm.SVC( kernel = 'sigmoid',
               C = 1000
               )
clf.fit( x, y ) 



xx = np.linspace( min(x[:, 0])-1, max(x[:, 0])+1, 1000 )
yy = np.linspace( min(x[:, 1])-1, max(x[:, 1])+1, 1000 )
XX, YY = np.meshgrid(xx, yy)


ax = plt.gca()

Z = clf.predict( np.vstack([XX.ravel(), YY.ravel()]).T ).reshape(XX.shape)

out = ax.contourf( XX, YY, Z,
                   alpha = 0.2
                   )

plt.show()
```

![sigmoid core SVM](<../.gitbook/assets/image (15) (1) (1) (1).png>)

You will find that sigmoid does not work well when dealing with XOR problems.

{% hint style="success" %}
<mark style="color:green;">**polynomial core**</mark>
{% endhint %}

If you know what a series, Taylor expansion or Fourier transform is, then polynomial expansion will be much easier.

![Taylor expansion of some formulas](<../.gitbook/assets/image (14) (1) (1).png>)

If you don't know the above concepts, then please check out the following example.

```python
import numpy as np
x = np.arange(-np.pi*2, np.pi*2, 0.1)
y = np.zeros(x.shape)

N = 2

for i in range( 1, N ):
    y += (-1)**(i-1) * x**(2*i-1) / np.math.factorial(2*i-1)


import matplotlib.pyplot as plt

plt.plot(x, y)

plt.title('cos(x) Taylor Expansion')
plt.xlabel('x'); plt.ylabel('y')
plt.ylim(-3, 3)
plt.grid(); plt.show()
```

The above function can draw the function image of the Taylor expansion of the cosine. Adjusting N can change the order of the Taylor expansion drawn.

For example, when N=2, the first-order Taylor expansion is drawn:

![N = 2](<../.gitbook/assets/image (5).png>)

For example, when N=3, the second-order Taylor expansion is drawn:

![N = 3](<../.gitbook/assets/image (10) (1).png>)

Then comes the higher-order Taylor expansion:

![N = 4](<../.gitbook/assets/image (14).png>)

![N = 5](<../.gitbook/assets/image (7) (1) (1) (1).png>)

![N = 6](<../.gitbook/assets/image (15) (1).png>)

![N = 7](<../.gitbook/assets/image (6) (1).png>)

![N = 8](<../.gitbook/assets/image (9) (1).png>)

![N = 9](<../.gitbook/assets/image (8) (1).png>)

When N=10, numpy reports an error, and Taylor expansion uses the power, and the power increases exponentially, which soon broke through the tolerance range of python. In the mathematical method, we will discuss other calculation algorithms to reduce the burden of python.

```python
Traceback (most recent call last):
  File "xxx.py", line 8, in <module>
    y += (-1)**(i-1) * x**(2*i-1) / np.math.factorial(2*i-1)
TypeError: ufunc 'add' output (typecode 'O') could not be coerced to provided 
output parameter (typecode 'd') according to the casting rule ''same_kind''
```

You will find that when N increases, the function of the Taylor expansion becomes more and more like a cosine function. This is a polynomial.

```python
import numpy as np
x = np.arange(-np.pi*2, np.pi*2, 0.1)
y = np.zeros(x.shape)

N = 10
curves = np.zeros((N-1, x.shape[0]))
for i in range( 1, N ):
    y += (-1)**(i-1) * x**(2*i-1) / np.math.factorial(2*i-1)
    curves[i-1] = y
# print(curves)

import matplotlib.pyplot as plt
for i in range(len(curves)):
    plt.plot(x, curves[i], label = i+1)

plt.title('cos(x) Taylor Expansion')
plt.xlabel('x'); plt.ylabel('y')
plt.ylim(-3, 3)
plt.grid(); plt.legend(); plt.show()
```

![merged](<../.gitbook/assets/image (14) (1).png>)

We can plot the multi-level results together, and you can see the difference between them.

When our order is **insufficient**, underfitting will occur, that is, the Taylor expansion function cannot keep up with the change of the original function. When the order is **right**, it fits the original function exactly. When the order is **too high**, over-fitting will occur, and the Taylor expansion will not tolerate any noise at all. But because the real world is noisy, the polynomials will have large deviations.

For example, in the previous example, if I get too few polynomials, the following results will appear:

![Underfitting](<../.gitbook/assets/image (3).png>)

If our polynomial order is right, then we can get as good results as the rbf kernel:

![Correct fit](<../.gitbook/assets/image (4).png>)

In this example, there is no overfitting problem. The overfitting problem needs a larger and more noisy data set.

## Comparison of different kernels

{% embed url="https://scikit-learn.org/stable/auto_examples/svm/plot_iris_svc.html" %}
Reference program
{% endembed %}

sklearn provides us with a very good program to visualize the effects of different SVM cores.

![SVM different kernel visualization](<../.gitbook/assets/image (13) (1).png>)

```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn import svm, datasets


def make_meshgrid(x, y, h=0.02):
    """
    Create a mesh of points to plot in

    Parameters
    ----------
    x: data to base x-axis meshgrid on
    y: data to base y-axis meshgrid on
    h: stepsize for meshgrid, optional

    Returns
    -------
    xx, yy : ndarray
    """
    x_min, x_max = x.min() - 1, x.max() + 1
    y_min, y_max = y.min() - 1, y.max() + 1
    xx, yy = np.meshgrid(np.arange(x_min, x_max, h), np.arange(y_min, y_max, h))
    return xx, yy


def plot_contours(ax, clf, xx, yy, **params):
    """
    Plot the decision boundaries for a classifier.

    Parameters
    ----------
    ax: matplotlib axes object
    clf: a classifier
    xx: meshgrid ndarray
    yy: meshgrid ndarray
    params: dictionary of params to pass to contourf, optional
    """
    Z = clf.predict(np.c_[xx.ravel(), yy.ravel()])
    Z = Z.reshape(xx.shape)
    out = ax.contourf(xx, yy, Z, **params)
    return out


# import some data to play with
iris = datasets.load_iris()
# Take the first two features. We could avoid this by using a two-dim dataset
X = iris.data[:, :2]
y = iris.target

# we create an instance of SVM and fit out data. We do not scale our
# data since we want to plot the support vectors
C = 1.0  # SVM regularization parameter
models = (
    svm.SVC(kernel="linear", C=C),
    svm.LinearSVC(C=C, max_iter=10000),
    svm.SVC(kernel="rbf", gamma=2, C=C),
    svm.SVC(kernel="poly", degree=3, gamma="auto", C=C),
)
models = (clf.fit(X, y) for clf in models)

# title for the plots
titles = (
    "SVC with linear kernel",
    "LinearSVC (linear kernel)",
    "SVC with RBF kernel",
    "SVC with polynomial (degree 3) kernel",
)

# Set-up 2x2 grid for plotting.
fig, sub = plt.subplots(2, 2)
plt.subplots_adjust(wspace=0.4, hspace=0.4)

X0, X1 = X[:, 0], X[:, 1]
xx, yy = make_meshgrid(X0, X1)

for clf, title, ax in zip(models, titles, sub.flatten()):
    plot_contours(ax, clf, xx, yy, cmap=plt.cm.coolwarm, alpha=0.8)
    ax.scatter(X0, X1, c=y, cmap=plt.cm.coolwarm, s=20, edgecolors="k")
    ax.set_xlim(xx.min(), xx.max())
    ax.set_ylim(yy.min(), yy.max())
    ax.set_xlabel("Sepal length")
    ax.set_ylabel("Sepal width")
    ax.set_xticks(())
    ax.set_yticks(())
    ax.set_title(title)

plt.show()
```

The basic idea of this visualization: use the iris data set to train an SVM model, and then divide the visualization space into small grids by linear interpolation, and then send the data of each small grid to the SVM to predict the results, and then give the background based on the results Color, and finally get the color block map of this area in the above figure.

{% hint style="danger" %}
<mark style="color:red;">**Tips on tuning**</mark>

In svm, rbf and linear are the most commonly used. Linear is suitable for linear data, while rbf is used for almost any data. When the noise is very large or the data has XOR problems, then rbf is a good choice. SVM has Some significant shortcomings, such as over-fitting, this problem can generally only be solved using deep learning.
{% endhint %}

## Statistics

Start time of this page: December 21, 2021

Completion time of this page: December 22, 2021
