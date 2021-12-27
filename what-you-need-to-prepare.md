---
description: Hardware resource requirements
coverY: 0
---

# What you need to prepare

Python has higher hardware requirements than other languages. Of course, this is all empirical. Python actually has kind of the same running time as C/C++ and Java.

## Computer composition

### Computing unit

#### Central Processing Unit (CPU)

![CPU](<.gitbook/assets/image (8).png>)

The CPU is responsible for the main calculations of the computer, so the core of a computer is the CPU.

CPUs generally have multiple cores, but python's support for multi-core is not good, so unless you are very good at multi-processes, you should have a single-core CPU with high performance. The specific performance is that the cache of the CPU is larger, and The frequency is very fast.

![Speed and cache size](<.gitbook/assets/image (2).png>)

The same CPU generates a lot of heat, so you should have a good CPU cooler. CPU radiators are divided into water-cooled and air-cooled. I personally recommend air-cooling, because electronic equipment will short-circuit when exposed to water, and water-cooling has a certain risk of leakage. In addition, water-cooling is much more expensive than air-cooling, but the heat dissipation effect may not be much better. , So air cooling has a high cost performance and safety.

![This kind of radiator has the best heat dissipation effect](<.gitbook/assets/image (7).png>)

#### Graphics Processing Unit (GPU)

GPU is a graphics computing unit. Unlike the CPU, the CPU is powerful, but generally there are no more than 16 cores, and each core can process complex instructions, just like a scientist. The GPU contains thousands of cores with simple functions, each of which can work in parallel and independently, just like a lot of workers.

When dealing with complex problems, we need scientists, but when dealing with a large number of simple problems, we need enough workers. We let scientists design blueprints for workers and guide them in their work, and many workers will return the results after completing the construction then Give to the scientist to do the acceptance. This is the job of the GPU.

Therefore, the workflow of the graphics card is as follows: CPU processing data is sent to the graphics card and tells the graphics card what each core should do. After the graphics card receives the data and instructions, it performs high-intensity parallel calculations, and finally feeds back the calculation results to the CPU, and the CPU Print the calculation results on the screen and you will see the calculation result.

GPU is mainly used in two places, one is graphics rendering, and the other is deep learning.

If you are not writing python programs for these two purposes, then a normal notebook core graphics card can meet your needs.

![The most common GPU](<.gitbook/assets/image (15).png>)

GPU has two parameters: memory size and computing power.

Of course, if your graphics card has a huge memory size and extremely powerful computing power, it is best, but we generally cannot afford such overhead.

If you are using python for graphics rendering, then the general game graphics card can meet your needs (as long as you don't buy a bad graphics card)

If you are doing deep learning, then the best graphics card is NVIDIA’s computing card:

![V100 computing card @ $8000 ](<.gitbook/assets/image (9).png>)

This kind of graphics card is generally configured on the server and is cooled by a violent fan with huge noise. The general civilian computer rarely has such a computing card. This kind of computing card has only PCIE slot, and does not have any graphics output interface (DVI or HDMI or VGA). So this kind of graphics card can only be used for calculations.

The video memory size of the computing card is generally 16G and above, so in general, the general model does not need to worry about the video memory usage problem.

The reason why computing cards are expensive is that computing cards have several times of the computing power of general graphics cards. It is very likely that the CPU has not yet prepared the data, and the GPU has already completed the calculation. So you should use multiple processes when using a computing card.

![Recommended graphics card](<.gitbook/assets/image (10).png>)













## Statistics

Start time of this page: December 27, 2021

Completion time of this page: December 27, 2021
