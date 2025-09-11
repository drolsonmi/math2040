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

## AND Probabilities
Now that we have an equation for conditional probability

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
* From section 
  * Exercise 
  * 
* From Chapter 2 Exercises
  * Exercises 