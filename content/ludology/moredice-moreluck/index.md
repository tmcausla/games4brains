# Does More Dice = More Luck?

[< Back Home](/)

There's little else as satisfying as the clickity clack of dice being cast upon a table.  Dice are most commonly used as a way to inject randomness into its system.  So does it stand to reason that more dice should produce more randomness?

Actually no.

## The Situation

To understand this we need to think of randomness as the probability spread of possible outcomes in a random event.  If each outcome has an equal probability, such as rolling a single six-sided die (d6), this could be thought of as a more purely random event because each die face 1-6 will appear a _mostly_ equal number of times.  

Once you add a second die to the roll and count the possible outcomes as the combined values on both dice, the probability of each outcome is no longer an equal distribution.  In the case of rolling two d6 (2d6), the outcome with the highest probability is the outcome 7.  

```
1 + 6
2 + 5
3 + 4
4 + 3
5 + 2
6 + 1
6/36 = 1/6 = 16.667%
```

As soon as you start rolling more than one die, the averages of outcomes start to center around a single value.  So by rolling **more** dice, you're causing certain values to be **more likely** to appear.  

## The Math

I made a program that simulated dice rolls, tallied the outcomes for each possible value, and produced a bar chart with the results.

![bar charts of dice rolling simulations](/images/dice-roll-trials.png)

## The Psychology

ABC

[< Back Home](/)
