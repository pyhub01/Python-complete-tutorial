---
description: Dictionaries and sets
coverY: 0
---

# 2 Data structure with hash table

I will explain the hash table in detail in the database section later. At present, we only need to know that the hash table can be quickly searched.

Let me give an example. The time it takes to search 10,000 times in the list (data structure that does not contain the hash table) and set (the data structure that contains the hash table):

```python
a = list(range(100000))
b = set(range(100000))

import time

time_start = time.time()

for _ in range(10000):
    99999 in a

time_end = time.time()
print('list time cost = ', time_end - time_start, 's')



time_start = time.time()

for _ in range(10000):
    99999 in b

time_end = time.time()
print('set time cost = ', time_end - time_start, 's')
```

The result of running this program is:

```python
list time cost =  8.223406553268433 s
set time cost =  0.0 s
>>> 
```

You will find that it takes a long time to search when the data structure does not contain a hash table, and when the data structure contains a hash table, the search can be completed in almost no time.&#x20;

This difference becomes more obvious when the amount of data becomes larger.

So when we perform large-scale data search, we should use data structure contains hash tables.

## <mark style="color:purple;">set</mark>

The meaning of set is derived from mathematics and refers to an unordered list without repetition.

We can create a new collection in the following way.

```python
>>> a = set()
>>> a
set()
>>> 
```

We can also convert a list into a collection.

```python
>>> a = [1, 2, 2, 2, 3, 4, 4, 5, 5, 5]
>>> a
[1, 2, 2, 2, 3, 4, 4, 5, 5, 5]

>>> a = set(a)
>>> a
{1, 2, 3, 4, 5}
>>> 
```

You will find that the repeated elements have been deleted from the set.







## Statistics

Start time of this page: December 19, 2021

Completion time of this page:&#x20;
