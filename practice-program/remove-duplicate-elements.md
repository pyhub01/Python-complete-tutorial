---
description: Use of sets
coverY: 0
---

# 🚩 Remove duplicate elements

When we are programming, we often need to remove duplicate elements, so what should we do? Let's look at the following example:

```python
>>> a = list(range(10))
>>> a
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> a = a * 2
>>> a
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> a = list(set(a))
>>> a
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> 
```

We first create a list, and then repeat the list, so that each element has a redundancy.&#x20;

We take advantage of the fact that there are no repeating elements in the set, and convert the list into a set to remove the repeating elements.&#x20;

Because our previous data structure was a list, for the unification, the final output still uses a list. So we need to transform the collection into a list again.

## Statistics

Start time of this page: December 19, 2021

Completion time of this page: December 19, 2021
