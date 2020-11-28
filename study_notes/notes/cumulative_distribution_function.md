# Cumulative distribution function

It is a function $F_X: R \rightarrow [0,1]$ which sprecifies a probability measure:

$$
F_X(x) = P(X \le x)
$$

This is the probability that a random variable will be less then $x$. We can use it to calculate the probability that a random variable will be within some bounds $a,b$ where $a < b$.

## Properties 

* $0 \le F_X(x) \le 1$
* $\lim_{x \rightarrow - \infty} F_X(x) = 0$
* $\lim_{x \rightarrow \infty} F_X(x) = 1$
* $x \le y \Leftrightarrow  F_X(x) \le F_X(y)$