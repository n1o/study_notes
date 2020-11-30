# Convolution

If X and Y are booth [random variables](./random_variable.md) than $T = X + Y$ is also random variable. Now we may want to find the PDF (PMF) $P(T = t)$. In the case that X and Y are independent, and we know their PDF we can express:

$$
P(T = t) = \sum_x P(Y = t - x)P(X=x) = \sum_y P(X = t - y)P(Y = y) 
$$