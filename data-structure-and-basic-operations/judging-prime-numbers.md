---
description: Prime Number Algorithm
coverY: 0
---

# Judging prime numbers

Prime numbers are very important in computer science. In the famous RSA protocol, it is done by factoring large integers. Its difficulty determines the reliability of the RSA algorithm.

In Goldbach's conjecture, the calculation of prime numbers is also very important. In future section, we will study how to prove Goldbach's conjecture on finite sets.

## what is prime number

The opposite of prime numbers is composite numbers.

A prime number refers to a number that is factored. If the factor is only 1 and itself, then the number is a prime number.

For example, the smallest prime number and the only even prime number is 2, because 2=1\*2, only 1 and itself are factors.

Then 3 and 5 and 7 and 11 are also prime numbers.

We see 4=2\*2, so 4 is a sum, then there are 6, 8, 9, 10, 12 and so on.

According to the above method, it is easy to write a program to calculate the prime numbers:

## first try

In the first attempt we didn't consider efficiency, we just wrote a program that would work.

```python
def prime_detect_v1(num):
    for i in range(2, num):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

for i in range(2, 20):
    print(i, end='\t')
    print(prime_detect_v1(i))
```

The program is very simple. If a number is not divisible by all numbers less than itself, then the number is a prime number, otherwise a composite number.

```python
2	prime number
3	prime number
4	composite number
5	prime number
6	composite number
7	prime number
8	composite number
9	composite number
10	composite number
11	prime number
12	composite number
13	prime number
14	composite number
15	composite number
16	composite number
17	prime number
18	composite number
19	prime number
>>> 
```

We simply run it and the program is correct.

## second attempt

In the first attempt we only considered correctness, this version we consider efficiency:

The most time-consuming thing in determining prime function is the loop. If we can reduce the number of loops, then the efficiency of our program can increase.

If there is a number 29, and we want to determine whether it is a prime number or not, do we need to try from 2 all the way to 28? No, because if numbers up to (square 29)+1 are not divisible by 29, then neither can numbers over (square 29)+1.

```python
def prime_detect_v1(num):
    for i in range(2, num):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

import math

def prime_detect_v2(num):
    for i in range( 2, int(math.sqrt(num))+1 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

for i in range(2, 30):
    print(i, end='\t')
    # print(prime_detect_v1(i))
    print(prime_detect_v2(i))
```

```python
2	prime number
3	prime number
4	composite number
5	prime number
6	composite number
7	prime number
8	composite number
9	composite number
10	composite number
11	prime number
12	composite number
13	prime number
14	composite number
15	composite number
16	composite number
17	prime number
18	composite number
19	prime number
20	composite number
21	composite number
22	composite number
23	prime number
24	composite number
25	composite number
26	composite number
27	composite number
28	composite number
29	prime number
>>> 
```

Such a method reduces a considerable amount of computation.

## third attempt

The second attempt reduced the computational load by a considerable amount, so can we go further?

YES!

We know that all even numbers except 2 are not prime numbers, so it is very simple, we can exclude all even numbers except 2.

```renpy
def prime_detect_v1(num):
    for i in range(2, num):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

import math

def prime_detect_v2(num):
    for i in range( 2, int(math.sqrt(num))+1 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

def prime_detect_v3(num):
    if num == 2:
        return 'prime number'
    if num % 2 == 0:
        return 'composite number'
    for i in range( 3, int(math.sqrt(num))+1, 2 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

for i in range(2, 30):
    print(i, end='\t')
    # print(prime_detect_v1(i))
    # print(prime_detect_v2(i))
    print(prime_detect_v3(i))
```

```python
2	prime number
3	prime number
4	composite number
5	prime number
6	composite number
7	prime number
8	composite number
9	composite number
10	composite number
11	prime number
12	composite number
13	prime number
14	composite number
15	composite number
16	composite number
17	prime number
18	composite number
19	prime number
20	composite number
21	composite number
22	composite number
23	prime number
24	composite number
25	composite number
26	composite number
27	composite number
28	composite number
29	prime number
>>> 
```

But since 2 is also the first number to be tested if you follow the normal process, this method does not change that much. Using this method reduces the amount of computation by about half.

## fourth attempt

In the third attempt, we ruled out all multiples of 2, so can we do the same for multiples of 3? Of course it is possible.

Any natural number can always be expressed in one of the following six forms: 6n, 6n+1, 6n+2, 6n+3, 6n+4, 6n+5 (n=0,1,2...)

We can find that, apart from 2 and 3, only numbers of the form 6n+1 and 6n+5 can be prime numbers. And if numbers of the form 6n+1 and 6n+5 are not prime numbers, their factors will also contain numbers of the form 6n+1 or 6n+5, so the following algorithm can be obtained:

```python
def prime_detect_v1(num):
    for i in range(2, num):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

import math

def prime_detect_v2(num):
    for i in range( 2, int(math.sqrt(num))+1 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

def prime_detect_v3(num):
    if num == 2:
        return 'prime number'
    if num % 2 == 0:
        return 'composite number'
    for i in range( 3, int(math.sqrt(num))+1, 2 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

def prime_detect_v4(num):
    if num == 2 or num == 3:
        return 'prime number'
    if num % 6 != 1 and num % 6 != 5:
        return 'composite number'
    for i in range( 5, int(math.sqrt(num))+1, 6 ):
        if num % i == 0 or num % (i + 2) == 0:
            return 'composite number'
    return 'prime number'

for i in range(2, 50):
    print(i, end='\t')
    # print(prime_detect_v1(i))
    # print(prime_detect_v2(i))
    # print(prime_detect_v3(i))
    print(prime_detect_v4(i))
```

```python
2	prime number
3	prime number
4	composite number
5	prime number
6	composite number
7	prime number
8	composite number
9	composite number
10	composite number
11	prime number
12	composite number
13	prime number
14	composite number
15	composite number
16	composite number
17	prime number
18	composite number
19	prime number
20	composite number
21	composite number
22	composite number
23	prime number
24	composite number
25	composite number
26	composite number
27	composite number
28	composite number
29	prime number
30	composite number
31	prime number
32	composite number
33	composite number
34	composite number
35	composite number
36	composite number
37	prime number
38	composite number
39	composite number
40	composite number
41	prime number
42	composite number
43	prime number
44	composite number
45	composite number
46	composite number
47	prime number
48	composite number
49	composite number
>>> 
```

This approach has reached the limit of artificial optimization, so we will not use the same method to optimize this program (you can add 5 or 7 or 11 ... optimization algorithms, but these optimizations decrease marginally as the number increases, and the code changes is too complicated, so I will not continue to use this method to optimize)

## fifth attempt

The previous algorithm has reached the limit of optimization, so if we want to continue to optimize the program, we can only change the algorithm.

There are three different measures of <mark style="color:blue;">**Labor complexity**</mark> and <mark style="color:orange;">**space complexity**</mark> and <mark style="color:green;">**time complexity**</mark> in the program.

<mark style="color:blue;">**Labor complexity**</mark> <mark style="color:blue;"></mark><mark style="color:blue;">refers to the labor cost of writing a program. The simpler the program, the lower the labor complexity, and vice versa.</mark>

<mark style="color:blue;">We use python because the</mark> <mark style="color:blue;"></mark><mark style="color:blue;">**Labor complexity**</mark> <mark style="color:blue;"></mark><mark style="color:blue;">of python is very low, so many python programs do not care so much about the time complexity or space complexity, because in scientific research, most programs do not run many times, and the length of time to write code is long. Much larger than the running time, and writing the program quickly is the most important.</mark>

<mark style="color:orange;">**Space complexity**</mark> <mark style="color:orange;"></mark><mark style="color:orange;">refers to the memory and disk size occupied by a program. The larger the space complexity, the larger the disk and memory size occupied by the program.</mark>

<mark style="color:green;">**Time complexity**</mark> <mark style="color:green;"></mark><mark style="color:green;">refers to the length of the running time of the program. In theory, we can calculate the time complexity of the program running (check algorithm books for details, and mathematics is not explained here). However, due to the multi-level cache mechanism of the computer and the connection mechanism of the memory, the time complexity is complicated. It is difficult to predict correctly (we are only predicting a trend), so the time complexity of a program is often calculated by running the program thousands of times (most programs run for a very short time, and the measured results are inaccurate) and measure the actual time divided by number of times the programming runs.</mark>

For a series of algorithms that are not stupid, the weighted product of Labor complexity and space complexity and time complexity is generally similar. That is to say, if the Labor complexity of an algorithm is relatively high, then the space complexity and time complexity of the algorithm will be relatively low.

In the previous program, the program became more and more complex, which is our Labor complexity has been increasing, but the corresponding time complexity has been decreasing.

Now our time complexity can't seem to be reduced, so we can convert some time complexity and  Labor complexity <mark style="color:blue;">****</mark> into space complexity to reduce time complexity and Labor complexity.

Today's computers are more resourceful (not always running out of memory as in 1990) and many programs can mediate between these three complexities.

```python
def prime_detect_v1(num):
    for i in range(2, num):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

import math

def prime_detect_v2(num):
    for i in range( 2, int(math.sqrt(num))+1 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

def prime_detect_v3(num):
    if num == 2:
        return 'prime number'
    if num % 2 == 0:
        return 'composite number'
    for i in range( 3, int(math.sqrt(num))+1, 2 ):
        if num % i == 0:
            return 'composite number'
    return 'prime number'

def prime_detect_v4(num):
    if num == 2 or num == 3:
        return 'prime number'
    if num % 6 != 1 and num % 6 != 5:
        return 'composite number'
    for i in range( 5, int(math.sqrt(num))+1, 6 ):
        if num % i == 0 or num % (i + 2) == 0:
            return 'composite number'
    return 'prime number'

import numpy as np
prime_list = np.array([2]) # init

def prime_detect_v5(num):
    global prime_list # passed to the function
    for i in prime_list[ prime_list < int(math.sqrt(num))+1 ]:
        if num % i == 0:
            return 'composite number'
    
    prime_list = np.append(prime_list, num)
    return 'prime number'

for i in range(2, 100):
    print(i, end='\t')
    # print(prime_detect_v1(i))
    # print(prime_detect_v2(i))
    # print(prime_detect_v3(i))
    # print(prime_detect_v4(i))
    print(prime_detect_v5(i))
```

In this method we build an array in which we keep all the prime numbers that have been tested.

Then we only need to divide the detected number by all the values in the array that are less than the square root of the detected number when we perform the detection.

This method has the same time complexity as the previous method, and the space complexity is much larger, but it is very easy to think of.

If a number is even, then the first number 2 in the array can rule out that the number is prime, and if a number is a multiple of 3, then the second number 3 in the array can rule out the number being prime.

The disadvantage of this method is that the continuous sequence must be detected, and in reality we generally only need to detect whether a certain number is a prime number. Which this method doesnot work.

```python
2	prime number
3	prime number
4	composite number
5	prime number
6	composite number
7	prime number
8	composite number
9	composite number
10	composite number
11	prime number
12	composite number
13	prime number
14	composite number
15	composite number
16	composite number
17	prime number
18	composite number
19	prime number
20	composite number
21	composite number
22	composite number
23	prime number
24	composite number
25	composite number
26	composite number
27	composite number
28	composite number
29	prime number
30	composite number
31	prime number
32	composite number
33	composite number
34	composite number
35	composite number
36	composite number
37	prime number
38	composite number
39	composite number
40	composite number
41	prime number
42	composite number
43	prime number
44	composite number
45	composite number
46	composite number
47	prime number
48	composite number
49	composite number
50	composite number
51	composite number
52	composite number
53	prime number
54	composite number
55	composite number
56	composite number
57	composite number
58	composite number
59	prime number
60	composite number
61	prime number
62	composite number
63	composite number
64	composite number
65	composite number
66	composite number
67	prime number
68	composite number
69	composite number
70	composite number
71	prime number
72	composite number
73	prime number
74	composite number
75	composite number
76	composite number
77	composite number
78	composite number
79	prime number
80	composite number
81	composite number
82	composite number
83	prime number
84	composite number
85	composite number
86	composite number
87	composite number
88	composite number
89	prime number
90	composite number
91	composite number
92	composite number
93	composite number
94	composite number
95	composite number
96	composite number
97	prime number
98	composite number
99	composite number
>>> 
```

## ensemble

We can put these methods together to see the correctness:

A basic way to check whether a program is right or wrong is a checker: use random numbers or a lot of data to check your method multiple times against a library function method (or two methods you write, one algorithm, the other is the brute force calculation) results are the same or not.

```python
def prime_detect_v1(num):
    for i in range(2, num):
        if num % i == 0:
            return 'composite'
    return 'prime'

import math

def prime_detect_v2(num):
    for i in range( 2, int(math.sqrt(num))+1 ):
        if num % i == 0:
            return 'composite'
    return 'prime'

def prime_detect_v3(num):
    if num == 2:
        return 'prime'
    if num % 2 == 0:
        return 'composite'
    for i in range( 3, int(math.sqrt(num))+1, 2 ):
        if num % i == 0:
            return 'composite'
    return 'prime'

def prime_detect_v4(num):
    if num == 2 or num == 3:
        return 'prime'
    if num % 6 != 1 and num % 6 != 5:
        return 'composite'
    for i in range( 5, int(math.sqrt(num))+1, 6 ):
        if num % i == 0 or num % (i + 2) == 0:
            return 'composite'
    return 'prime'

import numpy as np
prime_list = np.array([2]) # init

def prime_detect_v5(num):
    global prime_list # passed to the function
    for i in prime_list[ prime_list < int(math.sqrt(num))+1 ]:
        if num % i == 0:
            return 'composite'
    
    prime_list = np.append(prime_list, num)
    return 'prime'

for i in range(2, 1000):
    print(i, end='\t')
    print(prime_detect_v1(i), end=' ')
    print(prime_detect_v2(i), end=' ')
    print(prime_detect_v3(i), end=' ')
    print(prime_detect_v4(i), end=' ')
    print(prime_detect_v5(i))
```

```python
2	prime prime prime prime prime
3	prime prime prime prime prime
4	composite composite composite composite composite
5	prime prime prime prime prime
6	composite composite composite composite composite
7	prime prime prime prime prime
8	composite composite composite composite composite
9	composite composite composite composite composite
10	composite composite composite composite composite
11	prime prime prime prime prime
12	composite composite composite composite composite
13	prime prime prime prime prime
14	composite composite composite composite composite
15	composite composite composite composite composite
16	composite composite composite composite composite
17	prime prime prime prime prime
18	composite composite composite composite composite
19	prime prime prime prime prime
20	composite composite composite composite composite
21	composite composite composite composite composite
22	composite composite composite composite composite
23	prime prime prime prime prime
24	composite composite composite composite composite
25	composite composite composite composite composite
26	composite composite composite composite composite
27	composite composite composite composite composite
28	composite composite composite composite composite
29	prime prime prime prime prime
30	composite composite composite composite composite
31	prime prime prime prime prime
32	composite composite composite composite composite
33	composite composite composite composite composite
34	composite composite composite composite composite
35	composite composite composite composite composite
36	composite composite composite composite composite
37	prime prime prime prime prime
38	composite composite composite composite composite
39	composite composite composite composite composite
40	composite composite composite composite composite
41	prime prime prime prime prime
42	composite composite composite composite composite
43	prime prime prime prime prime
44	composite composite composite composite composite
45	composite composite composite composite composite
46	composite composite composite composite composite
47	prime prime prime prime prime
48	composite composite composite composite composite
49	composite composite composite composite composite
50	composite composite composite composite composite
51	composite composite composite composite composite
52	composite composite composite composite composite
53	prime prime prime prime prime
54	composite composite composite composite composite
55	composite composite composite composite composite
56	composite composite composite composite composite
57	composite composite composite composite composite
58	composite composite composite composite composite
59	prime prime prime prime prime
60	composite composite composite composite composite
61	prime prime prime prime prime
62	composite composite composite composite composite
63	composite composite composite composite composite
64	composite composite composite composite composite
65	composite composite composite composite composite
66	composite composite composite composite composite
67	prime prime prime prime prime
68	composite composite composite composite composite
69	composite composite composite composite composite
70	composite composite composite composite composite
71	prime prime prime prime prime
72	composite composite composite composite composite
73	prime prime prime prime prime
74	composite composite composite composite composite
75	composite composite composite composite composite
76	composite composite composite composite composite
77	composite composite composite composite composite
78	composite composite composite composite composite
79	prime prime prime prime prime
80	composite composite composite composite composite
81	composite composite composite composite composite
82	composite composite composite composite composite
83	prime prime prime prime prime
84	composite composite composite composite composite
85	composite composite composite composite composite
86	composite composite composite composite composite
87	composite composite composite composite composite
88	composite composite composite composite composite
89	prime prime prime prime prime
90	composite composite composite composite composite
91	composite composite composite composite composite
92	composite composite composite composite composite
93	composite composite composite composite composite
94	composite composite composite composite composite
95	composite composite composite composite composite
96	composite composite composite composite composite
97	prime prime prime prime prime
98	composite composite composite composite composite
99	composite composite composite composite composite
100	composite composite composite composite composite
101	prime prime prime prime prime
102	composite composite composite composite composite
103	prime prime prime prime prime
104	composite composite composite composite composite
105	composite composite composite composite composite
106	composite composite composite composite composite
107	prime prime prime prime prime
108	composite composite composite composite composite
109	prime prime prime prime prime
110	composite composite composite composite composite
111	composite composite composite composite composite
112	composite composite composite composite composite
113	prime prime prime prime prime
114	composite composite composite composite composite
115	composite composite composite composite composite
116	composite composite composite composite composite
117	composite composite composite composite composite
118	composite composite composite composite composite
119	composite composite composite composite composite
120	composite composite composite composite composite
121	composite composite composite composite composite
122	composite composite composite composite composite
123	composite composite composite composite composite
124	composite composite composite composite composite
125	composite composite composite composite composite
126	composite composite composite composite composite
127	prime prime prime prime prime
128	composite composite composite composite composite
129	composite composite composite composite composite
130	composite composite composite composite composite
131	prime prime prime prime prime
132	composite composite composite composite composite
133	composite composite composite composite composite
134	composite composite composite composite composite
135	composite composite composite composite composite
136	composite composite composite composite composite
137	prime prime prime prime prime
138	composite composite composite composite composite
139	prime prime prime prime prime
140	composite composite composite composite composite
141	composite composite composite composite composite
142	composite composite composite composite composite
143	composite composite composite composite composite
144	composite composite composite composite composite
145	composite composite composite composite composite
146	composite composite composite composite composite
147	composite composite composite composite composite
148	composite composite composite composite composite
149	prime prime prime prime prime
150	composite composite composite composite composite
151	prime prime prime prime prime
152	composite composite composite composite composite
153	composite composite composite composite composite
154	composite composite composite composite composite
155	composite composite composite composite composite
156	composite composite composite composite composite
157	prime prime prime prime prime
158	composite composite composite composite composite
159	composite composite composite composite composite
160	composite composite composite composite composite
161	composite composite composite composite composite
162	composite composite composite composite composite
163	prime prime prime prime prime
164	composite composite composite composite composite
165	composite composite composite composite composite
166	composite composite composite composite composite
167	prime prime prime prime prime
168	composite composite composite composite composite
169	composite composite composite composite composite
170	composite composite composite composite composite
171	composite composite composite composite composite
172	composite composite composite composite composite
173	prime prime prime prime prime
174	composite composite composite composite composite
175	composite composite composite composite composite
176	composite composite composite composite composite
177	composite composite composite composite composite
178	composite composite composite composite composite
179	prime prime prime prime prime
180	composite composite composite composite composite
181	prime prime prime prime prime
182	composite composite composite composite composite
183	composite composite composite composite composite
184	composite composite composite composite composite
185	composite composite composite composite composite
186	composite composite composite composite composite
187	composite composite composite composite composite
188	composite composite composite composite composite
189	composite composite composite composite composite
190	composite composite composite composite composite
191	prime prime prime prime prime
192	composite composite composite composite composite
193	prime prime prime prime prime
194	composite composite composite composite composite
195	composite composite composite composite composite
196	composite composite composite composite composite
197	prime prime prime prime prime
198	composite composite composite composite composite
199	prime prime prime prime prime
200	composite composite composite composite composite
201	composite composite composite composite composite
202	composite composite composite composite composite
203	composite composite composite composite composite
204	composite composite composite composite composite
205	composite composite composite composite composite
206	composite composite composite composite composite
207	composite composite composite composite composite
208	composite composite composite composite composite
209	composite composite composite composite composite
210	composite composite composite composite composite
211	prime prime prime prime prime
212	composite composite composite composite composite
213	composite composite composite composite composite
214	composite composite composite composite composite
215	composite composite composite composite composite
216	composite composite composite composite composite
217	composite composite composite composite composite
218	composite composite composite composite composite
219	composite composite composite composite composite
220	composite composite composite composite composite
221	composite composite composite composite composite
222	composite composite composite composite composite
223	prime prime prime prime prime
224	composite composite composite composite composite
225	composite composite composite composite composite
226	composite composite composite composite composite
227	prime prime prime prime prime
228	composite composite composite composite composite
229	prime prime prime prime prime
230	composite composite composite composite composite
231	composite composite composite composite composite
232	composite composite composite composite composite
233	prime prime prime prime prime
234	composite composite composite composite composite
235	composite composite composite composite composite
236	composite composite composite composite composite
237	composite composite composite composite composite
238	composite composite composite composite composite
239	prime prime prime prime prime
240	composite composite composite composite composite
241	prime prime prime prime prime
242	composite composite composite composite composite
243	composite composite composite composite composite
244	composite composite composite composite composite
245	composite composite composite composite composite
246	composite composite composite composite composite
247	composite composite composite composite composite
248	composite composite composite composite composite
249	composite composite composite composite composite
250	composite composite composite composite composite
251	prime prime prime prime prime
252	composite composite composite composite composite
253	composite composite composite composite composite
254	composite composite composite composite composite
255	composite composite composite composite composite
256	composite composite composite composite composite
257	prime prime prime prime prime
258	composite composite composite composite composite
259	composite composite composite composite composite
260	composite composite composite composite composite
261	composite composite composite composite composite
262	composite composite composite composite composite
263	prime prime prime prime prime
264	composite composite composite composite composite
265	composite composite composite composite composite
266	composite composite composite composite composite
267	composite composite composite composite composite
268	composite composite composite composite composite
269	prime prime prime prime prime
270	composite composite composite composite composite
271	prime prime prime prime prime
272	composite composite composite composite composite
273	composite composite composite composite composite
274	composite composite composite composite composite
275	composite composite composite composite composite
276	composite composite composite composite composite
277	prime prime prime prime prime
278	composite composite composite composite composite
279	composite composite composite composite composite
280	composite composite composite composite composite
281	prime prime prime prime prime
282	composite composite composite composite composite
283	prime prime prime prime prime
284	composite composite composite composite composite
285	composite composite composite composite composite
286	composite composite composite composite composite
287	composite composite composite composite composite
288	composite composite composite composite composite
289	composite composite composite composite composite
290	composite composite composite composite composite
291	composite composite composite composite composite
292	composite composite composite composite composite
293	prime prime prime prime prime
294	composite composite composite composite composite
295	composite composite composite composite composite
296	composite composite composite composite composite
297	composite composite composite composite composite
298	composite composite composite composite composite
299	composite composite composite composite composite
300	composite composite composite composite composite
301	composite composite composite composite composite
302	composite composite composite composite composite
303	composite composite composite composite composite
304	composite composite composite composite composite
305	composite composite composite composite composite
306	composite composite composite composite composite
307	prime prime prime prime prime
308	composite composite composite composite composite
309	composite composite composite composite composite
310	composite composite composite composite composite
311	prime prime prime prime prime
312	composite composite composite composite composite
313	prime prime prime prime prime
314	composite composite composite composite composite
315	composite composite composite composite composite
316	composite composite composite composite composite
317	prime prime prime prime prime
318	composite composite composite composite composite
319	composite composite composite composite composite
320	composite composite composite composite composite
321	composite composite composite composite composite
322	composite composite composite composite composite
323	composite composite composite composite composite
324	composite composite composite composite composite
325	composite composite composite composite composite
326	composite composite composite composite composite
327	composite composite composite composite composite
328	composite composite composite composite composite
329	composite composite composite composite composite
330	composite composite composite composite composite
331	prime prime prime prime prime
332	composite composite composite composite composite
333	composite composite composite composite composite
334	composite composite composite composite composite
335	composite composite composite composite composite
336	composite composite composite composite composite
337	prime prime prime prime prime
338	composite composite composite composite composite
339	composite composite composite composite composite
340	composite composite composite composite composite
341	composite composite composite composite composite
342	composite composite composite composite composite
343	composite composite composite composite composite
344	composite composite composite composite composite
345	composite composite composite composite composite
346	composite composite composite composite composite
347	prime prime prime prime prime
348	composite composite composite composite composite
349	prime prime prime prime prime
350	composite composite composite composite composite
351	composite composite composite composite composite
352	composite composite composite composite composite
353	prime prime prime prime prime
354	composite composite composite composite composite
355	composite composite composite composite composite
356	composite composite composite composite composite
357	composite composite composite composite composite
358	composite composite composite composite composite
359	prime prime prime prime prime
360	composite composite composite composite composite
361	composite composite composite composite composite
362	composite composite composite composite composite
363	composite composite composite composite composite
364	composite composite composite composite composite
365	composite composite composite composite composite
366	composite composite composite composite composite
367	prime prime prime prime prime
368	composite composite composite composite composite
369	composite composite composite composite composite
370	composite composite composite composite composite
371	composite composite composite composite composite
372	composite composite composite composite composite
373	prime prime prime prime prime
374	composite composite composite composite composite
375	composite composite composite composite composite
376	composite composite composite composite composite
377	composite composite composite composite composite
378	composite composite composite composite composite
379	prime prime prime prime prime
380	composite composite composite composite composite
381	composite composite composite composite composite
382	composite composite composite composite composite
383	prime prime prime prime prime
384	composite composite composite composite composite
385	composite composite composite composite composite
386	composite composite composite composite composite
387	composite composite composite composite composite
388	composite composite composite composite composite
389	prime prime prime prime prime
390	composite composite composite composite composite
391	composite composite composite composite composite
392	composite composite composite composite composite
393	composite composite composite composite composite
394	composite composite composite composite composite
395	composite composite composite composite composite
396	composite composite composite composite composite
397	prime prime prime prime prime
398	composite composite composite composite composite
399	composite composite composite composite composite
400	composite composite composite composite composite
401	prime prime prime prime prime
402	composite composite composite composite composite
403	composite composite composite composite composite
404	composite composite composite composite composite
405	composite composite composite composite composite
406	composite composite composite composite composite
407	composite composite composite composite composite
408	composite composite composite composite composite
409	prime prime prime prime prime
410	composite composite composite composite composite
411	composite composite composite composite composite
412	composite composite composite composite composite
413	composite composite composite composite composite
414	composite composite composite composite composite
415	composite composite composite composite composite
416	composite composite composite composite composite
417	composite composite composite composite composite
418	composite composite composite composite composite
419	prime prime prime prime prime
420	composite composite composite composite composite
421	prime prime prime prime prime
422	composite composite composite composite composite
423	composite composite composite composite composite
424	composite composite composite composite composite
425	composite composite composite composite composite
426	composite composite composite composite composite
427	composite composite composite composite composite
428	composite composite composite composite composite
429	composite composite composite composite composite
430	composite composite composite composite composite
431	prime prime prime prime prime
432	composite composite composite composite composite
433	prime prime prime prime prime
434	composite composite composite composite composite
435	composite composite composite composite composite
436	composite composite composite composite composite
437	composite composite composite composite composite
438	composite composite composite composite composite
439	prime prime prime prime prime
440	composite composite composite composite composite
441	composite composite composite composite composite
442	composite composite composite composite composite
443	prime prime prime prime prime
444	composite composite composite composite composite
445	composite composite composite composite composite
446	composite composite composite composite composite
447	composite composite composite composite composite
448	composite composite composite composite composite
449	prime prime prime prime prime
450	composite composite composite composite composite
451	composite composite composite composite composite
452	composite composite composite composite composite
453	composite composite composite composite composite
454	composite composite composite composite composite
455	composite composite composite composite composite
456	composite composite composite composite composite
457	prime prime prime prime prime
458	composite composite composite composite composite
459	composite composite composite composite composite
460	composite composite composite composite composite
461	prime prime prime prime prime
462	composite composite composite composite composite
463	prime prime prime prime prime
464	composite composite composite composite composite
465	composite composite composite composite composite
466	composite composite composite composite composite
467	prime prime prime prime prime
468	composite composite composite composite composite
469	composite composite composite composite composite
470	composite composite composite composite composite
471	composite composite composite composite composite
472	composite composite composite composite composite
473	composite composite composite composite composite
474	composite composite composite composite composite
475	composite composite composite composite composite
476	composite composite composite composite composite
477	composite composite composite composite composite
478	composite composite composite composite composite
479	prime prime prime prime prime
480	composite composite composite composite composite
481	composite composite composite composite composite
482	composite composite composite composite composite
483	composite composite composite composite composite
484	composite composite composite composite composite
485	composite composite composite composite composite
486	composite composite composite composite composite
487	prime prime prime prime prime
488	composite composite composite composite composite
489	composite composite composite composite composite
490	composite composite composite composite composite
491	prime prime prime prime prime
492	composite composite composite composite composite
493	composite composite composite composite composite
494	composite composite composite composite composite
495	composite composite composite composite composite
496	composite composite composite composite composite
497	composite composite composite composite composite
498	composite composite composite composite composite
499	prime prime prime prime prime
500	composite composite composite composite composite
501	composite composite composite composite composite
502	composite composite composite composite composite
503	prime prime prime prime prime
504	composite composite composite composite composite
505	composite composite composite composite composite
506	composite composite composite composite composite
507	composite composite composite composite composite
508	composite composite composite composite composite
509	prime prime prime prime prime
510	composite composite composite composite composite
511	composite composite composite composite composite
512	composite composite composite composite composite
513	composite composite composite composite composite
514	composite composite composite composite composite
515	composite composite composite composite composite
516	composite composite composite composite composite
517	composite composite composite composite composite
518	composite composite composite composite composite
519	composite composite composite composite composite
520	composite composite composite composite composite
521	prime prime prime prime prime
522	composite composite composite composite composite
523	prime prime prime prime prime
524	composite composite composite composite composite
525	composite composite composite composite composite
526	composite composite composite composite composite
527	composite composite composite composite composite
528	composite composite composite composite composite
529	composite composite composite composite composite
530	composite composite composite composite composite
531	composite composite composite composite composite
532	composite composite composite composite composite
533	composite composite composite composite composite
534	composite composite composite composite composite
535	composite composite composite composite composite
536	composite composite composite composite composite
537	composite composite composite composite composite
538	composite composite composite composite composite
539	composite composite composite composite composite
540	composite composite composite composite composite
541	prime prime prime prime prime
542	composite composite composite composite composite
543	composite composite composite composite composite
544	composite composite composite composite composite
545	composite composite composite composite composite
546	composite composite composite composite composite
547	prime prime prime prime prime
548	composite composite composite composite composite
549	composite composite composite composite composite
550	composite composite composite composite composite
551	composite composite composite composite composite
552	composite composite composite composite composite
553	composite composite composite composite composite
554	composite composite composite composite composite
555	composite composite composite composite composite
556	composite composite composite composite composite
557	prime prime prime prime prime
558	composite composite composite composite composite
559	composite composite composite composite composite
560	composite composite composite composite composite
561	composite composite composite composite composite
562	composite composite composite composite composite
563	prime prime prime prime prime
564	composite composite composite composite composite
565	composite composite composite composite composite
566	composite composite composite composite composite
567	composite composite composite composite composite
568	composite composite composite composite composite
569	prime prime prime prime prime
570	composite composite composite composite composite
571	prime prime prime prime prime
572	composite composite composite composite composite
573	composite composite composite composite composite
574	composite composite composite composite composite
575	composite composite composite composite composite
576	composite composite composite composite composite
577	prime prime prime prime prime
578	composite composite composite composite composite
579	composite composite composite composite composite
580	composite composite composite composite composite
581	composite composite composite composite composite
582	composite composite composite composite composite
583	composite composite composite composite composite
584	composite composite composite composite composite
585	composite composite composite composite composite
586	composite composite composite composite composite
587	prime prime prime prime prime
588	composite composite composite composite composite
589	composite composite composite composite composite
590	composite composite composite composite composite
591	composite composite composite composite composite
592	composite composite composite composite composite
593	prime prime prime prime prime
594	composite composite composite composite composite
595	composite composite composite composite composite
596	composite composite composite composite composite
597	composite composite composite composite composite
598	composite composite composite composite composite
599	prime prime prime prime prime
600	composite composite composite composite composite
601	prime prime prime prime prime
602	composite composite composite composite composite
603	composite composite composite composite composite
604	composite composite composite composite composite
605	composite composite composite composite composite
606	composite composite composite composite composite
607	prime prime prime prime prime
608	composite composite composite composite composite
609	composite composite composite composite composite
610	composite composite composite composite composite
611	composite composite composite composite composite
612	composite composite composite composite composite
613	prime prime prime prime prime
614	composite composite composite composite composite
615	composite composite composite composite composite
616	composite composite composite composite composite
617	prime prime prime prime prime
618	composite composite composite composite composite
619	prime prime prime prime prime
620	composite composite composite composite composite
621	composite composite composite composite composite
622	composite composite composite composite composite
623	composite composite composite composite composite
624	composite composite composite composite composite
625	composite composite composite composite composite
626	composite composite composite composite composite
627	composite composite composite composite composite
628	composite composite composite composite composite
629	composite composite composite composite composite
630	composite composite composite composite composite
631	prime prime prime prime prime
632	composite composite composite composite composite
633	composite composite composite composite composite
634	composite composite composite composite composite
635	composite composite composite composite composite
636	composite composite composite composite composite
637	composite composite composite composite composite
638	composite composite composite composite composite
639	composite composite composite composite composite
640	composite composite composite composite composite
641	prime prime prime prime prime
642	composite composite composite composite composite
643	prime prime prime prime prime
644	composite composite composite composite composite
645	composite composite composite composite composite
646	composite composite composite composite composite
647	prime prime prime prime prime
648	composite composite composite composite composite
649	composite composite composite composite composite
650	composite composite composite composite composite
651	composite composite composite composite composite
652	composite composite composite composite composite
653	prime prime prime prime prime
654	composite composite composite composite composite
655	composite composite composite composite composite
656	composite composite composite composite composite
657	composite composite composite composite composite
658	composite composite composite composite composite
659	prime prime prime prime prime
660	composite composite composite composite composite
661	prime prime prime prime prime
662	composite composite composite composite composite
663	composite composite composite composite composite
664	composite composite composite composite composite
665	composite composite composite composite composite
666	composite composite composite composite composite
667	composite composite composite composite composite
668	composite composite composite composite composite
669	composite composite composite composite composite
670	composite composite composite composite composite
671	composite composite composite composite composite
672	composite composite composite composite composite
673	prime prime prime prime prime
674	composite composite composite composite composite
675	composite composite composite composite composite
676	composite composite composite composite composite
677	prime prime prime prime prime
678	composite composite composite composite composite
679	composite composite composite composite composite
680	composite composite composite composite composite
681	composite composite composite composite composite
682	composite composite composite composite composite
683	prime prime prime prime prime
684	composite composite composite composite composite
685	composite composite composite composite composite
686	composite composite composite composite composite
687	composite composite composite composite composite
688	composite composite composite composite composite
689	composite composite composite composite composite
690	composite composite composite composite composite
691	prime prime prime prime prime
692	composite composite composite composite composite
693	composite composite composite composite composite
694	composite composite composite composite composite
695	composite composite composite composite composite
696	composite composite composite composite composite
697	composite composite composite composite composite
698	composite composite composite composite composite
699	composite composite composite composite composite
700	composite composite composite composite composite
701	prime prime prime prime prime
702	composite composite composite composite composite
703	composite composite composite composite composite
704	composite composite composite composite composite
705	composite composite composite composite composite
706	composite composite composite composite composite
707	composite composite composite composite composite
708	composite composite composite composite composite
709	prime prime prime prime prime
710	composite composite composite composite composite
711	composite composite composite composite composite
712	composite composite composite composite composite
713	composite composite composite composite composite
714	composite composite composite composite composite
715	composite composite composite composite composite
716	composite composite composite composite composite
717	composite composite composite composite composite
718	composite composite composite composite composite
719	prime prime prime prime prime
720	composite composite composite composite composite
721	composite composite composite composite composite
722	composite composite composite composite composite
723	composite composite composite composite composite
724	composite composite composite composite composite
725	composite composite composite composite composite
726	composite composite composite composite composite
727	prime prime prime prime prime
728	composite composite composite composite composite
729	composite composite composite composite composite
730	composite composite composite composite composite
731	composite composite composite composite composite
732	composite composite composite composite composite
733	prime prime prime prime prime
734	composite composite composite composite composite
735	composite composite composite composite composite
736	composite composite composite composite composite
737	composite composite composite composite composite
738	composite composite composite composite composite
739	prime prime prime prime prime
740	composite composite composite composite composite
741	composite composite composite composite composite
742	composite composite composite composite composite
743	prime prime prime prime prime
744	composite composite composite composite composite
745	composite composite composite composite composite
746	composite composite composite composite composite
747	composite composite composite composite composite
748	composite composite composite composite composite
749	composite composite composite composite composite
750	composite composite composite composite composite
751	prime prime prime prime prime
752	composite composite composite composite composite
753	composite composite composite composite composite
754	composite composite composite composite composite
755	composite composite composite composite composite
756	composite composite composite composite composite
757	prime prime prime prime prime
758	composite composite composite composite composite
759	composite composite composite composite composite
760	composite composite composite composite composite
761	prime prime prime prime prime
762	composite composite composite composite composite
763	composite composite composite composite composite
764	composite composite composite composite composite
765	composite composite composite composite composite
766	composite composite composite composite composite
767	composite composite composite composite composite
768	composite composite composite composite composite
769	prime prime prime prime prime
770	composite composite composite composite composite
771	composite composite composite composite composite
772	composite composite composite composite composite
773	prime prime prime prime prime
774	composite composite composite composite composite
775	composite composite composite composite composite
776	composite composite composite composite composite
777	composite composite composite composite composite
778	composite composite composite composite composite
779	composite composite composite composite composite
780	composite composite composite composite composite
781	composite composite composite composite composite
782	composite composite composite composite composite
783	composite composite composite composite composite
784	composite composite composite composite composite
785	composite composite composite composite composite
786	composite composite composite composite composite
787	prime prime prime prime prime
788	composite composite composite composite composite
789	composite composite composite composite composite
790	composite composite composite composite composite
791	composite composite composite composite composite
792	composite composite composite composite composite
793	composite composite composite composite composite
794	composite composite composite composite composite
795	composite composite composite composite composite
796	composite composite composite composite composite
797	prime prime prime prime prime
798	composite composite composite composite composite
799	composite composite composite composite composite
800	composite composite composite composite composite
801	composite composite composite composite composite
802	composite composite composite composite composite
803	composite composite composite composite composite
804	composite composite composite composite composite
805	composite composite composite composite composite
806	composite composite composite composite composite
807	composite composite composite composite composite
808	composite composite composite composite composite
809	prime prime prime prime prime
810	composite composite composite composite composite
811	prime prime prime prime prime
812	composite composite composite composite composite
813	composite composite composite composite composite
814	composite composite composite composite composite
815	composite composite composite composite composite
816	composite composite composite composite composite
817	composite composite composite composite composite
818	composite composite composite composite composite
819	composite composite composite composite composite
820	composite composite composite composite composite
821	prime prime prime prime prime
822	composite composite composite composite composite
823	prime prime prime prime prime
824	composite composite composite composite composite
825	composite composite composite composite composite
826	composite composite composite composite composite
827	prime prime prime prime prime
828	composite composite composite composite composite
829	prime prime prime prime prime
830	composite composite composite composite composite
831	composite composite composite composite composite
832	composite composite composite composite composite
833	composite composite composite composite composite
834	composite composite composite composite composite
835	composite composite composite composite composite
836	composite composite composite composite composite
837	composite composite composite composite composite
838	composite composite composite composite composite
839	prime prime prime prime prime
840	composite composite composite composite composite
841	composite composite composite composite composite
842	composite composite composite composite composite
843	composite composite composite composite composite
844	composite composite composite composite composite
845	composite composite composite composite composite
846	composite composite composite composite composite
847	composite composite composite composite composite
848	composite composite composite composite composite
849	composite composite composite composite composite
850	composite composite composite composite composite
851	composite composite composite composite composite
852	composite composite composite composite composite
853	prime prime prime prime prime
854	composite composite composite composite composite
855	composite composite composite composite composite
856	composite composite composite composite composite
857	prime prime prime prime prime
858	composite composite composite composite composite
859	prime prime prime prime prime
860	composite composite composite composite composite
861	composite composite composite composite composite
862	composite composite composite composite composite
863	prime prime prime prime prime
864	composite composite composite composite composite
865	composite composite composite composite composite
866	composite composite composite composite composite
867	composite composite composite composite composite
868	composite composite composite composite composite
869	composite composite composite composite composite
870	composite composite composite composite composite
871	composite composite composite composite composite
872	composite composite composite composite composite
873	composite composite composite composite composite
874	composite composite composite composite composite
875	composite composite composite composite composite
876	composite composite composite composite composite
877	prime prime prime prime prime
878	composite composite composite composite composite
879	composite composite composite composite composite
880	composite composite composite composite composite
881	prime prime prime prime prime
882	composite composite composite composite composite
883	prime prime prime prime prime
884	composite composite composite composite composite
885	composite composite composite composite composite
886	composite composite composite composite composite
887	prime prime prime prime prime
888	composite composite composite composite composite
889	composite composite composite composite composite
890	composite composite composite composite composite
891	composite composite composite composite composite
892	composite composite composite composite composite
893	composite composite composite composite composite
894	composite composite composite composite composite
895	composite composite composite composite composite
896	composite composite composite composite composite
897	composite composite composite composite composite
898	composite composite composite composite composite
899	composite composite composite composite composite
900	composite composite composite composite composite
901	composite composite composite composite composite
902	composite composite composite composite composite
903	composite composite composite composite composite
904	composite composite composite composite composite
905	composite composite composite composite composite
906	composite composite composite composite composite
907	prime prime prime prime prime
908	composite composite composite composite composite
909	composite composite composite composite composite
910	composite composite composite composite composite
911	prime prime prime prime prime
912	composite composite composite composite composite
913	composite composite composite composite composite
914	composite composite composite composite composite
915	composite composite composite composite composite
916	composite composite composite composite composite
917	composite composite composite composite composite
918	composite composite composite composite composite
919	prime prime prime prime prime
920	composite composite composite composite composite
921	composite composite composite composite composite
922	composite composite composite composite composite
923	composite composite composite composite composite
924	composite composite composite composite composite
925	composite composite composite composite composite
926	composite composite composite composite composite
927	composite composite composite composite composite
928	composite composite composite composite composite
929	prime prime prime prime prime
930	composite composite composite composite composite
931	composite composite composite composite composite
932	composite composite composite composite composite
933	composite composite composite composite composite
934	composite composite composite composite composite
935	composite composite composite composite composite
936	composite composite composite composite composite
937	prime prime prime prime prime
938	composite composite composite composite composite
939	composite composite composite composite composite
940	composite composite composite composite composite
941	prime prime prime prime prime
942	composite composite composite composite composite
943	composite composite composite composite composite
944	composite composite composite composite composite
945	composite composite composite composite composite
946	composite composite composite composite composite
947	prime prime prime prime prime
948	composite composite composite composite composite
949	composite composite composite composite composite
950	composite composite composite composite composite
951	composite composite composite composite composite
952	composite composite composite composite composite
953	prime prime prime prime prime
954	composite composite composite composite composite
955	composite composite composite composite composite
956	composite composite composite composite composite
957	composite composite composite composite composite
958	composite composite composite composite composite
959	composite composite composite composite composite
960	composite composite composite composite composite
961	composite composite composite composite composite
962	composite composite composite composite composite
963	composite composite composite composite composite
964	composite composite composite composite composite
965	composite composite composite composite composite
966	composite composite composite composite composite
967	prime prime prime prime prime
968	composite composite composite composite composite
969	composite composite composite composite composite
970	composite composite composite composite composite
971	prime prime prime prime prime
972	composite composite composite composite composite
973	composite composite composite composite composite
974	composite composite composite composite composite
975	composite composite composite composite composite
976	composite composite composite composite composite
977	prime prime prime prime prime
978	composite composite composite composite composite
979	composite composite composite composite composite
980	composite composite composite composite composite
981	composite composite composite composite composite
982	composite composite composite composite composite
983	prime prime prime prime prime
984	composite composite composite composite composite
985	composite composite composite composite composite
986	composite composite composite composite composite
987	composite composite composite composite composite
988	composite composite composite composite composite
989	composite composite composite composite composite
990	composite composite composite composite composite
991	prime prime prime prime prime
992	composite composite composite composite composite
993	composite composite composite composite composite
994	composite composite composite composite composite
995	composite composite composite composite composite
996	composite composite composite composite composite
997	prime prime prime prime prime
998	composite composite composite composite composite
999	composite composite composite composite composite
>>> 
```

Intuitively, it can be seen that these five methods can get the same answer. In the actual program, we generally do not print the answer but check it inside the program with logic.&#x20;

In general, check the program is correct for millions of times does not take more than 1 minute. And with such a large amount of data, it is almost certain that the program is correct. (Sometimes we need special value detection, that is, enter some special values to check the correctness of the program, such as 0 or 1 or 2, because some programs work well under random numbers, but special values will not work.)

## Statistics

Start time of this page: February 2, 2022

Completion time of this page: February 4, 2022
