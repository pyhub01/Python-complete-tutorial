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

We can filter out the cases where three of them are positive:

```python
ans = []

for a in [True, False]:
    for b in [True, False]:
        for c in [True, False]:
            for d in [True, False]:
                for e in [True, False]:
                    ans.append([a,b,c,d,e])

# print(len(ans))
# print(ans)

thrice = []
for i in ans:
    if sum(i)==3:
        thrice.append(i)

print(len(thrice))
print(thrice)
```

In this way, we filter out all the results with three heads and two tails, a total of 10:

```python
10

[[True, True, True, False, False], [True, True, False, True, False], 
[True, True, False, False, True], [True, False, True, True, False], 
[True, False, True, False, True], [True, False, False, True, True], 
[False, True, True, True, False], [False, True, True, False, True], 
[False, True, False, True, True], [False, False, True, True, True]]
>>> 
```

A total of 10 different throws resulted in three heads and two tails.

And the probability of getting \[True, True, True, False, False] result is 0.6\*_0.6\*_0.6\*_0.4\*_0.4=0.03456

So the probability of getting three heads and two tails is the product of the above two results: 10\*0.03456=0.3456

## binomial distribution

The calculation method of the binomial distribution uses permutations and combinations:

![binomial distribution](<../.gitbook/assets/image (21).png>)

If you follow the example just now, then in the binomial distribution formula, p is the probability of heads of the coin, and q is the probability of tails of the coin. The preceding c(n, x) is the frequency of three heads and two tails.

So the probability of three heads and two tails is: c(5,2)\*_(0.6\*\*3)\*_(0.4\*\*2)













## Statistics

Start time of this page: January 9, 2022

Completion time of this page: January 9, 2022
