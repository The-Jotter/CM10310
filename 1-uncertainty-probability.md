# Uncertainty and Probability

The language of probability and using
probabilistic reasoning can be used to act in
situations where the consequences of actions are not known beforehand.

## But first, Definitions and Notations

### Random Variable
Denotes an uncertain quantity.

### Probability Distribution
Looking at the differences in likelihood between outcomes.

### Experiment
Testing for these outcomes is called an experiment.

### Sample Space
The set of all possible outcomes.

### Events
An event is a set of particular possible outcomes.
The probability of an event is equal to the sum of all the outcomes.

## Probability 
### Joint Probability
Events that rely on multiple independent variables can be joined together. $p(X, Y)$ denotes that both $X$ and $Y$ must both happen.

### Conditional Probability
> $X$ given $Y$

The probability of an event given that we have other information.

$p(\text{Raining}\ |\ \text{Cloudy})$
> The probability that it is rainy given it is raining.

### Product Rule for Probability
In general, for two events $X$, $Y$:


$p(X,Y) = p(X|Y)\cdotp(Y)$
or $p(X,Y) = p(Y|X)\cdotp(X)$

If $X$ and $Y$ are independent, then $p(X|Y) = p(X)$.
Therefore, $p(X, Y) = p(X) \cdot p(Y)$

### Sum Rule for Probability

$p(X)=\sum_{Y}p(X, Y)=\sum_{Y}p(X|Y)p(Y)$
where $p(X)$ is called the "marginal probability".

This rule can be useful for estimating the probability of an uncertain event when you only have access to it given another.

### Bayes' Rule
$p(X,Y)=p(X|Y) \cdot p(Y)=p(Y|X) \cdot p(X)$

Or more commonly,
$p(X|Y)=\frac{p(Y|X) \cdot p(X)}{p(Y)}$

Where:

| Notation  | Description                      |
|-----------|----------------------------------|
|$p(X)$     | Prior belief                     |
|$p(Y\|X)$  | Liklihood                        |
|$p(X\|Y)$  | Posterior belief                 |
|$p(Y)$     | Evidence, or marginal likelihood |