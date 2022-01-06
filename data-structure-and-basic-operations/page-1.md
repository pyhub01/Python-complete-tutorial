---
description: Dictionaries and sets
coverY: 0
---

# Data structure with hash table

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

You will find that it takes a long time to search when the data structure does not contain a hash table, and when the data structure contains a hash table, the search can be completed in almost no time.

This difference becomes more obvious when the amount of data becomes larger.

So when we perform large-scale data search, we should use data structure contains hash tables.

{% hint style="danger" %}
One requirement for using a hash table is: there can only be one of each element. If the content to be searched contains duplicate elements, then the hash table cannot be used to speed up the search.

For example, you can use a hash table to find specific elements in 1, 2, 3, 4, 5, but you cannot find specific elements in 1, 1, 2, 2, 3 because they contain duplicate elements. This is reflected in both sets and dictionaries: sets do not allow duplicate elements, and dictionaries do not allow duplicate keys.

This feature of the hash table is very dangerous. If the content you need to find contains duplicate elements, it may cause errors in the search results.
{% endhint %}

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



The set uses a hash table index, so the set is unordered, and we cannot index the set:

```python
>>> test_set = {1,2,3,4,5}

>>> test_set[3]
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
    test_set[3]
TypeError: 'set' object is not subscriptable
>>> 
```

Set is not used much in python, it is mainly used to remove redundant elements in the list:

```python
>>> a = [1, 2, 2, 2, 3, 4, 4, 5, 5, 5]
>>> a = list(set(a))
>>> a
[1, 2, 3, 4, 5]
>>> 
```

## <mark style="color:purple;">dictionary</mark>

Dictionaries are used more in python. Because the hash table index is used, the dictionary can be looked up quickly.

```python
>>> d = {'name':'tom', 'age':24, 'gender':'male'}
>>> d
{'name': 'tom', 'age': 24, 'gender': 'male'}
>>> 
```

As shown in the code block above, we have created a dictionary.

{% hint style="danger" %}
<mark style="color:red;">**Please note that the keys in the dictionary are unique, which means you should not operate as follows(**</mark>Repeated assignments will be overwritten, you should be extra careful about this, because it may lead to incorrect program results<mark style="color:red;">**)**</mark>
{% endhint %}













## Statistics

Start time of this page: December 19, 2021

Completion time of this page:
