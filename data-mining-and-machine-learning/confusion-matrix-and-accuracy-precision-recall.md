---
description: Confusion matrix
coverY: 0
---

# Confusion matrix & Accuracy, Precision, Recall

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

### Precision

The precision is the ratio of tp/(tp + fp), where tp is the correct number of positive samples and fp is the number of false positives. The precision can be intuitively said to be the classifier’s ability to not mark negative samples as positive samples.

The best value of precision is 1, and the worst value is 0.

```python
true_table = [1,0,0,0,1,1,1,0,0,0,1,1,0,1,0,1,1,0,1,1,0,1,0,0,0,1,0,1]
pred_table = [0,1,0,1,0,1,1,0,1,0,1,0,0,1,0,1,1,1,0,1,0,0,1,1,0,0,0,1]

from sklearn.metrics import precision_score

print( precision_score(true_table, pred_table, average='macro') )
print( precision_score(true_table, pred_table, average='micro') )
```

Sklearn still provides us with very convenient code, we only need to call it to easily calculate the precision value.

```python
0.5714285714285714
0.5714285714285714
>>> 
```

#### <mark style="color:purple;">Macro Average</mark>

Macro average refers to making each category have the same weight when calculating the mean, and the final result is the arithmetic average of the indicators of each category.

#### <mark style="color:purple;">Micro Average</mark>

Micro-averaging refers to assigning the same weight to each sample of all categories when calculating the multi-category index, and all the samples are combined to calculate each index.

<mark style="color:orange;">****</mark>

<mark style="color:orange;">**The difference between macro average and micro average**</mark>

If the number of samples in each category is similar, there is not much difference between the macro-average and the micro-average.

If the number of samples in each category is very different, use micro-averaging when focusing on classes with a large sample size, and use macro-averaging when focusing on classes with a small sample size.

If the micro-average is much lower than the macro-average, then check the classes with a large sample size to determine the reason for the poor performance of the indicator.

If the macro average is significantly lower than the micro average, then check the class with a small sample size to determine the reason for the poor performance of the indicator.

**In most cases, the difference between these two calculation methods is not big, so in general, you don't need to care about such subtle issues.**

{% hint style="success" %}
<mark style="color:green;">**What is precision?**</mark>

The precision can be intuitively said to be the classifier’s ability to not mark negative samples as positive samples.

For example, there is a nuclear power plant. Nuclear power plants often have some super small accidents, such as falling off of the building structure. These small accidents generally do not cause a nuclear leak. So if we can evaluate what accidents are small accidents and what are large accidents, then we will not cause panic among the people.

The precision rate can be used to measure whether the announcement issued by the nuclear power plant will cause panic among the people.

For example, there was a small robbery in the parking lot of a nuclear power plant, and the suspect robbed 20 dollars, then this is a micro accident that has nothing to do with the safety of the nuclear power plant. If such an accident causes public panic, the precision rate of nuclear power plant accidents will be very low.
{% endhint %}

### Recall

The recall rate refers to the proportion of the samples that are actually positive that are predicted to be positive to the samples that are actually positive.

In other words, the recall rate is a measure of how many positive samples are not marked as positive.

{% hint style="success" %}
<mark style="color:green;">**What is recall?**</mark>

**The recall rate is a measure of how many positive samples are not marked as positive.**

For example, a sudden outbreak of an infectious disease, this infectious disease is very dangerous, so we have to isolate the patients. We conduct tests in the crowd and find possible patients for isolation.

If we isolate more people, there will be no serious consequences other than causing panic among the crowd and increasing the medical burden. But if some patients are not quarantined, the problem is serious because this infectious disease will explode quickly and cause the collapse of this society. The recall rate is a measure of the intensity of quarantining the sick. The higher the recall rate, the better the control of the disease.

Because most of the events in our lives are afraid of defective products leaving the factory, the recall rate is more meaningful than Precision in actual use.
{% endhint %}



















## Statistics

Start time of this page: December 28, 2021

Completion time of this page: December 30, 2021
