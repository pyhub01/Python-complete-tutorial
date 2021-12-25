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

I will tell you about the GPU version installation in the anaconda and deeplearning tutorial.

{% hint style="danger" %}
Deep learning requires a huge amount of calculation. Generally, the CPU has only 4-16 cores, and even the most powerful CPU today will generally not exceed 100 cores. That is to say, if I want to train a deep learning model, a CPU can only train 16 data at a time, and deep learning generally contains tens of thousands of data and extremely complex networks. So using CPU to train deep learning often takes a very long time.

However, GPUs often have hundreds of thousands of cores, so when we use GPUs for calculations, they are dozens of times faster than CPUs, which compresses the calculations that would otherwise take several days to dozens of minutes to dozens of minutes.

New GPUs often have TPU cores (computing cores that only support integer numbers, and deep learning often does not require such high precision), and these tensor cores often have faster computing speeds.

Designing GPU computing programs is a very complicated thing. Fortunately, libraries like tensorflow have helped us design programs. The same program can run on both the CPU and the GPU.
{% endhint %}

Then we can load the cifar data set and visualize it:

```python
from tensorflow.keras.datasets import cifar10

(x_train, y_train), (x_test, y_test) = cifar10.load_data()

print('x_train.shape =', x_train.shape)
print('y_train.shape =', y_train.shape)

print()

print('x_train[:5] =', x_train[:5])
print('y_train[:5] =', y_train[:5])

import matplotlib.pyplot as plt

for i in range(1, 31):
    plt.subplot(5, 6, i)
    plt.imshow(x_train[i])
    plt.title('label={}'.format(y_train[i]))
    plt.axis('off')

plt.tight_layout()
plt.show()
```

The output is as follows:

```python
x_train.shape = (50000, 32, 32, 3)
y_train.shape = (50000, 1)

x_train[:5] = [[[[ 59  62  63]
   [ 43  46  45]
   [ 50  48  43]
   ...
   [158 132 108]
   [152 125 102]
   [148 124 103]]

  [[ 16  20  20]
   [  0   0   0]
   [ 18   8   0]
   ...
   [123  88  55]
   [119  83  50]
   [122  87  57]]

  [[ 25  24  21]
   [ 16   7   0]
   [ 49  27   8]
   ...
   [118  84  50]
   [120  84  50]
   [109  73  42]]

  ...

  [[208 170  96]
   [201 153  34]
   [198 161  26]
   ...
   [160 133  70]
   [ 56  31   7]
   [ 53  34  20]]

  [[180 139  96]
   [173 123  42]
   [186 144  30]
   ...
   [184 148  94]
   [ 97  62  34]
   [ 83  53  34]]

  [[177 144 116]
   [168 129  94]
   [179 142  87]
   ...
   [216 184 140]
   [151 118  84]
   [123  92  72]]]


 [[[154 177 187]
   [126 137 136]
   [105 104  95]
   ...
   [ 91  95  71]
   [ 87  90  71]
   [ 79  81  70]]

  [[140 160 169]
   [145 153 154]
   [125 125 118]
   ...
   [ 96  99  78]
   [ 77  80  62]
   [ 71  73  61]]

  [[140 155 164]
   [139 146 149]
   [115 115 112]
   ...
   [ 79  82  64]
   [ 68  70  55]
   [ 67  69  55]]

  ...

  [[175 167 166]
   [156 154 160]
   [154 160 170]
   ...
   [ 42  34  36]
   [ 61  53  57]
   [ 93  83  91]]

  [[165 154 128]
   [156 152 130]
   [159 161 142]
   ...
   [103  93  96]
   [123 114 120]
   [131 121 131]]

  [[163 148 120]
   [158 148 122]
   [163 156 133]
   ...
   [143 133 139]
   [143 134 142]
   [143 133 144]]]


 [[[255 255 255]
   [253 253 253]
   [253 253 253]
   ...
   [253 253 253]
   [253 253 253]
   [253 253 253]]

  [[255 255 255]
   [255 255 255]
   [255 255 255]
   ...
   [255 255 255]
   [255 255 255]
   [255 255 255]]

  [[255 255 255]
   [254 254 254]
   [254 254 254]
   ...
   [254 254 254]
   [254 254 254]
   [254 254 254]]

  ...

  [[113 120 112]
   [111 118 111]
   [105 112 106]
   ...
   [ 72  81  80]
   [ 72  80  79]
   [ 72  80  79]]

  [[111 118 110]
   [104 111 104]
   [ 99 106  98]
   ...
   [ 68  75  73]
   [ 70  76  75]
   [ 78  84  82]]

  [[106 113 105]
   [ 99 106  98]
   [ 95 102  94]
   ...
   [ 78  85  83]
   [ 79  85  83]
   [ 80  86  84]]]


 [[[ 28  25  10]
   [ 37  34  19]
   [ 38  35  20]
   ...
   [ 76  67  39]
   [ 81  72  43]
   [ 85  76  47]]

  [[ 33  28  13]
   [ 34  30  14]
   [ 32  27  12]
   ...
   [ 95  82  55]
   [ 96  82  56]
   [ 85  72  45]]

  [[ 39  32  15]
   [ 40  33  17]
   [ 57  50  33]
   ...
   [ 93  76  52]
   [107  89  66]
   [ 95  77  54]]

  ...

  [[ 83  73  52]
   [ 87  77  56]
   [ 84  74  52]
   ...
   [ 99  93  70]
   [ 90  84  61]
   [ 81  75  52]]

  [[ 88  72  51]
   [ 90  74  52]
   [ 93  77  56]
   ...
   [ 80  74  53]
   [ 76  70  49]
   [ 82  76  55]]

  [[ 97  78  56]
   [ 94  75  53]
   [ 93  75  53]
   ...
   [ 54  47  28]
   [ 63  56  37]
   [ 72  65  46]]]


 [[[170 180 198]
   [168 178 196]
   [177 185 203]
   ...
   [162 179 215]
   [158 178 214]
   [157 177 212]]

  [[168 181 198]
   [172 185 201]
   [171 183 200]
   ...
   [159 177 212]
   [156 176 211]
   [154 174 209]]

  [[154 170 186]
   [149 165 181]
   [129 144 162]
   ...
   [161 178 214]
   [157 177 212]
   [154 174 209]]

  ...

  [[ 74  84  80]
   [ 76  85  81]
   [ 78  85  82]
   ...
   [ 71  75  78]
   [ 68  72  75]
   [ 61  65  68]]

  [[ 68  76  77]
   [ 69  77  78]
   [ 72  79  78]
   ...
   [ 76  80  83]
   [ 71  75  78]
   [ 71  75  78]]

  [[ 67  75  78]
   [ 68  76  79]
   [ 69  75  76]
   ...
   [ 75  79  82]
   [ 71  75  78]
   [ 73  77  80]]]]
y_train[:5] = [[6]
 [9]
 [9]
 [4]
 [1]]
```

![cifar10](<../.gitbook/assets/image (7).png>)

cifar10 contains a total of ten different types.

![10 kinds](<../.gitbook/assets/image (6).png>)

Each type is represented by a number. They are from 0-9.















## Statistics

Start time of this page: December 25, 2021

Completion time of this page: December 28, 2021
