# Lecture 8: Probability
* __Note__: Exam 1 coming up on __September 23-24__

## Intro to Probability
For quantitative data, we have a number of measures for analysis:
* Mean, Median, Mode, 5-number summary, Standard Deviation
* Boxplots

However, we can't use these measures on Categorical data. The most we can do at face value is count the occurences of each category. So, we need a tool that helps us analyze those counts. This is where probability comes in.

Probability is built on random chance. For example, 

> If I flip a coin, what is the chance that it lands on heads?

The flip adds randomness, and we can use the count of categories to calculate that chance.
* How many possible outcomes are there? 2
* How many of those outcomes would give us what we want (success)? 1
* So 1 out of the 2 outcomes would give us a success
* $P(H) = \frac{1}{2} = 0.50 = 50\%$

The general formula for a probability is,
$$P(x) = \frac{\text{\# of successful outcomes}}{\text{\# of outcomes}}$$

If you roll a die, what is the probability of rolling a 6?
* $P(6) = 1/6 = 0.1667 = 16.67\%$

## Law of Large Numbers
Let's say you want to test the probability of rolling a 6.
* Roll a die 10 times and get: `3,5,1,2,6,6,3,1,4,2`
* 2 of the 10 rolls were 6's
* P(6) = 2/10 = 20\%?? <-- No

When you do this as an experiment, it is called a __relative frequency__, or a __proportion__.

> In Python, open [Law of Large Numbers](https://colab.research.google.com/drive/1VRXPNELUI0to4PCfmwk-a8KV4n7zBsiD?usp=sharing) demo

> The __Law of Large Numbers__ says that if the sample size ($n$) is large enough, then the proportion $\hat{p}_n$ approaches the probability $p$. 

## Addition Rule
What is the probability of getting a 5 or a 6?
* A __disjoint__ probability (also known as __mutually exclusive__ outcomes) occur when there is no way the two outcomes could happen at the same time.
    * When you roll a die, there is no way to role a 5 or a 6 at the same time
* $P(5~or~6) = P(5) + P(6) = 1/6 + 1/6 = 2/6 = 1/2 = 0.50 = 50\%$

The __addition rule__:
$$P(A~or~B) = P(A) + P(B)$$
$$P(A~or~B~or~C~or...~Z) = P(A) + P(B) + P(C) + ... + P(Z)$$

## General Addition Rule
A deck of cards:
>	AH	AD	AC	AS
>
>	2H	2D	2C	2S
>
>	3H	3D	3C	3S
>
>	4H	4D	4C	4S
>
>	5H	5D	5C	5S
>
>	6H	6D	6C	6S
>
>	7H	7D	7C	7S
>
>	8H	8D	8C	8S
>
>	9H	9D	9C	9S
>
>	10H	10D	10C	10S
>
>	JH	JD	JC	JS
>
>	QH	QD	QC	QS
>
>	KH	KD	KC	KS

What is the probability of drawing a card that is either an Ace or a Spade?
* Following the formula, $P(A~or~S) = P(A)+P(S) = \frac{4}{52}+\frac{13}{52} = \frac{17}{52}$
* But if we count them, there are only 16 cards that are either an Ace or a Spade, so $P(A~or~S) = \frac{16}{52}$. What happened?
* Double-counted one card: the Ace of Spades
* If you double-count, then just remove one of those counts: $P(A~or~S) = P(A) + P(S) - P(A~and~S) = \frac{4}{52}+\frac{13}{52} - \frac{1}{52} = \frac{16}{52}$

Here is the __general addition rule__:
$$P(A~or~B) = P(A) + P(B) - P(A~and~B)$$

## Class Practice
A bag of marbles contains 7 red marbles, 12 blues marbles, 6 green marbles, and 11 purple marbles.
1. If you draw out one marble, what is the probability of getting a blue?
    * $P(blue)=12/36=0.3333$
2. If you draw out one marble, what is the probability of getting a green OR a blue?
    * $P(green OR blue)=P(green)+P(blue)−P(green AND blue)=6/36+12/36−0/36=18/36=0.50$
3. If you draw out one marble, what is the probability of getting a green AND a purple?
    * $P(green AND purple)=0$
    * If drawing 1 marble, green and purple are mutually exclusive

-----
# Homework
## Reading
* 3.1 Defining Probability

## Exercises
* From section 
  * Exercise 
  * 
* From Chapter 3 Exercises
  * Exercises 