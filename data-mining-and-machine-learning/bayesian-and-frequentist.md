---
coverY: 0
---

# Bayesian and Frequentist

In this tutorial, I'm not going to cover the Bayesian model because it involves so much math that it's hard to understand. And SVM or random forest or deep learning has better effect than Bayesian model.

A Bayesian model may have good results on some specific problems, but it is not a very general model in the broadest sense.

But in the previous content I talked about the recommendation algorithm, so here is the probability problem:

{% hint style="success" %}
A simple question: If I toss a coin five times in a row and it gets heads, what does it mean?
{% endhint %}

<mark style="color:purple;">**Frequentists would think it's nothing to tangle, because a coin toss is half and half, sometimes more heads, sometimes more tails, it doesn't matter, what matters is that if we toss enough times, then both heads and tails The probability is the same.**</mark>

<mark style="color:purple;">**So if you pick up a coin on the road, no matter what the toss it was, it's still half and half in your hand.**</mark>

<mark style="color:orange;">**The Bayesian probability system is a little different. If a coin is tossed five times and it is heads, then there may be a problem with the weight distribution of the coin, and it may be that the person is out of luck. It may also be a matter of magnetic fields. In short, Bayesian likes to analyze the reasons for the nature of things.**</mark>

<mark style="color:orange;">**The Bayesian formula can reverse the cause and effect. For example, we know the probability that the car alarm sounded because it was smashed by a thief (this probability indicates the accuracy of the car alarm), and the Bayesian formula can turn this probability into: The Probability of a thief smashing a car causing the car alarm to alarm. In conclusion, the Bayesian formula can flip the cause and effect (prior and posterior), which is very useful.**</mark>

![A very classic Bayesian problem](<../.gitbook/assets/image (21).png>)

A very well-known example of Bayesian algorithms is the probability of rain, whether the ground is wet, and whether the sprinkler is working.

After a series of flips of the Bayesian formula, we can infer the probability that the ground is wet due to cloudiness and the probability that the ground is wet is cloudy.

Because it involves a lot of calculations, it will not be shown here. If you are interested, you can search for this problem on Google.

{% hint style="danger" %}
Bayesian probability is crazy because we can investigate the relationship between some people's political leanings and their shopping receipts, car purchases, real estate, academic performance, income, and then build a model (linear or non-linear) We can then use Bayesian logic to flip the model and predict a person's political leanings with maximum likelihood by shopping receipts, cars purchased, real estate, school grades, and income.

**In fact, this model has been made, and the specific links are as follows:**

****[https://news.stanford.edu/2017/11/28/neighborhoods-cars-indicate-political-leanings/](https://news.stanford.edu/2017/11/28/neighborhoods-cars-indicate-political-leanings/)

The model has achieved good accuracy using only cars as input data.

<mark style="color:red;">**This practice is dangerous**</mark>

In the TV series **Westworld**, artificial intelligence is used to rule humans. These machines can use a person's past experience, family background, wealth, education level to predict his future career and probability of success. If he/she is unsuccessful in the future in prediction, then It is not cultivated to save the resources of the future world.

The result of this is increased polarization, the rich will get more resources because they have an advantage in the machine learning model as their family is rich, and the poor will become poorer because the machines don't think they can be successful, so once a person Going to failure, he will lose all resources and be finally eliminated from society by this artificial intelligence.

<mark style="color:red;">**It's a scary and sad future.**</mark>
{% endhint %}

{% hint style="danger" %}
<mark style="color:red;">**Recommendation Algorithms and Internet User Extremes**</mark>

Recommendation algorithms are in fact polarizing humans. Because on the Internet, the recommendation algorithm will only recommend what you want to see (we said that the recommendation algorithm actually understands humans better than humans), then a person continues to receive positive feedback on his/her ideas, he/she will Believe that his/her idea is correct and do it more extreme, and then the Internet system will recommend him/her more extreme content (because he/she has become more extreme)

In fact, this is exactly what is happening on the Internet now.(Of course, there are also problems caused by the anonymity of the Internet. Only the problems caused by computer algorithms are analyzed here.) The Internet is not as human beings expected: Humans live in a place called the global village and then love each other. The recommendation algorithm makes the Internet more extreme. At the same time, there is too much content on the Internet. The explosion of information makes it impossible for everyone to distinguish whether it is good or bad, which leads to a rapid decrease in the network signal-to-noise ratio, and the most extreme content becomes The new mainstream of the Internet. This is very dangerous.

Studies have shown that when people avoid use the Internet and social networks, this group of people is more moderate than the control group. It has to be said that the situation will only get worse as the Internet now appears in more places (4G, 5G networks, on cars, on buses, even on airplanes).
{% endhint %}

## Statistics

Start time of this page: February 2, 2022

Completion time of this page: February 8, 2022
