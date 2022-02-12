---
description: Chaotic system
coverY: 0
---

# Chaotic system

There are many chaotic systems in our life. For example, the stock market, free economic system, ecosystem, weather system and so on.

## Lorentz and the Butterfly Effect

In the winter of 1961, Lorenz(1917-2008), a young assistant professor of meteorology at MIT, ran climate simulations on a Royal McBee LPG-30 computer with a simple model consisting of only 12 differential equations. After completing a calculation, he wanted to repeat the same pattern. To save time, instead of repeating this calculation from beginning to end, he starts from the middle of the program. So he used the data output from the last calculation to this position as the initial condition of this calculation. Then, to avoid the annoying noise of the computer, he went out for a cup of coffee. When he came back, he was stunned. According to common sense, the same procedures and data will obviously lead to the same results. But the second forecast was very different from the previous one. At first he thought it was a computer fault, but after ruling out this possibility, he found that the data he entered was not complete. The computer he used at that time stored data with six digits after the decimal point, but when printing out the data, in order to save paper, only three digits after the decimal point were output. When Lorenz entered the initial conditions for the second calculation, he only entered three digits after the decimal point, which had an error of less than 0.1% from the exact data. It is this error, which should have been negligible, that makes the final result very different. This made Lorenz realize that perfect long-term weather forecasts are impossible. A perfect forecast requires not only perfect climate models, but also precise measurements of temperature, humidity, wind, and all other meteorological conditions. Any small error will result in a completely different climate phenomenon.

In 1963, Lorenz published a paper entitled "Deterministic Aperiodic Flows" in the American Journal of Meteorology, proposing aperiodic phenomena in deterministic systems. The following year, he published another paper, showing that small changes to the parameters of the model can lead to completely different results, turning regular, periodic behavior into a state of complete chaos. However, his findings went unnoticed, and it wasn't until a decade later that he came up with the popular but startling idea of ​​the "butterfly effect" that the significance of the phenomenon was realized.

At the 139th meeting of the American Association for the Advancement of Science in 1972, Lorenz gave a speech titled "Predictability: Can a Butterfly Flutter in Brazil Cause a Tornado in Texas?" He believes that a small change in initial conditions can lead to a series of gradually magnifying changes that eventually lead to completely different results - this seemingly absurd assertion, shatters all illusions about "causal determinism predictability", Eventually one of the greatest theories in the world today - "chaos theory" was born. Lorenz later said that he originally wanted to use the seagull as a metaphor. A colleague told him that "butterfly" might be more vivid, while "Brazil" was chosen purely for rhyme.

In 1987, after interviewing more than 200 scientists, James Gleick, director of science and technology at The New York Times, wrote what would become a world-renowned bestseller, Chaos: Creating New Science. The title of the first chapter is "The Butterfly Effect", which introduces the process of Lorenz's first discovery of the phenomenon of chaos, but he moved a house for the butterfly - "Today, a butterfly flapping its wings in Beijing caused disturbance to the air, which may trigger Next month's storm in New York." The book, which was later translated into 19 languages, also brought the concept of "chaos" to Chinese readers in the early 1990s.

This phenomenon, which was originally only seen in weather forecasting, was later found to exist in numerous natural and social systems, such as population fluctuations, the onset of mental illness, the rhythm of heart rate, the shape of snowflakes, fluctuations in the stock market, changes in exchange rates And so on, there is chaos. After Lorentz, with the help of computers, humans began to use "chaos theory" to study the irregular, discontinuous and unstable aspects of nature and society, opening the possibility of simplifying complex phenomena.

## Lorenz Chaos

```python
def Lorenz_Chaos( init, t ):
    x, y, z = init
    dx = -10 * (x-y)
    dy = 28*x - y - x*z
    dz = -8/3*z + x*y
    return np.array( [dx, dy, dz] )



import numpy as np
from scipy.integrate import odeint
import matplotlib.pyplot as plt

t = np.arange(0, 50, 0.01)
init = [1, 1, 1]
ans = odeint( Lorenz_Chaos, init, t )



plt.figure()
plt.axes( projection='3d' )
plt.plot( ans[:, 0], ans[:, 1], ans[:, 2] )

plt.tight_layout()
plt.show()
```

The trajectory of the Lorenz system when ρ=28, σ = 10, and β = 8/3 is shown in the following figure:

![front](<../.gitbook/assets/image (19) (1).png>)

![side](<../.gitbook/assets/image (5).png>)

![up](<../.gitbook/assets/image (13).png>)

As you can see, Lorentz Chaos is a very complex graph. To draw this graph, scipy is used to automatically calculate the function of differential equations (I will explain it later)

Lorentzian chaos is very sensitive to the initial state, even if it changes by only 0.1%, the trajectory of motion will be completely different after a few hundred iterations.

```python
def Lorenz_Chaos( init, t ):
    x, y, z = init
    dx = -10 * (x-y)
    dy = 28*x - y - x*z
    dz = -8/3*z + x*y
    return np.array( [dx, dy, dz] )



import numpy as np
from scipy.integrate import odeint
import matplotlib.pyplot as plt

t = np.arange(0, 50, 0.01)

init = [1, 1, 1]
ans = odeint( Lorenz_Chaos, init, t )

init_1 = [0.999, 1, 1]
ans_1 = odeint( Lorenz_Chaos, init_1, t )



plt.figure()
plt.axes( projection='3d' )
plt.plot( ans[:, 0], ans[:, 1], ans[:, 2] )
plt.plot( ans_1[:, 0], ans_1[:, 1], ans_1[:, 2] )

plt.tight_layout()
plt.show()
```

![The blue line and the orange line are getting farther and farther apart](<../.gitbook/assets/image (20) (1).png>)

The blue line in the figure is the Lorentzian chaotic trajectory with the initial state \[1, 1, 1], and the orange line is the Lorentzian chaotic trajectory with the initial state \[0.999, 1, 1]. You will find that with time t As time goes on, they are farther and farther apart.



Plotting Lorentzian Chaos can improve your programming skills and improve your proficiency with differential equation calculation libraries.

## Statistics

Start time of this page: January 6, 2022

Completion time of this page: January 7, 2022
