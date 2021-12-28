---
description: Confusion matrix
coverY: 0
---

# Confusion matrix &

Confusion matrix is one of the most important ways to observe training results in machine learning and deep learning.

After the confusion matrix is built, we can also calculate the accuracy rate, error rate, precision rate, recall rate and other evaluation parameters.



Because we deal with binary classification problems in most cases, I will start with the confusion matrix of the binary classification problem:

```python
true_table = [1,0,0,0,1,1,1,0,0,0,1,1,0,1,0,1,1,0,1,1,0,1,0,0,0,1,0,1]
pred_table = [0,1,0,1,0,1,1,0,1,0,1,0,0,1,0,1,1,1,0,1,0,0,1,1,0,0,0,1]
```

We now have a cat and dog data set, where 0 is a cat and 1 is a dog.

The above is the original label and the result obtained through model prediction.

```python
true_table = [1,0,0,0,1,1,1,0,0,0,1,1,0,1,0,1,1,0,1,1,0,1,0,0,0,1,0,1]
pred_table = [0,1,0,1,0,1,1,0,1,0,1,0,0,1,0,1,1,1,0,1,0,0,1,1,0,0,0,1]

from sklearn.metrics._plot.confusion_matrix import confusion_matrix

print(confusion_matrix( true_table, pred_table ))

tn, fp, fn, tp = confusion_matrix( true_table, pred_table ).ravel()

print()
print('Confusion Matrix')
print('=====================')
print('TN =', str(tn), end=' | ')
print('FP =', str(fp))
print('---------------------')
print('FN =', str(fn), end=' | ')
print('TP =', str(tp))
```

Get the following results:

```python
[[8 6]
 [6 8]]

Confusion Matrix
=====================
TP = 8 | FP = 6
---------------------
FN = 6 | TN = 8
>>> 
```

<mark style="color:green;">**TP: A positive sample was retrieved, which is actually a positive sample (correctly identified)**</mark>

<mark style="color:green;">**In this case, the performance is as follows: it is predicted to be a cat, but it is also a cat in reality.**</mark>

<mark style="color:red;">**FP: A positive sample was retrieved, but it was actually a negative sample (a type of misidentification)**</mark>

<mark style="color:red;">**In this case, the performance is: predicted to be a cat, but actually a dog.**</mark>

<mark style="color:red;">**FN: No positive sample has been retrieved, but it is actually a positive sample. (Another type of misidentification)**</mark>

<mark style="color:red;">**In this case, the performance is: predicted to be a dog, but actually a cat.**</mark>

<mark style="color:green;">**TN: No positive sample has been retrieved, but it is actually a negative sample. (Correct identification)**</mark>

<mark style="color:green;">**In this case, the performance is: predicted to be a dog, but in fact it is also a dog.**</mark>

### Accuracy

The accuracy rate is the correct prediction divided by the overall data size.

The accuracy rate is equal to (TN+TP)/(TN+TP+FN+FP)

Of course, in fact, we don't need to manually calculate these things, sklearn has prepared related libraries for us.

```python
true_table = [1,0,0,0,1,1,1,0,0,0,1,1,0,1,0,1,1,0,1,1,0,1,0,0,0,1,0,1]
pred_table = [0,1,0,1,0,1,1,0,1,0,1,0,0,1,0,1,1,1,0,1,0,0,1,1,0,0,0,1]

from sklearn.metrics import accuracy_score

print(accuracy_score(true_table, pred_table))
```

The results of the above program are as follows:

```python
0.5714285714285714
>>> 
```

{% hint style="danger" %}
<mark style="color:red;">**Don't write your own code!**</mark>

In python programming, we should avoid writing code by ourselves as much as possible, because the code you write is not necessarily correct, and even if it is correct, it is certainly not as efficient as the code in the python built-in library.

So if there is a piece of code in the python built-in library (including keras, sklearn, numpy, pandas), then don't write your own code!
{% endhint %}

### Error rate

The error rate is 1-the accuracy rate. Because of the accuracy rate is so clear, we rarely compare the error rate.

In the confusion matrix, the error rate is sum of all prediction error types: FN and FP, divided by the total amount of data.





















## Statistics

Start time of this page: December 28, 2021

Completion time of this page: December 30, 2021
