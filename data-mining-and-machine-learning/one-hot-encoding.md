---
description: Multi-classification problem
coverY: 0
---

# One Hot Encoding

{% embed url="https://www.tensorflow.org/api_docs/python/tf/keras/datasets" %}

tf.keras.datasets provides some data sets:

1. [`boston_housing`](https://www.tensorflow.org/api\_docs/python/tf/keras/datasets/boston\_housing) module: Public API for tf.keras.datasets.boston\_housing namespace.
2. [`cifar10`](https://www.tensorflow.org/api\_docs/python/tf/keras/datasets/cifar10) module: Public API for tf.keras.datasets.cifar10 namespace.
3. [`cifar100`](https://www.tensorflow.org/api\_docs/python/tf/keras/datasets/cifar100) module: Public API for tf.keras.datasets.cifar100 namespace.
4. [`fashion_mnist`](https://www.tensorflow.org/api\_docs/python/tf/keras/datasets/fashion\_mnist) module: Public API for tf.keras.datasets.fashion\_mnist namespace.
5. [`imdb`](https://www.tensorflow.org/api\_docs/python/tf/keras/datasets/imdb) module: Public API for tf.keras.datasets.imdb namespace.
6. [`mnist`](https://www.tensorflow.org/api\_docs/python/tf/keras/datasets/mnist) module: Public API for tf.keras.datasets.mnist namespace.
7. [`reuters`](https://www.tensorflow.org/api\_docs/python/tf/keras/datasets/reuters) module: Public API for tf.keras.datasets.reuters namespace.

Today we use the cifar10 data set to explain:

{% hint style="success" %}
<mark style="color:green;">**Basic data analysis process**</mark>
{% endhint %}

When we are prepare to use a new data set, the first thing is to download the data set.

The cifar10 data set is in tensorflow, so the first thing is to install tensorflow.

```
pip install tensorflow-cpu
```

Enter the above command in the CMD command prompt (search in win10)

tensorflow will be installed on your computer. Please note that tensorflow is a deep learning library, the library has two versions of CPU and GPU, because the GPU version is extremely troublesome to install, so I recommend installing the CPU version here.

I will tell you about the GPU version installation in the anaconda tutorial.

{% hint style="danger" %}
Deep learning requires a huge amount of calculation. Generally, the CPU has only 4-16 cores, and even the most powerful CPU today will generally not exceed 100 cores. That is to say, if I want to train a deep learning model, a CPU can only train 16 data at a time, and deep learning generally contains tens of thousands of data and extremely complex networks. So using CPU to train deep learning often takes a very long time.


{% endhint %}





























## Statistics

Start time of this page: December 25, 2021

Completion time of this page: December 28, 2021
