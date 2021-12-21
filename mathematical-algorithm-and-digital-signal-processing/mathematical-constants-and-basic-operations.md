---
description: pi e Trigonometric function
---

# 5 Mathematical constants and basic operations

When we are using python, we will use mathematical operations very often. For example, some mathematical constants or trigonometric functions, exponential functions, etc.&#x20;

This tutorial will teach you how to use these contents.

Python's built-in math library contains a lot of mathematical operations, but for unification, we all use the numpy library.

```python
>>> import numpy as np

>>> np.pi
3.141592653589793

>>> np.e
2.718281828459045

>>> np.sin(np.pi/4)
0.7071067811865476

# Power has priority over division, so there is no need to add parentheses
>>> 2**0.5 / 2
0.7071067811865476

# Euler formula: e^(i*pi)+1=0 numpy can handle complex number operations
>>> np.e ** (0+1j * np.pi)
(-1+1.2246467991473532e-16j)
>>> 
```

## Statistics

Start time of this page: December 21, 2021

Completion time of this page: December 21, 2021
