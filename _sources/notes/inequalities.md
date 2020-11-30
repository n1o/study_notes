# Inequalities
We can use inequalities to give us provable guarantee that a probability is in within some reasonable range. 

## Cauchy-Schwartz

It follows that, given two random variables Y and X 

$$ |E(XY)| \le \sqrt{E(X^2)E(Y^2)}  $$

* equality holds only if the two random variables are independent.


If we substitute $Y=1$ than we get the form:

$$E[X \times 1] \le \sqrt{E[X^2]E[1^2]} \Rightarrow E[X^2] \ge (E[X])^2 $$

This can than be showed that the sample standard deviation is biased.

### Second order method
Let X be a random variable, now we want to bound the probability of $P(X=0)$. As an example that X is the number of questions that we get wrong. Thus we want to find a bound on the probability that we wont make a mistake. 

To to this we start with an indicator variable:
$$ X = XI(X>0) = P(X>0)$$

$$P(X=0) = \frac{Var[X]}{E[X^2]}$$

![](inequalities.assets/second_order_method.png)

### Jensens inequality and convexity
Tels us about the relationship between 


# Markov inequality
It gives us bounds on the probability that a random variable will take extreme values (far from the mean) in its tails. We require that this distribution has a stable mean. 

Markov inequality gives bounds on its mean. 

$$P(|X| \ge a) \le \frac{E|X|}{a} $$

Thus as an example if $a = 3E[X]$ than we have $P(X \ge 3E[X]) \le 1/3$ thus we cannot have more than 1/3 of the population having the probability greater than 3 times the average.

# Chebyshev

Gives us an upper bound on the probability that a r.v is being more than c standard deviations away from its mean. 

$$ P(|X - \mu| \ge c \sigma) \le \frac{1}{c^2}$$

Thus as an example we cannot have more than 25% of the population be father away than two standard deviations from the mean.

