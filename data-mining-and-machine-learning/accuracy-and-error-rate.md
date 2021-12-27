---
description: Evaluate the model's quality
coverY: 0
---

# Accuracy and error rate

In the previous chapter, we used SVM to predict the handwritten digits in the mnist dataset. In this chapter, we will evaluate the quality of our model.

The most commonly used method to check the quality of a model is accuracy. This is also used a lot in our lives. For example, in our exams, students get scores if they answer correctly, but they don’t get scores if they don’t answer it correctly. In the end, students' scores determine their academic performance. The score here is the accuracy.

```python
model_pred = [
    7, 0, 1, 0, 4, 1, 9, 4, 1, 9,
    0, 1, 9, 0, 1, 9, 7, 7, 2, 4,
    9, 6, 1, 5, 4, 0, 7, 4, 0, 1,
    3, 1, 3, 4, 9, 5, 7, 1, 1, 1
    ]

ture_label = [
    7, 2, 1, 0, 4, 1, 4, 9, 5, 9,
    0, 6, 9, 0, 1, 5, 9, 7, 3, 4,
    9, 6, 6, 5, 4, 0, 7, 4, 0, 1,
    3, 1, 3, 4, 7, 2, 7, 1, 2, 1
    ]
```









## Statistics

Start time of this page: December 26, 2021

Completion time of this page: December 26, 2021
