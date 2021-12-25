---
description: Use of step size
coverY: 0
---

# 🚩 Palindrome detection

![DNA](<../.gitbook/assets/image (9) (1).png>)

There are some palindrome sequences in DNA, such as "ATGCGCGTAATGCGCGTA"

This sequence is symmetric from a certain position in the middle, and we call this sequence a palindrome sequence. So how to detect palindrome sequence?

Look at the following program:

```python
def palindrome(string):
    print(string, end='\t')
    print(string==string[::-1])
    # return string==string[::-1]

palindrome('123454321')
palindrome('13454321')
palindrome('ATGCGCGTAATGCGCGTA')
palindrome('ATGCGCGTAATGCGCGTG')
```

If this sequence is a palindrome sequence, then it will return True, if not, it will return False.

The string is reversed by changing the string step length to -1, and then it is judged whether it is the same as the previous string to distinguish the palindrome sequence.

```python
123454321	True
13454321	False
ATGCGCGTAATGCGCGTA	True
ATGCGCGTAATGCGCGTG	False
>>> 
```

## Statistics

Start time of this page: December 20, 2021

Completion time of this page: December 20, 2021
