# Lecture 9: Conditional Probability
* __Note__: Exam 1 coming up on __September 23-24__

Resources for this lecture:

Remember:
* $P(A) = \frac{\text{Number of Successful Outcomes}}{\text{Number of Possible Outcomes}}$
* $P(A~or~B) = P(A) + P(B) - P(A~and~B)$

## Complements


## Confusion Matrix
Sometimes we are looking at multiple categories at once. The probability of one category may depend on the other category. We often use a __confusion matrix__ to show how the two categories react with each other.

A table that shows the two categories

|           | $A$                | $\bar{A}$                |
| :-------: | :----------------: | :----------------------: | 
| $B$       | $P(A~and~B)$       | $P(\bar{A}~and~B)$       |
| $\bar{B}$ | $P(A~and~\bar{B})$ | $P(\bar{A}~and~\bar{B})$ |

For example, let's compare students who like football compared to students who like basketball.
* You sample 200 students
* 160 students said they like football
* 145 students said they like basketball
* 120 like both

|           | $F$   | $\bar{F}$ |
| :-------: | :---: | :-------: | 
| $B$       | 120   | 25        |
| $\bar{B}$ | 40    | 15        |

## Conditional Probability
* What is the probability that a student likes basketball? (145/200 = 0.725)
* What is the probability that a student likes basketball if we already know they like football? (120/160 = 0.75)

The concept behind __conditional probability__ is that a probability for one category depends on another category.
> What is the probability that a student likes basketball if we already know they like football?
> * $P(B|F) = 120/160 = 0.75$
> * $P(\bar{B}|F) = 40/160 = 0.25$

Equation for Conditional Probabilities:
$$P(B|A)=\frac{P(A~and~B)}{P(A)}$$
> * $P(B|F) = \frac{P(B~and~F)}{P(F)} = \frac{120/200}{160/200} = \frac{120}{160} = 0.75$

> __Blackjack__: The goal of blackjack is to get as close to 21 as possible. Cards are awarded points as follows:
> * Face = 10
> * Numbers = numerical value
> * Ace = either 1 or 11, player's choice
> 
> If you already have a King, what is the probability of getting a blackjack?
>  * King + 2 = 10 + 2 = 12
>  * The only way to get a blackjack is to draw a 9
>  * There are only 50 cards left in the deck, and there are four 9's.
>   $$P(9|(K+2)) = \frac{4}{50} = 0.08$$


## AND Probabilities
Now that we have an equation for conditional probability, we can define the AND probability.

$$P(A~and~B) = P(B|A)P(A)$$

> __Blackjack Variation__: Let's say you create a version where if you draw both of the black jacks (jack of spades and jack of clubs), you automatically win the hand, even if someone else actually gets 21. What's the probability of drawing both black jacks?
> $$P(JS~and~JC) = P(JS|JC)P(JC) = \frac{1}{51}\frac{1}{52} = \frac{1}{2652} = 0.000377$$

Notice that we could have swapped the order and gotten the same result:

> $$P(JC~and~JS) = P(JC|JS)P(JS) = \frac{1}{51}\frac{1}{52} = \frac{1}{2652} = 0.000377$$

This leads to an important relationship:
$$P(A|B) = \frac{P(A~and~B)}{P(B)} \qquad P(B|A)=\frac{P(A~and~B)}{P(A)}$$
$$P(A|B)P(B) = P(A~and~B) = P(B|A)P(A)$$

> __Basketball__: From practicing free throw shots, I notice a pattern whenever I have 2 shots:
> * I have a 70% chance of making the first shot
> * If I make the first shot, I have a 75% chance of making the second
> * If I miss the first shot, I have a 60% chance of making the second
> 
> You come into the game just after I made a first shot, so you don't know if I made it or not. If I make the second shot, what's the probability that I made the first shot?
> 
> * Only two options: $(1~and~2)$ or $(1^C~and~2)$

### Class Practice
A bag of marbles contains 7 red marbles, 12 blues marbles, 6 green marbles, and 11 purple marbles.
1. If you draw out two marbles with replacement, what is the probability of getting a red and then a blue?

2. If you draw out two marbles with replacement, what is the probability of getting a red and then a marble that is not blue?

3. If you draw out two marbles without replacement, what is the probability of getting a purple and then another purple?

4. If you draw out three marbles without replacement, what is the probability of getting a red and then a green and then a marble that is not blue?



-----
-----
# Homework
## Reading
* 3.1.6 Complement of an event
* 3.2 Conditional Probability

## Exercises
* From section 3.1
  * Exercises 3.5, 3.6, 3.7, 3.9, 3.10
  * 
* From Chapter 3 Exercises
  * Exercises 3.41