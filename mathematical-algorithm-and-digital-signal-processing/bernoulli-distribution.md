---
description: binomial distribution
coverY: 0
---

# Bernoulli distribution

Bernoulli distribution or binomial distribution is A common distribution in our lives.

For example: I now have an uneven coin, the probability of flipping heads is 0.6, and the probability of flipping tails is 0.4.

I toss a coin five times in a row. What is the probability of three heads?

We list five coin toss possibilities: True for heads up and False for tails up.

Then one of the coin tosses is True or False, and five consecutive coin tosses can be represented by an ordered list: \[True, False, True, True, False], The probability of this happening is: 0.6\*0.4\*0.6\*0.6\*0.4 = 0.03456

So how many outcomes are there in total when we flip a coin five times in a row?

```cfscript
ans = []

for a in [True, False]:
    for b in [True, False]:
        for c in [True, False]:
            for d in [True, False]:
                for e in [True, False]:
                    ans.append([a,b,c,d,e])

print(len(ans))
print(ans)
```

Each coin toss has either heads or tails, so there are 2\*\*5=32 different situations for five tosses.

All cases can be printed in full using the above code.

```python
32

[[True, True, True, True, True], [True, True, True, True, False], 
[True, True, True, False, True], [True, True, True, False, False], 
[True, True, False, True, True], [True, True, False, True, False], 
[True, True, False, False, True], [True, True, False, False, False], 
[True, False, True, True, True], [True, False, True, True, False], 
[True, False, True, False, True], [True, False, True, False, False], 
[True, False, False, True, True], [True, False, False, True, False], 
[True, False, False, False, True], [True, False, False, False, False], 
[False, True, True, True, True], [False, True, True, True, False], 
[False, True, True, False, True], [False, True, True, False, False], 
[False, True, False, True, True], [False, True, False, True, False], 
[False, True, False, False, True], [False, True, False, False, False], 
[False, False, True, True, True], [False, False, True, True, False], 
[False, False, True, False, True], [False, False, True, False, False], 
[False, False, False, True, True], [False, False, False, True, False], 
[False, False, False, False, True], [False, False, False, False, False]]
>>> 
```



















## Statistics

Start time of this page: January 9, 2022

Completion time of this page: January 9, 2022
