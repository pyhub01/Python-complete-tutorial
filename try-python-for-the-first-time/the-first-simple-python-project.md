---
description: Draw three-dimensional graphics
coverY: 0
---

# 1 The first simple python project

In this chapter, I will talk about how to learn python and teach you how to do a simple small project.

Linux founder Linus once said: Read The Fucking Source Code

![Linux founder Linus](<../.gitbook/assets/002 linus.jpg>)

What is learning?

We sometimes feel that artificial intelligence is very mentally retarded. Why do we feel that way? Because the artificial intelligence which you use can't learn.

Learning is to acquire knowledge from the world, acquire knowledge autonomously and spontaneously.

If you have a question today, it is:

```python
>>> import numpy
Traceback (most recent call last):
  File "<pyshell>", line 1, in <module>
    import numpy
ModuleNotFoundError: No module named 'numpy'
```

How would you solve it? Here are a few options for you:

1. python is really hard, I can't learn
2. what the fxxk is this?
3. Google search: ModuleNotFoundError: No module named'numpy'

If you choose the last one, congratulations, you know how to learn. The characteristic of learning is to continuously acquire knowledge, and the key to learning is to know how to effectively acquire knowledge.

{% embed url="https://pypi.org/project/numpy" %}
about numpy
{% endembed %}

Here is a website for everyone: pypi, through this website you can get information and installation methods of various libraries in python.

You will find that through this command: pip install numpy, we can install numpy.

So how do we use this command? Open your windows and search for cmd in the lower left corner.

Then you will open an interface like this:

![CMD in Win10](<../.gitbook/assets/002 cmd.PNG>)

Then enter pip install numpy in it. After that, you will find that the progress bar keeps moving, and then the installation is complete.

Now you try the previous commands again, and you are all set.

```python
>>> import numpy
>>> 
```

In order to run today's program, we need to install another library: matplotlib. This library is modeled after matlab's api. It can easily draw function images. We enter the following commands into CMD:

```bash
pip install matplotlib
```

{% embed url="https://pypi.org/project/matplotlib" %}
How to install matplotlib and instructions
{% endembed %}

The program to be tried today is a program for drawing a three-dimensional quadratic function. The code is as follows. You can create a new python script called 3D drawing.py, and then paste the following code and run it to see how it works:

```python
from matplotlib import pyplot as plt
import numpy as np
from mpl_toolkits.mplot3d import Axes3D

fig = plt.figure()
ax = Axes3D( fig, auto_add_to_figure = False )
fig.add_axes(ax)

x = np.arange( -4, 4, 0.1 )
y = np.arange( -4, 4, 0.1 )

x, y = np.meshgrid( x, y )
z = x**2 + y**2

ax.plot_surface( x, y, z,
                 rstride = 1, cstride = 1,
                 cmap = 'rainbow',
                 )

plt.show()
```

![](<../.gitbook/assets/002 三维.PNG>)









































