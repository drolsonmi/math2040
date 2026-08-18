# Lab 2: Analysis












* Mean
* Quartiles
* Boxplots
* Counting

How?
* Load a dataset in python using pandas
* Identify the quantitative and categorical variables
* Instruction sheet with (is there a cheat sheet?)
    * How to find the mean, standard deviation, 5-number summary: `df.describe()`
    * How to make a boxplot
    * How to count of categories
    * How to make probabilities
    * 

https://www.datacamp.com/cheat-sheet/pandas-cheat-sheet-for-data-science-in-python


## FOR loops

## 
> __Repeated Birthdays__: How many people need to be in a room before there is more than a 50% chance of a repeated birthday? (Assume 365 days in a year)
> * Easier to think of probability that birthdays are NOT repeated. That is, what is the probability that someone who walks into a room has a unique birthday?
>   * Person 1 enters. His probability of a unique birthday is $P(1) = \frac{365}{365}$
>   * Person 2 enters. His probability of a unique birthday is $P(2) = \frac{364}{365}$
>   * Person 3 enters. His probability of a unique birthday is $P(3) = \frac{363}{365}$
>   * Person 4 enters. His probability of a unique birthday is $P(4) = \frac{362}{365}$
>   * Person 5 enters. His probability of a unique birthday is $P(5) = \frac{361}{365}$
>   * Person 6 enters. His probability of a unique birthday is $P(6) = \frac{360}{365}$
>   * Person 7 enters. His probability of a unique birthday is $P(7) = \frac{359}{365}$
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
> Therefore, taking the complement, it takes 23 people to have a probability greater than 50% that *somebody* has repeated a birthday.