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

![Two-dimensional Gaussian distribution of 1000 points](<../.gitbook/assets/image (18) (1) (1).png>)

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

![projection](<../.gitbook/assets/image (19) (1) (1).png>)

We can change the slope of this line, and the result of the projection will change accordingly, for example:

```python
y = -x
```

![Result 1](<../.gitbook/assets/image (15).png>)

```python
y = x
```

![Result 2](<../.gitbook/assets/image (17) (1).png>)

We call the result above as result 1, and the result below as result 2.

I now want to compress this two-dimensional Gaussian distribution into one-dimensional data. Do you think I keep the projection of result 1 more reflecting the real situation or the projection of keeping result 2 more reflecting the real situation?

Our data is a positive correlation (x increases with y will also increase), if we keep the result 1, then the data becomes a negative correlation, then the second result is more representative.

So does the projection of result 2 best reflect the characteristics of the data?

We can rotate this line to make the projection of each point more dispersed on this line. When we adjust to a certain position, these points reach the most dispersed, then this is the best position.

There are some complicated mathematical algorithms involved, and I won’t describe them here. Those who are interested can read the description of PCA in the machine learning book.

Let's talk about how to use python's sklearn library to instantiate PCA.

{% embed url="https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html" %}
instruction
{% endembed %}

```python
import numpy as np
import matplotlib.pyplot as plt

# Set a random seed
# So the result of each run is the same
np.random.seed(42)

mu = [0, 0]
sigma = [ [10, 8], [8, 10] ]
point = np.random.multivariate_normal(mu, sigma, 200)

plt.scatter(point[:,0], point[:,1])



from sklearn.decomposition import PCA

pca_clf = PCA(n_components = 2)
pca_clf.fit(point)
print(pca_clf.explained_variance_ratio_)

pca_data = pca_clf.fit_transform(point)
print(pca_data)

plt.scatter(pca_data[:,0], pca_data[:,1])

plt.show()
```

![Drawing result](<../.gitbook/assets/image (11).png>)

```python
[0.89874751 0.10125249]

[[-2.08302664e+00 -2.28111353e-01]
 [-2.69843058e+00  2.12801965e+00]
 [ 1.01615694e+00 -3.96801699e-01]
 [-6.66173935e+00  1.10171260e+00]
 [ 2.02621253e+00  6.90889329e-01]
 [ 1.98528998e+00 -7.34692054e-01]
 [-1.02907466e+00 -2.74976196e+00]
 [ 7.33561835e+00 -9.28392805e-01]
 [ 4.32790039e+00  3.43406757e-01]
 [ 3.85719196e+00 -2.09341737e+00]
 [-6.19495530e+00 -3.07965098e-01]
 ...
```

In this program, I used sklearn's pca function to perform principal component analysis on the data.

The input data is two-dimensional, and PCA model analyzes two-dimensional (you can only analyze and output one-dimensional, n\_components = 2 can be changed to n\_components = 1, and the reduction of n\_components will only reduce the dimensionality of the output result, but it will not change the result Value)

Then use this model to fit\_transform the two-dimensional Gaussian distribution data and plot it.

The blue point in the above figure is the original data, and the orange point is the data after PCA.

In the orange data, the x-axis is its principal component, and the y-axis is its second component.

<mark style="color:purple;">**You will find that the working method of PCA is to rotate the coordinate axis to a certain angle, so that the data can be displayed as much as possible on the new coordinate axis of this angle.**</mark>

Let's look at the output of the command line:&#x20;

The content of the first line is: \[0.89874751 0.10125249], This is the output of the line of code print(pca\_clf.explained\_variance\_ratio\_). This line of code is used to analyze how much information the principal and minor components account for in the overall data.&#x20;

Here we find that the principal component occupies 0.89874751 information of the overall data, and the principal component occupies close to 90% of the information, which is very high. So if we ignore the remaining 10% of the amount of information, it will not have much impact on the integrity of our data.

After that, a large amount of data output is the data after PCA. If we only extract the first number of each row of data, it is our principal component.

```python
print(pca_data[:,0])
```

The following is the output result.

```python
[-2.08302664e+00 -2.69843058e+00  1.01615694e+00 -6.66173935e+00
  2.02621253e+00  1.98528998e+00 -1.02907466e+00  7.33561835e+00
  4.32790039e+00  3.85719196e+00 -6.19495530e+00 -2.81677763e-01
  2.33748479e+00  4.91496868e+00  2.57006454e+00  2.60697432e+00
  6.76075794e-02 -3.48168025e+00 -8.89357479e-01  5.66398893e+00
 -3.10396063e+00  5.12399721e-01  6.28792944e+00  1.99649948e+00
 -1.45807103e+00 -1.35438812e+00  2.90733186e+00 -4.33352549e+00
  3.58194651e+00 -1.36429746e+00  2.05636528e+00  4.70176947e+00
 -3.40025500e+00  3.46972448e-01 -1.51762612e+00 -1.48363516e+00
  2.01939288e-01  1.11527371e+01 -3.47483123e-01 -3.92981967e-01
  9.63650013e-01 -6.25132202e+00  3.44869549e+00 -3.85221487e+00
  2.28152662e+00 -3.70891770e-01  2.99976167e+00  1.66769748e+00
 -1.22599673e+00  1.08483221e-03  6.02453530e+00  1.46813628e+00
  7.16661455e-01 -7.97299518e+00 -1.06743478e+00  8.16611320e+00
 -1.91998587e-01  8.46947016e-01  1.55932264e-01 -4.81063307e+00
 -3.34328593e+00 -5.94606323e+00 -2.43027957e+00  4.22001859e+00
 -4.04043548e-01  6.60588908e+00  4.54018936e+00  3.95029303e+00
  3.34432987e+00 -3.44353250e+00 -9.18913695e-01  6.84869430e+00
 -1.06439801e+00  5.25401703e+00 -2.18347806e+00 -1.03113735e+00
  2.91476463e+00 -1.22779776e+00 -7.88188244e+00  5.09022104e+00
  4.17319621e+00 -4.90129777e+00 -4.05447070e+00 -3.43253979e+00
  1.05597197e+00  3.78767518e+00  3.58569421e-01 -1.13501922e+00
 -6.88629256e-03  1.19018203e+00 -2.64095456e+00  4.57676052e+00
  9.85122393e-01 -1.98244161e+00  3.59587971e+00  1.93354919e+00
 -9.00763746e-01 -7.02562315e-01  3.77831831e+00 -2.37885250e-01
 -1.48308644e+00 -4.55249927e+00  5.85678036e+00 -2.15090456e+00
 -2.10053099e+00 -2.37847438e+00 -4.01109730e+00  1.37528114e+00
  3.30137719e+00  2.08666321e+00 -9.82158392e+00 -2.90942434e+00
  2.04488998e+00 -2.62657064e-01  3.07118815e+00  3.12809654e+00
 -1.76853683e-01 -9.05957102e+00  8.62059931e+00  2.84675690e+00
  3.38677719e+00 -2.10296139e+00  5.11340520e+00  2.03136152e+00
 -7.45732367e+00  5.38935548e+00 -8.96111907e+00  6.46478113e+00
 -5.35910884e+00 -1.84483913e+00  3.95783070e+00  1.37615988e+01
  1.07897123e+00 -6.92061733e+00  1.89513968e+00 -6.10982005e+00
 -4.90812892e+00  4.19725097e+00 -8.27234356e-01 -2.75626463e-01
 -4.45265056e-01 -6.72088883e+00 -9.05233846e+00  6.79138924e-01
 -1.17516284e+00  9.01813050e-01  2.53947238e+00 -1.49874569e+00
 -3.78549943e+00 -3.41265531e+00  3.53478830e+00 -3.13477838e+00
  1.16765821e-01 -5.40297715e+00 -2.29773786e+00  9.66405682e-01
 -3.46313831e+00 -5.51172347e+00 -2.87148123e+00 -1.35088742e+00
 -3.76186239e-01  3.52913958e+00  4.27591067e+00 -4.87489110e+00
 -2.61195459e+00  6.47259507e-02 -3.05498969e-01 -4.11274668e+00
  3.52355557e+00 -1.73401252e+00  3.51818805e+00 -1.02058097e+00
  2.02815784e+00  6.14841606e+00  3.07102429e+00 -1.27039139e+00
 -3.61462859e+00  9.18546834e-02  1.00501647e-01 -1.35527304e+00
 -2.15380590e+00  4.93791744e-01 -2.90760443e+00 -9.24178497e-01
 -3.99734305e-01 -7.01399452e-02 -6.11552151e+00 -9.11992642e+00
 -3.67164208e+00 -9.27590354e+00  3.57970360e+00  9.02879339e+00
  3.24913577e+00 -1.39520936e+00 -4.01446858e+00  3.84518347e+00
  5.65493623e+00 -4.98442001e+00  7.31456758e+00  5.30938749e-01]
```

Principal component analysis can not only extract principal components. In our actual machine learning, because sometimes the data dimension is too high, the training time is too long. Using PCA for dimensionality reduction and discarding some low-information dimensions can solve this problem.

## View the most important dimensions

In PCA, we always want to know which dimension is the most important. For example, we have information about wages, consumption, housing loans, car loans, etc. We want to know which information has a greater impact on raising children(positive and negative). We need to analyze the proportion of the original components in the PCA.

```python
pca_components = abs(pca_clf.components_)

print(pca_components)
```

Get the following output:

```python
[[0.69951524 0.71461768]
 [0.71461768 0.69951524]]
>>> 
```

![Raw data](<../.gitbook/assets/image (18) (1).png>)

The data obtained in the first row is the data source ratio of the principal components.

pca obtained 0.69951524 data from the x-axis and 0.71461768 data from the y-axis. From the figure, we can see that the dispersion of the data on the x-axis and y-axis is similar.

The data obtained in the second row is the data source ratio of the second principal component.

## PCA inverse\_transform

In machine learning, PCA inverse\_transform is rarely used, so I won’t introduce it here. If you are interested, please check sklearn.

Principal component analysis analyzes the key information in the data. If you use principal component analysis to reduce dimensionality, you will retain most of the information in the data. Of course, the data can be reconstructed using this information. If you retain enough information, the reconstructed data will be very close to the original data.

If the Mars exploration satellite transmits the complete data of Mars it has collected to the earth, the amount of this data is very large and the transmission will be very difficult. But if we use PCA for dimensionality reduction and retain 80% or 90% or 95% of the information before transmission, a considerable part of the data will be reduced. But the transmitted data is similar to which before it was reduce.

## Statistics

Start time of this page: January 3, 2022

Completion time of this page: January 6, 2022
