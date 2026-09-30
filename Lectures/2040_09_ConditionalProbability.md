<head>
<script>
  MathJax = {
    tex: {
      inlineMath: [['$', '$'], ['\\(', '\\)']],
    displayMath: [['$$', '$$'], ['\\[', '\\]']]
  }
};
</script>
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js"></script>
<title>Lecture 9: Conditional Probability</title>
</head>

# Lecture 9: Conditional Probability
* __Note__: Exam 1 coming up (See the course schedule)

Materials:
* Deck of Cards

Remember:
* $P(A) = \frac{\text{Number of Successful Outcomes}}{\text{Number of Possible Outcomes}}$
* $P(A~or~B) = P(A) + P(B) - P(A~and~B)$
* Disjoint (or Mutually Exclusive) if $P(A~and~B) = 0$
* $P(A^C) = 1 - P(A)$

> __Magic Trick__
> * Have a student draw a card and place it face down into the deck
> * Shuffle the deck and put it under the desk viewer
> * Calculate the probability that I draw that student's card
> * Reveal

## Confusion Matrix (or Contingency Table, or Cross-tabulation)
Sometimes we are looking at multiple categories at once. The probability of one category may depend on the other category. We often use a __confusion matrix__ to show how the two or more categories react with each other.

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

Contingency Table comparing favorite sport to favorite concessions foods:

|          | $Football$ | $Basketball$ | $Baseball$ |
| :------: | :--------: | :----------: | :--------: |
| Hot Dogs | Moderate   | Low          | High       |
| Nachos   | High       | High         | Moderate   |
| Wings    | High       | Moderate     | Low        |
| Churros  | Moderate   | High         | Moderate   |

## Conditional Probability
* What is the probability that a student likes basketball? (145/200 = 0.725)
* What is the probability that a student likes basketball if we already know they like football? (120/160 = 0.75)

The concept behind __conditional probability__ is that a probability for one category depends on another category.
> What is the probability that a student likes basketball if we already know they like football?
> * $P(B\vert F) = 120/160 = 0.75$
> * $P(\bar{B}\vert F) = 40/160 = 0.25$

Equation for Conditional Probabilities:

$$P(B\vert A)=\frac{P(A~and~B)}{P(A)}$$

> * $P(B\vert F) = \frac{P(B~and~F)}{P(F)} = \frac{120/200}{160/200} = \frac{120}{160} = 0.75$

## AND Probabilities
Now that we have an equation for conditional probability, we can define the AND probability.

$$P(A~and~B) = P(B\vert A)P(A)$$

> __Magic Trick - Part 2__
> * Have 2 students draw cards and place them face down into the deck
> * Shuffle the deck and put it under the desk viewer
> * Calculate the probability that I draw both students' cards
> $$P(A~and~B) = P(B\vert A)P(A) = \frac{1}{51}\frac{1}{52} = \frac{1}{2652} = 0.000377$$
> * Reveal

> __Blackjack__: The goal of blackjack is to get as close to 21 as possible. Cards are awarded points as follows:
> * Face = 10
> * Numbers = numerical value
> * Ace = either 1 or 11, player's choice
> 
> If you already have a King, what is the probability of getting a blackjack?
>  * King = 10 -> Must get an Ace
> $$P(A ~ and ~ K) = P(A\vert K)P(K) = \frac{4}{51}\frac{4}{52} = \frac{16}{2652} = 0.00603$$

Notice that we could have swapped the order and gotten the same result:

> $$P(K~and~A) = P(K\vert A)P(A) = \frac{4}{51}\frac{4}{52} = \frac{16}{2652} = 0.00603$$

This leads to an important relationship:

$$P(A\vert B) = \frac{P(A~and~B)}{P(B)} \qquad P(B\vert A)=\frac{P(A~and~B)}{P(A)}$$

$$P(A\vert B)P(B) = P(A~and~B) = P(B\vert A)P(A)$$

> __Basketball__: From practicing free throw shots, I notice a pattern whenever I have 2 shots:
> * I have a 70% chance of making the first shot
> * If I make the first shot, I have a 75% chance of making the second
> * If I miss the first shot, I have a 60% chance of making the second
> 
> You come into the game just after I made a first shot, so you don't know if I made it or not. If I make the second shot, what's the probability that I made the first shot?
> 
> $$P(1~and~2) = P(1|2)P(2) \qquad P(1~and~2)= P(2|1)P(1)$$
>
> We want $P(1|2)$. We'll find $P(1~and~2)$, then solve for $P(1|2)$
>
> $$P(1~and~2) = P(2|1)P(1) = 0.75\cdot 0.70 = 0.525$$
>
> Now, we use $P(1~and~2$ to find $P(1|2)$
> * We are missing $P(2)$
>
> $$\begin{align*}
   P(2) &= P[(1~and~2) or (1^C and 2)] \\
        &= P(1~and~2) + P(1^C and 2) \\
        &= P(2|1)P(1) + P(2|1^C)P(1^C) \\
        &= 0.75\cdot 0.70 + 0.60\cdot 0.30 \\
        &= 0.525 + 0.18\\
        &= 0.705
   \end{align*}$$
>
> Now, we finish.
> 
> $$P(1|2) = \frac{P(1~and~2)}{P(2)} = \frac{0.525}{0.705} = 0.7447$$


> __Blackjack - Part 2__: If I draw a 9, what is the probability that I can get blackjack?
> * Blackjack means I get 21 points
> * I need 12 points. Different ways to get 12 points:
>    * Ace (11) and Ace (1): $P(A~and~A) = P(A\vert A)P(A) = \frac{3}{50}\frac{4}{51} = \frac{12}{2550} = 0.00471$
>    * Face and 2: $P(F~and~2) = P(F\vert 2)P(2) = \frac{12}{50}\frac{4}{51} = \frac{48}{2550} = 0.01882$
>    * 10 and 2: $P(10~and~2) = P(10\vert 2)P(2) = \frac{4}{50}\frac{4}{51} = \frac{16}{2550} = 0.00627$
> $$P((A~and~A) or (F~and~2) or (10~and~2)) = 0.00471+0.01882+0.00627 = 0.02980 = 2.98%$$

### Multiple AND Probabilities
What is $P(A~and~B~and~C)$?
* Treat $A~and~B$ as a separate event. Then,

$$P( [A~and~B]~and~C) = P(C|[A~and~B])P(A~and~B)$$

We already learned how to find $P(A~and~B)$, so,

$$P( [A~and~B]~and~C) = P(C|[A~and~B])P(B|A)P(A)$$

Continuing, we see a pattern: (For simplicity, let $P(A,B) = P(A~and~B)$)

$$P(A,B,C,D) = P(D|A,B,C)P(C|A,b)P(B|A)P(A)$$

$$P(A,B,C,D,E) = P(E|A,B,C,D)P(D|A,B,C)P(C|A,B)P(B|A)P(A)$$

> __Birthdays__: What is the minimum number of people needed in a room for there to be a 50% chance that at least 2 people share the same birthday?
> * It's easier to calculate the probability of all unique birthdays: $P(unique)$
> * Then take the complement: $P(\text{at least 2 shared birthdays}) = 1 - P(unique)$
>
> $$P(A) = \frac{365}{365} \qquad P(B|A) = \frac{364}{365} \qquad P(C|A,B) = \frac{363}{365} \qquad \dots$$
>
> $$P(all~unique) = P(A)P(B|A)P(C|A,B)P(D|A,B,C)\dots$$
>
> (Open excel and show these calculations and the product of all the probabilities)
>
> It takes 23 people to have less than 50% chance of everyone having a unique birthday

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

# Homework
(15 points)

## Reading
* 3.2 Conditional Probability

## Exercises
1. Exercise 3.5 from section 3.1
2. Exercise 3.6 from section 3.1
3. Exercise 3.7 from section 3.1
4. Exercise 3.9 from section 3.1
5. Exercise 3.10 from section 3.1
6. Exercise 3.13 from section 3.2
7. Exercise 3.15 from section 3.2
8. Exercise 3.17 from section 3.2
9. Exercise 3.41 from chapter 3 Exercises