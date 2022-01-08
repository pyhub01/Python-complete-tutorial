---
description: Harmonic mean
coverY: 0
---

# Harmonic mean

We have explained what an average is before, so today we will explain the other most important average in probability statistics: the harmonic average.

For example, Some students study literature and mathematics. We want to give these students a comprehensive score. (We want to analyze the problem of students' partial subjects)

<mark style="color:red;">There is a student who scored 60 points in the literature test and 60 points in the math test, so his average score is 60, which does not seem very good.</mark>

<mark style="color:red;">But his harmonic average score is: 2/(1/60+1/60)=60.0</mark>

<mark style="color:blue;">Another student scored 100 points in the literature test, but only 20 points in the math test. His average score is the same as the previous student, which is 60 points.</mark>

<mark style="color:blue;">But his harmonic average score is: 2/(1/100+1/20)=33.33333333333333</mark>

![binary harmonic mean definition](<../.gitbook/assets/image (19) (1) (1) (1).png>)

We can know that the second student's partial subject problem is more serious.



![Lymphoma](<../.gitbook/assets/image (6) (1).png>)

Lymphoma is a cancer that occurs on the lymphatics.

The incidence of lymphoma is only 6.68 per 100,000 people.

We call a data set with approximately the same number of positive samples (sickness) and negative samples (not sick) as a balanced data set. A data set with a large difference in the number of positive samples (sick) and negative samples (not sick) is called an unbalanced data set.

**You should be extra careful when dealing with unbalanced data sets:**

If we invent a new lymphoma detection method, the detection accuracy rate in normal people is 99.9%, while the detection accuracy rate in patients is 0%.

This detection method is actually useless at all, because it can't detect patients at all.

If we use a weighted average to measure the effectiveness of this detection method, because the number of people who are not sick accounted for the vast majority, so the weight of the contribution of those who are not sick is very high, then the correct rate is relatively close to 99.9%. The detection method is very effective according to the result from the weighted average, but it is wrong.

If we use the harmonic average, then the final accuracy is equal to 0, which is the correct result.

More details will be discussed in F1 score.

## Statistics

Start time of this page: December 28, 2021

Completion time of this page: December 28, 2021
