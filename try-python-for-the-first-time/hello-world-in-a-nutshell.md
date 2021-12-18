---
description: Several forms of python code
coverY: 0
---

# 1 Hello world in a nutshell

## Assembly language and compiled language and interpreted language

We can divide programming languages ​​into three categories. One is assembly language. We know that computers can only recognize binary codes, so our programs must compile into binary codes before they can run. In order to make it easier for people to remember these binary codes, we use some symbols. To represent these binary codes, for example, use "ADD" to mean "1010100010001110", and "SUB" to mean "0011000001100110". This is what we call assembly language. Assembly language is unlikely to be encountered when we are programming, because low-level code engineers(Low-level does not mean that their engineers is naive in skills. Just the opposite. Because assembly language is very difficult to manage and requires a lot of programming skills.) have solved it for you. The other is a compiled programming language. Compiled programming languages ​​such as C and C++ and Java work by first using a compiler to convert the code into assembly language and then run it. It is the main form of the relatively early programming languages. The last type is interpreted programming languages, such as our commonly used matlab or R or python. Interpreted programming languages ​​use an interpreter to convert the code into a compiled programming language code, then use the compiler of a compiled programming language to compile the code. These codes are generally more powerful. One line of commands can do things that have to be done in dozens or even tens of thousands of lines in a compiled programming language, which is very convenient, but the efficiency will be reduced accordingly.

## Process-oriented language and object-oriented language

### Process-oriented programming

Process-oriented languages appeared earlier and simpler. For example, the following piece of code is a process-oriented language:

```python
a = 3
b = 5

print(a)
print('hello world')
print(b)

print( a + b )
```

The result of the above program is:

```python
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

The following code can complete this process.

```python
# Continuously monitor the soil moisture
while True:

    # Get soil moisture
    soil_status = get_humidity_sensor_result()

    # Stop the water pump if it gets wet
    if soil_status == 'wet':
        water_pump('halt')

    # Turn on the pump if it gets dry
    if soil_status == 'dry':
        water_pump('start')
```

### Object-Oriented Programming

Object-oriented programming appeared later than process-oriented programming, because object-oriented programming can handle more complex tasks. Similarly, it becomes more difficult to convert these codes into binary assembly codes which can be read by machines.

Using the example above, we have an automatic watering system, but this time the automatic watering system is carried out in a botanical garden. Imagine a greenhouse with hundreds of plants in it, and every plant needs a Independent automatic watering system. If I use a supercomputer to control all the water pumps and soil moisture sensors in this greenhouse, how do we do it?

![A greenhouse with thousands of plants](<../.gitbook/assets/001 温室苗圃.jpg>)

```python
# Continuously monitor the soil moisture
while True:

    # Get soil moisture of plant 1
    soil_status_plant_1 = get_humidity_sensor_result_plant_1()

    # Stop the water pump if plant 1 gets wet
    if soil_status_plant_1 == 'wet':
        water_pump_plant_1('halt')

    # Turn on the pump if plant 1 gets dry
    if soil_status_plant_1 == 'dry':
        water_pump_plant_1('start')


    # Get soil moisture of plant 2
    soil_status_plant_2 = get_humidity_sensor_result_plant_2()

    # Stop the water pump if plant 2 gets wet
    if soil_status_plant_2 == 'wet':
        water_pump_plant_2('halt')

    # Turn on the pump if plant 2 gets dry
    if soil_status_plant_2 == 'dry':
        water_pump_plant_2('start')


    # Get soil moisture of plant 3
    soil_status_plant_3 = get_humidity_sensor_result_plant_3()

    # Stop the water pump if plant 3 gets wet
    if soil_status_plant_3 == 'wet':
        water_pump_plant_3('halt')

    # Turn on the pump if plant 3 gets dry
    if soil_status_plant_3 == 'dry':
        water_pump_plant_3('start')
```

If our greenhouse contains 3 plants, then we need to write these much of the code, what if our greenhouse contains thousands of plants? Then our code will become extremely redundant.

To avoid this problem, we can introduce object-oriented programming. In other words, we program each automatic watering module as an object.

```python
class auto_water_module:

    def __init__(self, id_of_the_plant):
        self.id = id_of_the_plant

    def process(self)
        # Get soil moisture
        __soil_status = get_humidity_sensor_result(self.id)

        # Stop the water pump if it gets wet
        if __soil_status == 'wet':
            water_pump('halt', self.id)

        # Turn on the pump if it gets dry
        if __soil_status == 'dry':
            water_pump('start', self.id)

# Create 1000 automatic watering devices
plant_list = []
for i in range(1000):
    plant_list.append(auto_water_module(i))

# Make 1000 automatic watering devices work
while True:
    for i in plant_list:
        i.process()
```

In this example, I encapsulated each automatic watering device into a class, and then called the function of creating the class, we successfully created 1000 automatic watering devices! Then we can make these automatic watering devices work.&#x20;

And all of this we only used a few lines of code.

The true charm of object-oriented programming is not here. Let's change an example:

![Different professions](<../.gitbook/assets/001 不同职业.jpg>)

We have different professions in life, such as policeman, soldier, doctor, nurse, taxi driver, truck driver, chef, student, painter and so on.

As a human being, each person has many attributes, such as eating, sleeping, hobbies, height, weight, gender. At the same time, each of us has different attributes due to different occupations. For example, painters need to paint, cooks need to cook, the police need to catch the thief, the firefighters need to put out the fire, and the students need to take an exam. At this time, if you use process-oriented programming, it will become extremely cumbersome, while using object-oriented programming will become very simple.

We can make a template (class) called human, which contains different attributes such as height, weight, gender, and then create a template called painter, which contains the popularity, type of painting, the name of the exhibition that we participated in, etc., and the other template is called student. Including grade, educational background, whether you have participated in an internship, test scores, etc. If we need to create a 24-year-old male student learning computer, we only need to combine humans and students to assign these attributes to this object. If we need to build a 43-year-old firefighter, we can do the same. A class is a template, and we can apply this template to build a lot of things we need.

![Design Patterns](<../.gitbook/assets/001 设计模式.png>)

When we are creating a complex system (such as designing an Amazon website or designing a computer operating system), we need to figure out what design patterns we need. This is a difficult science. I will create one chapter and talks about it later.

In our lives, there are actually many object-oriented designs. For example, for a shopping website, we have thousands of users, and everyone has their own wish list, shopping cart, and payment method. Another example is the army. We have the navy, the army and the air force. For another example, our city has countless traffic lights. Some are designed for pedestrians, some are designed for bicycles, some are designed for motor vehicles, and some are designed for trains.

Object-oriented programming is so widespread that some languages are inherently designed for object-oriented programming, such as Java:

```java
public class HelloWorld 
{
    public static void main(String[] args) 
    {
        System.out.println("hello world");
    }
}
```











