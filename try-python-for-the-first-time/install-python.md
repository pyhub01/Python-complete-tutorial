---
description: Install python3 tutorial
coverY: 0
---

# 1 Install python

Python is divided into python2 and python3. Python2 uses an older programming language design scheme, which is no longer suitable for the current high-level programming language design ideas. Therefore, in order to remove the burden from old version, python3 did not consider backward compatibility when designing.

Python workshop officially announced that on January 1, 2020, the update of Python 2 will be discontinued.

So in this tutorial, the latest version of python3 will be used for teaching.

First we need to install python3.

{% embed url="https://www.python.org" %}
python official website
{% endembed %}

Before starting to install python3, I suggest you take a look at the official python website.

## Install the most basic graphical python3 interpreter

When I wrote this tutorial, python has been updated to version 3.10, but I strongly recommend that you do not use the latest version of python because there are still many package compatibility issues that need to be resolved in this version. So I suggest that you use the last version of 3.8, which is python3.8.10.

{% embed url="https://www.python.org/downloads/release/python-3810" %}
python download introduction page
{% endembed %}

At the bottom of this page is the download options and file download address. You can choose different installation packages according to your system. If your system is win10, then I recommended you to choose Windows installer (64-bit), and then you only need to follow the prompts step by step Just install it.

{% embed url="https://www.python.org/ftp/python/3.8.10/python-3.8.10-amd64.exe" %}
If you are a win10 user but you cannot find the download link, this is the exe download link.
{% endembed %}

There are two things to pay attention to when installing:

1. You should check Add python3 to the windows environment variable (system PATH), so you don't need to manually add environment variables (a rather troublesome thing).
2. You should choose to lift the system's longest string (256 bytes) limit at the end of the installation, so that you will have no problem installing any packages in the future.

The above is the way to install the simplest version of the python3 graphical interpreter.

{% hint style="danger" %}
Warning that the native interpreter interface is not very friendly to the input method. When you type in languages other than English, some shortcut keys may be triggered by mistake, which is quite annoying. The following software will be no such problem.
{% endhint %}

## (Optional) Install pycharm

The basic interpreter is very useful, but if you write a deep learning program and want to watch the progress bar scroll, then the basic interpreter does not support the backspace, which will become your nightmare, but if you use pycharm, backspace is no longer a problem. If you want to run two programs that require different versions of libraries, then if you use a basic interpreter, then when you run the first program, you need to install the libraries required by the first program. If you run the first program In the case of two programs, you need to uninstall the dependent library of the first program, and then install the dependent library of the second program. This is quite troublesome. If you have pycharm, you can directly create two different virtual environments, which Contains different libraries.

{% embed url="https://www.jetbrains.com/pycharm" %}
pycharm
{% endembed %}

Installing pycharm is a simple matter. You need to click on the above website, and then choose Professional version or Community version. The former requires a fee and the latter is free. I recommend using the Community version, because Community basically includes all you need, and the volume consuming on disk is relatively small.

## (Optional) Install anaconda

Anaconda supports virtual environments. This is the reason why I strongly recommend you to install anaconda. Another reason why I strongly recommend you to install anaconda is that if you want to program artificial intelligence and deep learning programs, then you will most likely use a graphics card (Nvidia) as Your computing device, and the graphics card need to install cuda and cudnn drivers, if you manually install these drivers will be a very troublesome thing(Especially setting environment variables), but if you have anaconda, you only need two lines of command, you can complete cuda and cudnn Install.

If you want to use jupyter notebook, anaconda is also a good choice.

Installing anaconda is also an easy task, you just need to keep clicking next after downloading. It should be noted that if you want to program deep learning, anaconda may occupy a considerable amount of disk space (10G), then I suggest you install anaconda on a mechanical hard drive(HDD) instead of a solid state drive(SSD).

{% embed url="https://www.anaconda.com" %}
anaconda
{% endembed %}

## (Optional) Install vscode

In my opinion, vscode is a very easy-to-use software. First of all, it is much lighter than visual studio. You no longer need dozens of gigabytes of disk space to accommodate various libraries you don't need. The plug-ins in vscode can be installed by clicking install, which is very convenient. Vscode supports languages other than English well, and there will be no problems such as false triggering of shortcut keys caused by input methods. The bad news is that vscode programming python may need to install external libraries, which will be more troublesome. The download link of vscode is as follows:

{% embed url="https://code.visualstudio.com" %}
vscode
{% endembed %}

## Why choose python

{% embed url="https://www.tiobe.com/tiobe-index" %}
Ranking of programming languages in the world
{% endembed %}

The above link is the world's programming language ranking, including the number of users and popularity. You can open the web page to observe the current programming language ranking. Sometimes it will change.

In the next chapter, we will also mention why we choose python. You can feel the simplicity of python by installing the python basic compiler. If you have used c and c++, you will find that c and c++ programming is quite troublesome, all You need to write the data structure yourself, and installing the g++ compiler is also a troublesome thing. If you have written R language or MATLAB, you will find that the subscripts of these two languages start from 1, which does not match The feeling of computer programming, and if you use a different version of R language or MATLAB, various errors will drive you crazy. MATLAB is still a fee-based software. In addition to the large-scale use in schools, you will find that in the company It is rarely used, if you have used go, you will find it quite troublesome to install and run the code. According to my observation, the reasons for choosing python are divided into the following:

1. Python programming is simple and does not require superb programming skills
2. The python code is very concise, a few lines of content can solve a troublesome problem
3. Open source software has fewer bugs and does not require licensing fees, Many companies use it
4. The current world economy is not good these years, so using python will be more economical than using c++ or java. (Fewer employees, higher efficiency)
5. The code efficiency of python is improving year by year, and the performance of the computer is improving year by year, so the criticism of python's low efficiency is gradually weakening.
6. The code development cycle is getting shorter and shorter, which is suitable for programming languages that can be developed quickly.
7. Many emerging fields, such as image recognition (deep learning) or text mining (deep learning) can only be processed with python
8. Many well-known websites and software are written in python today.
9. The python code structure is very similar to c, c++, java, so these programmers can easily transfer to the python field.

## Statistics

Start time of this page: December 17, 2021

Completion time of this page: December 17, 2021
