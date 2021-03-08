# Expectations
Given an random variable $X$ with PDF $f(x)$ we define its expected value (**mean**) as:

$$
E[X] = \int_{-\infty}^{\infty} xp(x)dx \\
$$

# Functions of random variables

Given a [function](functions_of_random_variables.md) $g: R \rightarrow R$, $g(X)$ is also an random variable we define its expectation as:

$$
E[g(X)] = \int_{-\infty}^{\infty} g(x)p(x)dx \\ 
= E_{x \sim p(x)}[g(x)]
$$

This is the weighted average of $g$. In the special case when $g$ is the *identity* function we get **mean**.

## Properties
* $E[a] = a$ for any constant $a$
* $E[af(X)] = a E[f(X)]$ for any constant $a$
* $E[af(X) + bg(X)] = aE[f(X)] + bE[g(X)]$ Linearity 

# Variance
Variance of a random variable X is a measure how concentrated the distribution of a random variable X is around its mean. 

$$
Var[X] = E[(X - E[X])^2] = E[X^2] - E[X]^2
$$
**Units of variance are the squared units of the original**.

## Properties
* $Var[a] = 0$ for any constant
* $Var[f(x) + a] = Var[f(x)]$  for any constant $a$, thus shifting an random variable has no effect on its variance.
* $Var[af(X)] = a^2Var[f(X)]$ for any constant $a$. Variance is measured in units squared thus any constant is also squared
* $Var[f(x) + g(Y)] = Var[f(Y)] + Var[g(Y)]$ if $X \perp Y$

## Standard deviation
We take the square root of the variance.
$$
std[X] = \sqrt{Var[X]}
$$

**Standard deviation has the same units as the original**

# Skew

# Curtosis
# Discrete random variables
More or less the same but we replace the integration with a sum over the domain of a random variable.