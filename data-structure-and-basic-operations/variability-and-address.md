---
description: Quite important
---

# 2 Variability and address

Python is a label language, which is very different from the C language.&#x20;

In python, each variable name is a pointer to the corresponding memory unit.

```python
>>> a = 5
>>> a
5
>>> id(a)
140735234512784
>>> 
```

We can use the id() method to get the address of the memory unit pointed to by a variable.

In this example, the variable name **a** points to the memory address numbered **140735234512784**, and the memory address stores an **int** type data, the value of this data is **5**.

As shown in the figure below:

![Variables and memory](../.gitbook/assets/image.png)



If I copy a variable in python, for example, as shown below:

```python
>>> a = 5
>>> b = a

>>> a
5
>>> b
5

>>> id(a)
140735234512784
>>> id(b)
140735234512784
>>> 
```

You will find that the memory address units pointed to by **a** and **b** are the same! That is to say, when I tried to copy a variable, I didn't really clone the variable, but: I created another pointer points to the memory, and the two pointers point to the same memory space.

![Shared memory](<../.gitbook/assets/image (2) (1).png>)

This means that when I try to change the content of **a**, the content of **b** will also change<mark style="color:red;">**???**</mark>

{% hint style="danger" %}
<mark style="color:red;">**Not always, This is the real trouble!**</mark>
{% endhint %}

If I change the value of **a**, but the address of **a** does not change, the value of **b** will also change accordingly.&#x20;

Then we say that this is a **variable** data type.

<mark style="color:red;">**We need to pay extra attention to this pattern!**</mark>

![Scenario 1](<../.gitbook/assets/image (1).png>)



But if I change the value of **a**, but **a** points to another address, then **b** still points to the original address, and the values of **a** and **b** are different.

Then we say that this is an **immutable** data type.

![Scenario 2](<../.gitbook/assets/image (2).png>)

{% hint style="success" %}
<mark style="color:green;">**Numbers are immutable**</mark>
{% endhint %}

```python
>>> a = 5
>>> b = a

>>> id(a)
140735234512784
>>> id(b)
140735234512784

>>> a = 10
>>> b
5

>>> id(a)
140735234512944
>>> id(b)
140735234512784
>>> 
```

Number is an immutable data type. When I assign another number to a variable, the address of the variable changes.

{% hint style="success" %}
<mark style="color:green;">**Strings are immutable**</mark>
{% endhint %}

```python
>>> a = 'hello'
>>> a[2] = 'p'
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
    a[2] = 'p'
TypeError: 'str' object does not support item assignment
>>> 
```

The string itself cannot be modified, So when we modify the string, python will report an error

So when the string is updated, The original string is recycled, the pointer must point to another memory location, the previous address must be changed.

```python
>>> a = 'hello'
>>> b = a

>>> id(a)
3074560303408
>>> id(b)
3074560303408

>>> a = 'world'
>>> b
'hello'

>>> id(a)
3074560304176
>>> id(b)
3074560303408
>>> 
```

String is an immutable data type. When I assign another string to a variable, the address of the variable changes.

{% hint style="danger" %}
<mark style="color:red;">**Lists are**</mark><mark style="color:red;">** **</mark><mark style="color:red;"><mark style="color:green;">****<mark style="color:green;"></mark><mark style="color:red;">** **</mark><mark style="color:red;">**Variable**</mark>
{% endhint %}

```python
>>> a = [1, 2, 3]
>>> b = a

>>> id(a)
3074560050560
>>> id(b)
3074560050560

>>> a[2] = 10
>>> b
[1, 2, 10]

>>> id(a)
3074560050560
>>> id(b)
3074560050560
>>> 
```

```python
>>> a = [1, 2, 3]
>>> b = a

>>> id(a)
3074560050688
>>> id(b)
3074560050688

>>> a.append(4)
>>> b
[1, 2, 3, 4]

>>> id(a)
3074560050688
>>> id(b)
3074560050688
>>> 
```

The list is changeable, and every time the list is modified, the variable pointer of the list will not change, so when the list is copied, it cannot be simply done by assignment.

In python, we call this method of assignment shallow copy, which means that we just copy a label pointer, and the memory still shares a location with the previous variable.

We call a full copy of the memory a deep copy. In a deep copy, the data in the memory is completely copied. Of course, this will also consume more memory.

There are many ways to deep copy, for example, we can write a loop.

```python
>>> a = list(range(10))
>>> a
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> b = []
>>> for i in a:
	b.append(i)
>>> b
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> id(a)
1777018729856
>>> id(b)
1777019369664

>>> a[3] = 9999
>>> a
[0, 1, 2, 9999, 4, 5, 6, 7, 8, 9]
>>> b
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> 
```



