# Probability mass functions
It is defined for discrete [random variables](random_variable.md). It measures the probability associated with for each possible random variable. The **pmf** can be viewed as a function $p_X: \Omega \rightarrow R$ such that

$$
p_X(x) = P(X = x)
$$

## Properties
* $0 \le p_X(x) \le 1$
* $\sum_{x \in Val(X)} p_X(x)=1$
* $\sum_{x \in A} p_X(x) = P(X \in A)$

# Probability density function
It is defined for continuous [random variables](random_variable.md) and iit is defined as the derivative of the [CDF](cumulative_distribution_function.md):

$$
f_X(x) = \frac{dF_X(x)}{dx}
$$

This may not exists if the CDF is not differentiable everywhere.