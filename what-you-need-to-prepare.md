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

![Speed and cache size](<.gitbook/assets/image (2) (1).png>)

The same CPU generates a lot of heat, so you should have a good CPU cooler. CPU radiators are divided into water-cooled and air-cooled. I personally recommend air-cooling, because electronic equipment will short-circuit when exposed to water, and water-cooling has a certain risk of leakage. In addition, water-cooling is much more expensive than air-cooling, but the heat dissipation effect may not be much better. , So air cooling has a high cost performance and safety.

![This kind of radiator has the best heat dissipation effect](<.gitbook/assets/image (7) (1).png>)

#### Graphics Processing Unit (GPU)

GPU is a graphics computing unit. Unlike the CPU, the CPU is powerful, but generally there are no more than 16 cores, and each core can process complex instructions, just like a scientist. The GPU contains thousands of cores with simple functions, each of which can work in parallel and independently, just like a lot of workers.

When dealing with complex problems, we need scientists, but when dealing with a large number of simple problems, we need enough workers. We let scientists design blueprints for workers and guide them in their work, and many workers will return the results after completing the construction then Give to the scientist to do the acceptance. This is the job of the GPU.

Therefore, the workflow of the graphics card is as follows: CPU processing data which sent to the graphics card and tells the graphics card what each core should do. After the graphics card receives the data and instructions, it performs high-intensity parallel calculations, and finally feeds back the calculation results to the CPU, and the CPU Print the calculation results on the screen and you will see the calculation result.

**So the working process of GPU is actually the cooperation of GPU and CPU. In other words, if your GPU is too strong and the CPU is too weak, then the CPU may not have preprocessed the data, and the GPU will complete the calculation. Or your GPU is too weak and the CPU is too strong, then the CPU has to wait for the GPU to process the data. Therefore, the capabilities of the CPU and GPU must be properly matched, so that they can work together perfectly, shorten the running time, and reduce the vacancy rate of the equipment.**

Under normal circumstances, the performance of your game graphics card is much weaker than the CPU, so there is no need to worry about the problem of excessive CPU.



GPU is mainly used in two places, one is graphics rendering, and the other is deep learning.

If you are not writing python programs for these two purposes, then a normal notebook core graphics card can meet your needs.

![The most common GPU](<.gitbook/assets/image (15) (1) (1).png>)

GPU has two parameters: memory size and computing power.

Of course, if your graphics card has a huge memory size and extremely powerful computing power, it is best, but we generally cannot afford such overhead.

If you are using python for graphics rendering, then the general game graphics card can meet your needs (as long as you don't buy a bad graphics card)

If you are doing deep learning, then the best graphics card is NVIDIA’s computing card:

![V100 computing card @ $8000 ](<.gitbook/assets/image (9).png>)

This kind of graphics card is generally configured on the server and is cooled by a violent fan with huge noise. The general civilian computer rarely has such a computing card. This kind of computing card has only PCIE slot, and does not have any graphics output interface (DVI or HDMI or VGA). So this kind of graphics card can only be used for calculations.

The video memory size of the computing card is generally 16G and above, so in general, the general model does not need to worry about the video memory usage problem.

The reason why computing cards are expensive is that computing cards have several times of the computing power of general graphics cards. It is very likely that the CPU has not yet prepared the data, and the GPU has already completed the calculation. So you should use multiple processes when using a computing card.

**Most people use gaming graphics cards:**

![Recommended graphics card](<.gitbook/assets/image (10) (1).png>)

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

{% hint style="info" %}
<mark style="color:blue;">**Once the CPU and GPU are installed successfully, as long as the radiator works normally and keeps the CPU and GPU below 90 degrees Celsius, the CPU and GPU are difficult to break. So CPU and GPU are not consumables.**</mark>
{% endhint %}

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

<mark style="color:red;">**Unless you know how to mix memory with different size and are willing to take the risk of memory errors, or you can try whether it succeeds, and return the product if it fails.**</mark>
{% endhint %}

{% hint style="info" %}
<mark style="color:blue;">**Once the memory is installed successfully, it is generally difficult to break (unless you overclock too much and the temperature is too high or accidentally spill Coke on it), so memory is not a consumables.**</mark>
{% endhint %}

### Read only memory (ROM)

![UV erasable read-only memory](<.gitbook/assets/image (17) (1) (1) (1).png>)

The name read-only memory comes from the 1970s, when the disk at that time is shown in the picture above (there are even ertlier read-only memories, The ertlier the ROM, the more unconvent to use.). This chip requires a special programmer to write data into it. When in use, data can only be read but not written. When we need to change the data, we need to use ultraviolet rays into the small quartz window in the middle of the chip. The high-energy ultraviolet light will excite the stored charges and clear the data in the chip.

![Mask ROM](<.gitbook/assets/image (13) (1).png>)

Mask ROM is one of the oldest ROMs. This type of ROM writes data when it leaves the factory and cannot modify the data once it leaves the factory. Each transistor as above represents data 1, and blank represents data 0.

So when you look at today's disks, you will have an illusion, that is: It is obvious that we can easily write data, why is this thing called a read-only memory. The reason lies in the above two tell you th story about the primitive and ancient read-only memories.

#### HDD

![HDD](<.gitbook/assets/image (16) (1) (1) (1).png>)

The abbreviation of Hard drive disk is HDD. HDD is an ancient computer hard disk. This hard disk uses a robotic arm to read and write the contents of the disk. Since it takes time for the robot arm to be in place and to rotate, the HDD speed is very slow. Especially when we try to put a large amount of fragmented data on the HDD, it will take a long time for the robotic arm to find the data and read the data.

In the middle of the HDD is a floppy disk. This disk rotates at a high speed when the hard disk is working, usually 5400RPM (round per minute) or 7200RPM, or even 10000RPM (these speed depends on the factory positioning of the disk itself). Mechanical aging determines the life of the disk. (The aging of the magnetic head, the ingress of dust, and the degaussing of the disk will also affect the life of the disk)

Because HDDs rely on mechanical structures to store data, HDDs are very fragile, and mechanical arm failures, power failure, bumps, and magnets can easily destroy this delicate device. Therefore, the content stored on the HDD is not safe.

#### SSD

![HDD & SSD](<.gitbook/assets/image (14) (1).png>)

SSD is the abbreviation of solid state drive. Solid state drives use chips to store data, which is very different from mechanical hard drives.

The use of a chip to store data in a solid-state drive will increase the reliability of the data (it is not easy to damage the data due to bumps and magnets), and will reduce the weight of the disk.

But because electric charge is used to store data, it is easy to damage the SSD if there is static electricity, and static electricity is relatively easy to occur.

![TLC in 2020 and QLC after 2025](<.gitbook/assets/image (17) (1) (1).png>)

Solid state drives also have a wide range of concerns, that is, life issues. Solid state drives rely on electric charge to store data, and the charge is stored in the MOSFET. The first problem is that the charge will leak slowly, when the leakage reaches a certain level. , The data in the solid state drive will be lost, and the charge leakage rate is proportional to the three-half square of the temperature (thermodynamic formula). That is to say, the problem of charge leakage becomes extremely serious as the temperature rises.

If the room temperature is 20 degrees, the charge will leak out in 5 years, and if the room temperature is 30 degrees, the charge will leak out in only 2-3 years. So your data may disappear within 2-3 years, unless you intermittently power on your SSD. In this case, the data is not secure.

In addition, in order to increase the capacity and cost of the solid state drive, new technologies such as TLC and QLC are adopted, which reduces the life of the solid state drive, but this is fine, because the current life of the 1TB solid state drive is still 300-600TBW, which is Say that a 1TB solid state drive needs to write 300-600TB of data to be damaged, and few people can write so much data in 10-20 years.

{% hint style="danger" %}
<mark style="color:red;">**It is worth noting that modern hard drives use cache to improve disk performance (make writing and reading faster). The cache is composed of RAM, which means that all data in the RAM cache will disappear once the power is turned off.**</mark>

<mark style="color:red;">**And RAM may store very important data, once these data is lost, it will damage the integrity of the information. What's more serious is that some of the hard disk's own data is also stored in RAM. If the power is suddenly cut off, the hard disk may be directly unreadable, thereby damaging the hard disk.**</mark>

<mark style="color:red;">**Therefore, a power failure will cause serious problems with the hard disk! We should 100% avoid power failure of the hard drive!**</mark>
{% endhint %}

#### UPS

In order to avoid damage to the hard disk due to sudden power failure, an uninterruptible power supply is introduced.

The simplest uninterruptible power supply is the battery of mobile phones and laptops. Battery exhaustion can be estimated, so the system will force the hard disk to write the cache to the hard disk before the battery is almost exhausted to avoid data loss and hard disk damage. So devices with batteries do not need to worry about sudden power failures.

For desktop computers and servers that contain important data, UPS is necessary.

![Home UPS](<.gitbook/assets/image (15) (1).png>)

The UPS has large and small, and the small is as large as a power strip, but its internal battery can provide short-term power supply in the event of a power failure. If the power is interrupted, the user needs to back up the data in time and shut down the computer.

Large data centers need to use diesel generator UPS, which usually does not need us to consider.

![data center](<.gitbook/assets/image (14).png>)

#### data center

If your programs and data are very important, storing in an online cloud disk is a good choice. First of all, the online cloud disk is very safe. Your data will follow principles such as 3-2-1 (3: store 3 complete files, one original Add two copies. 2: Keep the files on at least two different media. 1: Keep one copy in a different place.). And you only need to spend relatively little money to maintain your data service.

Cloud disks have certain risks. If you don't want your data to be exposed to public, then you'd better build your own private cloud disk.

{% hint style="success" %}
<mark style="color:green;">**About data security**</mark>
{% endhint %}

Data security is a very important topic. You must adopt certain security strategies to ensure that your data is not leaked or maliciously tampered with. This requires a certain cryptographic foundation, which will be explained in subsequent chapters.

{% hint style="success" %}
<mark style="color:green;">**Data integrity**</mark>
{% endhint %}

We have already talked about the fragility of hard disks before, so if we combine multiple hard disks and place one data on multiple disks to form a disk array, then we can effectively avoid the problem of data loss due to damage to a single disk. It is possible that the same disk fails, but if 2 or 3 disks fail at the same time, it is a small probability event. If we can make the data redundant, then we can guarantee us with great probability Data integrity.

![RAID 5](<.gitbook/assets/image (18).png>)

The picture shows the raid5 scheme that can tolerate any one-disk failure but the data integrity is not destroyed. Here we do not discuss the implementation details of raid5, we will discuss in detail in the database section later.

In order to realize raid disk array solutions such as raid1, raid5, raid6, and raid10. We may need raid expansion cards or hard drive docks or NAS (Network Attached Storage). The specific implementation is relatively simple. Many data integrity solutions are mature and have graphical interfaces.

### Motherboard and power supply

The motherboard, power supply, cooling fan, and chassis provide a platform for all of the above. Among them, there is less content that needs to be explained.

It is worth noting that the motherboard needs to be compatible with your CPU, GPU, memory, and hard drive. Many motherboards have restrictions on the size of memory. You need to read your motherboard instructions carefully. At the same time, motherboards have different sizes. If the motherboard you buy is too large, you may not be able to install it in a mini-size chassis.

Regarding the power supply: You should ensure that the output power of the power supply is greater than the total power of your hardware, and retain 20% of the wealth. Otherwise, your power supply may explode or catch fire due to excessive current.

{% hint style="danger" %}
<mark style="color:red;">**Keeping the computer at a low temperature is very important, because high temperature will increase the electronic drift rate in the chip and accelerate the aging of the chip. At the same time, if the chip temperature is too high, the chip's own temperature protection will be triggered, and the chip will reduce its load. And frequency, your program will also be greatly affected.**</mark>
{% endhint %}

## Python programming computer recommendations

The type of code you write needs to match the type of your computer.

For example, if the code you write is ordinary object-oriented programming or web page production or basic visualization, then any tablet, laptop, or even mobile phone can meet your requirements.

But if you want to do more complex visualization, you need a laptop or desktop computer with a discrete graphics card.

If you are doing machine learning then it is recommended that you have a desktop computer, but not a very advanced graphics card.

If you do deep learning, then you need a better graphics card, and the performance of the laptop is not enough at this time.

If you are doing large-scale deep learning models, it is recommended that you use a server-level supercomputer.

## Statistics

Start time of this page: December 27, 2021

Completion time of this page: December 27, 2021
