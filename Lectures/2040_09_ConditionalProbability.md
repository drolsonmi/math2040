# Lecture 9: Conditional Probability
* __Note__: Exam 1 coming up on __September 23-24__

Materials:
* Deck of Cards

Remember:
* $P(A) = \frac{\text{Number of Successful Outcomes}}{\text{Number of Possible Outcomes}}$
* $P(A~or~B) = P(A) + P(B) - P(A~and~B)$

> __Magic Trick__
> * Have a student draw a card and place it face down into the deck
> * Shuffle the deck and put it under the desk viewer
> * Calculate the probability that I draw that student's card
> * Reveal

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
Now that we have an equation for conditional probability, we can define the AND probability.

$$P(A~and~B) = P(B|A)P(A)$$

> __Magic Trick - Part 2__
> * Have 2 students draw cards and place them face down into the deck
> * Shuffle the deck and put it under the desk viewer
> * Calculate the probability that I draw both students' cards
> $$P(A~and~B) = P(B|A)P(A) = \frac{1}{51}\frac{1}{52} = \frac{1}{2652} = 0.000377$$
> * Reveal

> __Blackjack__: The goal of blackjack is to get as close to 21 as possible. Cards are awarded points as follows:
> * Face = 10
> * Numbers = numerical value
> * Ace = either 1 or 11, player's choice
> 
> If you already have a King, what is the probability of getting a blackjack?
>  * King = 10 -> Must get an Ace
> $$P(A ~ and ~ K) = P(A|K)P(K) = \frac{4}{51}\frac{4}{52} = \frac{16}{2652} = 0.00603$$

Notice that we could have swapped the order and gotten the same result:

> $$P(K~and~A) = P(K|A)P(A) = \frac{4}{51}\frac{4}{52} = \frac{16}{2652} = 0.00603$$

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

> __Blackjack - Part 2__: If I draw a 9, what is the probability that I can get blackjack?
> * I need 12 points. Different ways to get 12 points:
>    * Ace (11) and Ace (1): $P(A~and~A) = P(A|A)P(A) = \frac{3}{49}\frac{4}{50} = \frac{12}{2450} = 0.00490$
>    * Face and 2: $P(F~and~2) = P(F|2)P(2) = \frac{12}{49}\frac{4}{50} = \frac{48}{2450} = 0.01959$
>    * 10 and 2: $P(10~and~2) = P(10|2)P(2) = \frac{4}{49}\frac{4}{50} = \frac{48}{2450} = 0.00490$
> $$P((A~and~A) or (F~and~2) or (10~and~2)) = 0.00490+0.01959+0.00490 = 0.02939$$

> __Repeated Birthdays__: How many people need to be in a room before there is more than a 50% chance of a repeated birthday? (Assume 365 days in a year)
> * Easier to think of probability that birthdays are NOT repeated
>   * Person 1 enters. His probability of not sharing birthdays is $P(1) = \frac{365}{365}$
>   * Person 2 enters. His probability of not sharing birthdays is $P(2) = \frac{364}{365}$
>   * Person 3 enters. His probability of not sharing birthdays is $P(3) = \frac{363}{365}$
>   * Person 4 enters. His probability of not sharing birthdays is $P(4) = \frac{362}{365}$
>   * Person 5 enters. His probability of not sharing birthdays is $P(5) = \frac{361}{365}$
>   * Person 6 enters. His probability of not sharing birthdays is $P(6) = \frac{360}{365}$
>   * Person 7 enters. His probability of not sharing birthdays is $P(7) = \frac{359}{365}$
>   * ...
> 
> * Now, what is the probability that person 1 doesn't share birthdays AND person 2 doesn't share birthdays AND person 3 doesn't share birthdays AND person 4 doesn't share birthdays AND ...
>
> $$\begin{align*}
        P(2~no~shared~birthdays) &= P(1)*P(2) \\
        &= \frac{365}{365}*\frac{364}{365}\\
        &= 1*0.997=0.997\\
        P(3~no~shared~birthdays) &= P(1)*P(2)*P(3) \\
        &= \frac{365}{365}*\frac{364}{365}*\frac{363}{365}\\
        &= 1*0.997*0.995 = 0.992\\
        P(7~no~shared~birthdays) &= P(1)*P(2)*P(3)*P(4)*P(5)*P(6)*P(7) \\
        &= \frac{365}{365}*\frac{364}{365}*\frac{363}{365}*\frac{362}{365}*\frac{361}{365}*\frac{360}{365}*\frac{359}{365}\\
        &= 1*0.997*0.995*0.992*0.989*0.986*0.984 = 0.944\\
        P(8~no~shared~birthdays) &= 0.926\\
        P(10~no~shared~birthdays) &= 0.883\\
        P(15~no~shared~birthdays) &= 0.747\\
        P(20~no~shared~birthdays) &= 0.589\\
        P(21~no~shared~birthdays) &= 0.556\\
        P(22~no~shared~birthdays) &= 0.524\\
        P(23~no~shared~birthdays) &= 0.493
      \end{align*}$$
> It takes 23 people to have a probability less than 50% that nobody is repeating a birthday. 
>
> Therefore, taking the compement, it takes 23 people to have a probability greater than 50% that *somebody* has repeated a birthday.

## Independence
Conditional probabilities imply that one variable depends on another.
* Probability of drawing a specific card from the deck depends on the cards drawn before it

Sometimes, however, the second variable does not depend at all on the first
* Replace the first card, then draw a second

Such events are known as __independent__ events. Since the second event does not rely on the first, the conditional probability will be the same whether the first event happens or not.

$$P(B|A) = P(B|A^C) = P(B)$$

### Class Practice
A bag of marbles contains 7 red marbles, 12 blues marbles, 6 green marbles, and 11 purple marbles. For each of the following, determine whether they are independent or not, then find the probability.
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