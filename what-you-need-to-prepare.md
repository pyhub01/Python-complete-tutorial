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

Therefore, the workflow of the graphics card is as follows: CPU processing data which sent to the graphics card and tells the graphics card what each core should do. After the graphics card receives the data and instructions, it performs high-intensity parallel calculations, and finally feeds back the calculation results to the CPU, and the CPU Print the calculation results on the screen and you will see the calculation result.

**So the working process of GPU is actually the cooperation of GPU and CPU. In other words, if your GPU is too strong and the CPU is too weak, then the CPU may not have preprocessed the data, and the GPU will complete the calculation. Or your GPU is too weak and the CPU is too strong, then the CPU has to wait for the GPU to process the data. Therefore, the capabilities of the CPU and GPU must be properly matched, so that they can work together perfectly, shorten the running time, and reduce the vacancy rate of the equipment.**

Under normal circumstances, the performance of your game graphics card is much weaker than the CPU, so there is no need to worry about the problem of excessive CPU.



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

**Most people use gaming graphics cards:**

![Recommended graphics card](<.gitbook/assets/image (10).png>)

I also recommend that you buy and use gaming graphics cards, because if you give up python programming and deep learning, such graphics cards can still play games or sell.

{% hint style="danger" %}
Please do not buy second-hand graphics cards as much as possible, because graphics cards are often used for mining, and mining is very harmful to the graphics cards.

Many mining cards are easily damaged or many functions are already unstable. Unless you can be sure that the graphics card is not a mining card, you should be extra cautious.
{% endhint %}

The performance of the graphics card is divided into two points, the first is the size of the video memory, and the second is the strength of the computing power.

The video memory size is the most important, because if your model cannot fit in the video memory, then your model cannot run on the graphics card!

So I recommend buying a large-capacity graphics card. For example, the RTX3060 has 12GB of video memory but the price is very cheap (of course, you can’t buy the RTX3060 in 2020 2021 2022 or even later because everyone is mining ethereum And other cryptocurrencies that are mined with graphics cards now) or the RTX3090 has 24G of video memory, which is slightly more expensive but has strong performance.

The computing power of the graphics card is actually not very important. Of course, the graphics memory and computing power of the graphics card earlier than GTX960 are not enough (when the computing power is below a certain level, deep learning cannot be performed, but this kind of graphics card should not be available in shop now) . Another important point is that the M-series graphics card used by the laptop computers and tablet is a weakened version of the desktop computer graphics card. The heat dissipation and power consumption of the M-series graphics card may cause damage to the notebook (for example, one of my previous notebooks exploded because of long-term deep learning).

{% hint style="danger" %}
The best way to buy graphics cards and CPUs is to evaluate the product's cost-effectiveness and performance.

We should choose graphics cards and CPUs that are more cost-effective and have higher running scores.

The following is a very good evaluation score and cost-effective website.

**(The data on this website is not so accurate, so it is more appropriate as a reference and approximate ranking)**
{% endhint %}

{% embed url="https://www.cpubenchmark.net/cpu_value_available.html" %}
cpu cost performance
{% endembed %}

{% embed url="https://www.videocardbenchmark.net/gpu_value.html" %}
GPU cost performance
{% endembed %}

### Random access memory(RAM)

![RAM](<.gitbook/assets/image (12).png>)

RAM is a storage method: when our computer is powered on, it can storeage data. When the computer is powered off, the stored content disappears with the power off.

RAM is different from our hard disk. When the power is off, the data in the hard disk still exists, but the data in RAM disappears.

{% hint style="success" %}
<mark style="color:green;">**The speed of RAM that disappears after a power off is much faster than that of a disk that does not disappear after a power off.**</mark>&#x20;

<mark style="color:green;">**Because the two principles are different, the disk can store data permanently, whether it is stored in the form of a magnetic field or in the form of electric charge, it takes longer than RAM.**</mark>

<mark style="color:green;">**If you are interested in the principles of rom and ram, then please read the article about transistors and MOSFETs and how MOSFETs store electric charge.**</mark>
{% endhint %}

{% hint style="danger" %}
<mark style="color:red;">**The memory is fast, dozens of times faster than the disk, but still much slower than the CPU. So the bottleneck of many programs is to read data from memory. This is why you have a fast CPU but cannot process data at this speed.**</mark>

<mark style="color:red;">**So improving your memory is very important, because it will directly increase the execution speed of your program. Especially for big data programs.**</mark>
{% endhint %}

RAM has three important parameters, one is ddrx, the other is speed, and the other is capacity.

ddrx is generally ddr3 or ddr4, these are two types of memory chips, and their working principles are different. ddr3 is half the speed of ddr4, so if you have ddr4 memory, then your program execution speed will also increase.

The second parameter is the speed and the number of instruction cycles: the memory has different frequencies such as **2133MHZ, 2400MHZ, 2666MHZ, 3000MHZ, 3200MHZ**. The higher the frequency, the faster the memory speed, and the running speed of your program will increase accordingly.

The number of instruction cycles refers to how many cycles of instructions are used to read data from the memory. For example, **CL16, CL19, CL22** are common. The smaller the number of instruction cycles, the better. If your instruction cycle number is CL22 and the memory frequency is 3200MHZ, then you need to read an instruction The time spent is: 1/3200MHZ\*22=6.875ns. (The actual time may be different from this)&#x20;

These previous parameters will make your program run faster, if you deal with big data, then the effect will be more significant.

{% hint style="danger" %}
<mark style="color:red;">**There are many things to note about memory:**</mark>

<mark style="color:red;">**The first is to check what memory your motherboard supports. If you buy unsupported memory, it may not be plugged into the motherboard (ddr3 and ddr4 have different slots) or cannot be read correctly.**</mark>

<mark style="color:red;">**The second is that memory modules are generally dual-channel, which means that if you have two memory slots, one memory slot has been inserted into 8GB 2400MHZ CL22 memory, then the other memory slot should also be inserted exactly the same. Memory (including the brand must be the same), so as to maximize compatibility. If you insert a 16GB memory, it may not be recognized. If you insert 3200MHZ memory, the motherboard will down-clock this 3200MHZ memory to 2400MHZ to synchronize with another memory. So you should ensure the consistency of dual-channel memory.**</mark>&#x20;

Unless you know how to mix memory <mark style="color:red;">**with different size**</mark> and are willing to take the risk of memory errors, or you can try whether it succeeds, and return the product if it fails.
{% endhint %}























## Statistics

Start time of this page: December 27, 2021

Completion time of this page: December 27, 2021
