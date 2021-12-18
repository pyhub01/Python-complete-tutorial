---
description: Draw three-dimensional graphics
coverY: 0
---

# 1 The first simple python project

In this chapter, I will talk about how to learn python and teach you how to do a simple small project.

Linux founder Linus once said: Read The Fucking Source Code!

![Linux founder Linus](<../.gitbook/assets/002 linus.jpg>)

## What is learning?

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

## Try to plot in python

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

![Running result figure](<../.gitbook/assets/002 三维.PNG>)

Let's take a look at what is being done at each step of this program:

```python
# Introduce necessary packages (library functions)
from matplotlib import pyplot as plt
import numpy as np
from mpl_toolkits.mplot3d import Axes3D

# Create a 3D canvas
fig = plt.figure()
ax = Axes3D( fig, auto_add_to_figure = False )
fig.add_axes(ax)

# Create xy axis
x = np.arange( -4, 4, 0.1 )
y = np.arange( -4, 4, 0.1 )

# Create xy plane
x_2d, y_2d = np.meshgrid( x, y )
# Create the data for the z coordinate
z = x_2d**2 + y_2d**2

# Draw three-dimensional graphics
ax.plot_surface( x_2d, y_2d, z,
                 rstride = 1, cstride = 1,
                 cmap = 'rainbow',
                 )

# Project the graphics in the internal memory and video memory onto the screen.
plt.show()
```

If we want to see what the following sentence accomplish, then what should we do?

```python
x = np.arange( -4, 4, 0.1 )
```

We close the graphical interface that pops up before, so that the interpreter script can input content. At this time, the interpreter script should output the following content:

```python
>>>
```

Enter in:

```python
>>> x
```

Then press the Enter key, the interface should output the following content:

```python
>>> x
array([-4.00000000e+00, -3.90000000e+00, -3.80000000e+00, -3.70000000e+00,
       -3.60000000e+00, -3.50000000e+00, -3.40000000e+00, -3.30000000e+00,
       -3.20000000e+00, -3.10000000e+00, -3.00000000e+00, -2.90000000e+00,
       -2.80000000e+00, -2.70000000e+00, -2.60000000e+00, -2.50000000e+00,
       -2.40000000e+00, -2.30000000e+00, -2.20000000e+00, -2.10000000e+00,
       -2.00000000e+00, -1.90000000e+00, -1.80000000e+00, -1.70000000e+00,
       -1.60000000e+00, -1.50000000e+00, -1.40000000e+00, -1.30000000e+00,
       -1.20000000e+00, -1.10000000e+00, -1.00000000e+00, -9.00000000e-01,
       -8.00000000e-01, -7.00000000e-01, -6.00000000e-01, -5.00000000e-01,
       -4.00000000e-01, -3.00000000e-01, -2.00000000e-01, -1.00000000e-01,
        3.55271368e-15,  1.00000000e-01,  2.00000000e-01,  3.00000000e-01,
        4.00000000e-01,  5.00000000e-01,  6.00000000e-01,  7.00000000e-01,
        8.00000000e-01,  9.00000000e-01,  1.00000000e+00,  1.10000000e+00,
        1.20000000e+00,  1.30000000e+00,  1.40000000e+00,  1.50000000e+00,
        1.60000000e+00,  1.70000000e+00,  1.80000000e+00,  1.90000000e+00,
        2.00000000e+00,  2.10000000e+00,  2.20000000e+00,  2.30000000e+00,
        2.40000000e+00,  2.50000000e+00,  2.60000000e+00,  2.70000000e+00,
        2.80000000e+00,  2.90000000e+00,  3.00000000e+00,  3.10000000e+00,
        3.20000000e+00,  3.30000000e+00,  3.40000000e+00,  3.50000000e+00,
        3.60000000e+00,  3.70000000e+00,  3.80000000e+00,  3.90000000e+00])
>>> 
```

So we can see the content of the variable x.

In the previous program, the step size I set was too small, so you will see a dense pile of content. In order to avoid flashing the screen, I changed the previous program. You need to copy and paste the following program into the script file (delete all previous program codes first), then run (or press F5 shortcut key to run):

```python
# Introduce necessary packages (library functions)
from matplotlib import pyplot as plt
import numpy as np
from mpl_toolkits.mplot3d import Axes3D

# Create a 3D canvas
fig = plt.figure()
ax = Axes3D( fig, auto_add_to_figure = False )
fig.add_axes(ax)

# Create xy axis
x = np.arange( -4, 4, 1 )
y = np.arange( -4, 4, 1 )

# Create xy plane
x_2d, y_2d = np.meshgrid( x, y )
# Create the data for the z coordinate
z = x_2d**2 + y_2d**2

# Draw three-dimensional graphics
ax.plot_surface( x_2d, y_2d, z,
                 rstride = 1, cstride = 1,
                 cmap = 'rainbow',
                 )

# Project the graphics in the internal memory and video memory onto the screen.
plt.show()
```

![A low-precision three-dimensional figure](<../.gitbook/assets/002 三维 1.PNG>)

Then close this interface, and then enter the variables you want to observe in the interpreter window:

```python
>>> x
array([-4, -3, -2, -1,  0,  1,  2,  3])
>>> 
```

You will find: x = np.arange( -4, 4, 1) means to create an arithmetic sequence from -4 to 4 (not including 4), with a step length of 1.

We can also observe y:

```python
>>> y
array([-4, -3, -2, -1,  0,  1,  2,  3])
>>> 
```

So what does x\_2d, y\_2d = np.meshgrid( x, y) mean? We are using the same method to interactively observe:

```python
>>> x_2d
array([[-4, -3, -2, -1,  0,  1,  2,  3],
       [-4, -3, -2, -1,  0,  1,  2,  3],
       [-4, -3, -2, -1,  0,  1,  2,  3],
       [-4, -3, -2, -1,  0,  1,  2,  3],
       [-4, -3, -2, -1,  0,  1,  2,  3],
       [-4, -3, -2, -1,  0,  1,  2,  3],
       [-4, -3, -2, -1,  0,  1,  2,  3],
       [-4, -3, -2, -1,  0,  1,  2,  3]])
>>> y_2d
array([[-4, -4, -4, -4, -4, -4, -4, -4],
       [-3, -3, -3, -3, -3, -3, -3, -3],
       [-2, -2, -2, -2, -2, -2, -2, -2],
       [-1, -1, -1, -1, -1, -1, -1, -1],
       [ 0,  0,  0,  0,  0,  0,  0,  0],
       [ 1,  1,  1,  1,  1,  1,  1,  1],
       [ 2,  2,  2,  2,  2,  2,  2,  2],
       [ 3,  3,  3,  3,  3,  3,  3,  3]])
>>> 
```

We will find that x\_2d and y\_2d form a plane. If we draw this plane, it looks like this (code attached):

```python
>>> plt.scatter(x_2d, y_2d)
<matplotlib.collections.PathCollection object at 0x00000166CF0D2760>
>>> plt.show()
>>>
```

![2D figure drawn out](<../.gitbook/assets/002 二维.PNG>)

So we have created a lattice, and after:

```python
z = x_2d**2 + y_2d**2
```

we calculate z equal to the square of x plus the square of y, thereby obtaining a three-dimensional quadratic function.

Let's take a look at what is happening with z:

```python
>>> z
array([[32, 25, 20, 17, 16, 17, 20, 25],
       [25, 18, 13, 10,  9, 10, 13, 18],
       [20, 13,  8,  5,  4,  5,  8, 13],
       [17, 10,  5,  2,  1,  2,  5, 10],
       [16,  9,  4,  1,  0,  1,  4,  9],
       [17, 10,  5,  2,  1,  2,  5, 10],
       [20, 13,  8,  5,  4,  5,  8, 13],
       [25, 18, 13, 10,  9, 10, 13, 18]], dtype=int32)
>>> 
```

If we put the previous two figures together, you will find how python's matplotlib package draws three-dimensional function images:

```python
# Introduce necessary packages (library functions)
from matplotlib import pyplot as plt
import numpy as np
from mpl_toolkits.mplot3d import Axes3D

# Create a 3D canvas
fig = plt.figure()
ax = Axes3D( fig, auto_add_to_figure = False )
fig.add_axes(ax)

# Create xy axis
x = np.arange( -4, 4, 1 )
y = np.arange( -4, 4, 1 )

# Create xy plane
x_2d, y_2d = np.meshgrid( x, y )
# Create the data for the z coordinate
z = x_2d**2 + y_2d**2

# Draw the lattice plane
ax.scatter(x_2d, y_2d, np.zeros( (len(x_2d), len(x_2d)) ))

# Draw three-dimensional graphics
ax.plot_surface( x_2d, y_2d, z,
                 rstride = 1, cstride = 1,
                 cmap = 'rainbow',
                 )

# Project the graphics in the internal memory and video memory onto the screen.
plt.show()
```

![Low resolution](<../.gitbook/assets/002 低分辨率合成.PNG>)

```python
# Introduce necessary packages (library functions)
from matplotlib import pyplot as plt
import numpy as np
from mpl_toolkits.mplot3d import Axes3D

# Create a 3D canvas
fig = plt.figure()
ax = Axes3D( fig, auto_add_to_figure = False )
fig.add_axes(ax)

# Create xy axis
x = np.arange( -4, 4, 0.5 )
y = np.arange( -4, 4, 0.5 )

# Create xy plane
x_2d, y_2d = np.meshgrid( x, y )
# Create the data for the z coordinate
z = x_2d**2 + y_2d**2

# Draw the lattice plane
ax.scatter(x_2d, y_2d, np.zeros( (len(x_2d), len(x_2d)) ))

# Draw three-dimensional graphics
ax.plot_surface( x_2d, y_2d, z,
                 rstride = 1, cstride = 1,
                 cmap = 'rainbow',
                 )

# Project the graphics in the internal memory and video memory onto the screen.
plt.show()
```

![High resolution](<../.gitbook/assets/002 高分辨率合成.PNG>)

So the way to draw points in matplotlib is to enumerate all possible points, and then calculate and draw them one by one. Is that mysterious? Absolutely not!

## Python program debugging method

What should you do when your python is wrong or you encounter a python program that you can't understand?

It's very simple, just like we did step by step debugging, and soon we will be able to figure out the meaning of each variable.

When we encounter a huge array, we try to reduce it, and when we encounter a mathematical problem that is difficult to understand, we try to visualize it. If we encounter a function, we try to disassemble it, and the problem will be solved!

## Statistics

Start time of this page: December 18, 2021

Completion time of this page: December 18, 2021
