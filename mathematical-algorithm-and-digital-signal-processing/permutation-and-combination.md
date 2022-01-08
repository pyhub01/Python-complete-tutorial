---
description: Permutation and combination
coverY: 0
---

# Permutation and combination

Permutation and combination are commonly used content in statistics.

It can be easily implemented in python through libraries.

## Combination

```python
import itertools
print( itertools.combinations(['tom',2,3,4], 3) )
print( list(itertools.combinations(['tom',2,3,4], 3)) )
```

get the following result

```python
<itertools.combinations object at 0x000001BB837F6630>

[('tom', 2, 3), ('tom', 2, 4), ('tom', 3, 4), (2, 3, 4)]
>>> 
```

The result obtained with itertools can only see the address header position of the result.

If we convert the result to a list we can see the result.

{% hint style="success" %}
<mark style="color:green;">**The meaning of the above code is: regardless of the order, select three from \['tom', 2, 3, 4] without repetition**</mark>
{% endhint %}

Implementing composition requires some specific algorithms, which we will explain in the leetcode section later.

## Permutation

```python
import itertools
print( itertools.permutations(['tom',2,3,4], 3) )
print( list(itertools.permutations(['tom',2,3,4], 3)) )
```

get the following result

```python
<itertools.permutations object at 0x00000213DE0766D0>

[('tom', 2, 3), ('tom', 2, 4), ('tom', 3, 2), ('tom', 3, 4), 
('tom', 4, 2), ('tom', 4, 3), (2, 'tom', 3), (2, 'tom', 4), 
(2, 3, 'tom'), (2, 3, 4), (2, 4, 'tom'), (2, 4, 3), (3, 'tom', 2), 
(3, 'tom', 4), (3, 2, 'tom'), (3, 2, 4), (3, 4, 'tom'), (3, 4, 2), 
(4, 'tom', 2), (4, 'tom', 3), (4, 2, 'tom'), (4, 2, 3), (4, 3, 'tom'), 
(4, 3, 2)]
>>> 
```

{% hint style="success" %}
<mark style="color:green;">**The meaning of the above code is: consider the order, select three from \['tom', 2, 3, 4] without repetition**</mark>
{% endhint %}

Permutation and combination are very useful in statistics and mathematics, such as in the Bernoulli distribution chapter.

## Statistics

Start time of this page: January 7, 2022

Completion time of this page: January 9, 2022
