---
description: Model composite score
coverY: 0
---

# F1 score

If a factory produces a batch of products, if we improve the process level, the defective rate of the product will decrease, but the cost will also increase. If we reduce the process level, the defective rate will rise, but the cost will also decrease.

Then the technological level has entered the state of Nash equilibrium. We don’t want the level of craftsmanship to be too high, because it will make our prices unattractive, but we also don’t want too low a level of craftsmanship to cause our factories to produce mobile phones that will explode. So how should we decide?

In the previous chapter, we talked about precision and recall. If the precision is high, you need a low level of craftsmanship, and if the precision is high, you need a high level of craftsmanship. Then if we use an average (we said before that the harmonic average is suitable for dealing with such problems) to average the precision and recall, then we can find a suitable level of craftsmanship.

![F1 score](<../.gitbook/assets/image (7).png>)

F1 score is the harmonic average of precision and recall.

In sklearn we can easily calculate the F1 score, the procedure is as follows:

```python
true_table = [1,0,0,0,1,1,1,0,0,0,1,1,0,1,0,1,1,0,1,1,0,1,0,0,0,1,0,1]
pred_table = [0,1,0,1,0,1,1,0,1,0,1,0,0,1,0,1,1,1,0,1,0,0,1,1,0,0,0,1]

from sklearn.metrics import f1_score

print( f1_score(true_table, pred_table, average='macro') )
print( f1_score(true_table, pred_table, average='micro') )
```

The calculation results are as follows:

```python
0.5714285714285714
0.5714285714285714
>>> 
```

## illustration

In real life, we will receive a lot of emails, but many emails are spam and contain advertisements and fraudulent content.

We can make a language model to detect which emails are spam and which are not spam.

![illustration](<../.gitbook/assets/image (5).png>)

As shown in the figure, we have explained the precision recall rate and F1 score.

![Fβ](<../.gitbook/assets/image (20).png>)

In our real life, there are some events that require a high precision rate, and some events require a high rate of precision.

For example, if nuclear power plants always release high-risk news but actually there is no problem at all, it will cause public panic and not trusted.

If a high-intensity infectious disease breaks out, but the patients are not effectively isolated, it will cause the collapse of the social system.

So we need to add a coefficient to the F score to ensure that we take into account both the precision and recall.



## Statistics

Start time of this page: December 29, 2021

Completion time of this page: December 31, 2021
