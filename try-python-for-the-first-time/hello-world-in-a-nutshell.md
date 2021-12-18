---
description: Several forms of python code
coverY: 0
---

# 1 Hello world in a nutshell

## Assembly language and compiled language and interpreted language

We can divide programming languages ​​into three categories. One is assembly language. We know that computers can only recognize binary codes, so our programs must compile into binary codes before they can run. In order to make it easier for people to remember these binary codes, we use some symbols. To represent these binary codes, for example, use "ADD" to mean "1010100010001110", and "SUB" to mean "0011000001100110". This is what we call assembly language. Assembly language is unlikely to be encountered when we are programming, because low-level code engineers(Low-level does not mean that their engineers is naive in skills. Just the opposite. Because assembly language is very difficult to manage and requires a lot of programming skills.) have solved it for you. The other is a compiled programming language. Compiled programming languages ​​such as C and C++ and Java work by first using a compiler to convert the code into assembly language and then run it. It is the main form of the relatively early programming languages. The last type is interpreted programming languages, such as our commonly used matlab or R or python. Interpreted programming languages ​​use an interpreter to convert the code into a compiled programming language code, then use the compiler of a compiled programming language to compile the code. These codes are generally more powerful. One line of commands can do things that have to be done in dozens or even tens of thousands of lines in a compiled programming language, which is very convenient, but the efficiency will be reduced accordingly.

## Process-oriented language and object-oriented language

Process-oriented languages appeared earlier and simpler. For example, the following piece of code is a process-oriented language:

```
a = 3
b = 5

print(a)
print('hello world')
print(b)

print( a + b )
```

The result of the above program is:

```
3 
hello world 
5 
8
```

Process-oriented language is executed from the beginning to the end. This is in line with human thinking habits. We need to follow the steps to do a thing. When we do all the steps, we finished a thing.

Process-oriented language is very effective for some simple things, such as making an automatic watering circuit with a single-chip microcomputer chip.

![arduino project - automatic watering machine](<../.gitbook/assets/001 自动浇花器.jpg>)

This circuit consists of a soil moisture sensor, a microcontroller and a relay (used to control the water pump).

When the soil moisture detector finds that the soil moisture is insufficient, the microcontroller will order the water pump to supply water. When the water is supplied, the soil moisture detector will continue to monitor the soil moisture. If the soil is already moist, stop the water pump and continue to detect whether the soil is moist. If the soil dries out again, continue to supply water. This continues to be tested again and again. We can complete the task of automatic watering.







