# PMF/PDF of a function of random variables

Given a [random variable](./random_variable.md) X, the pdf of X is $P(X = x)$, now if we have a [function](./functions_of_random_variables.md) $Y = f(X)$ we may want to find $P(Y = y)$. This process is similar to change of variables in integration. Fortunately if $P(X = x)$ is known we may express $P(Y = y)$ using $P(X = x)$.

$$
P(Y = g(x)) = P(g(X) = g(x)) = P(X = x)
$$

Which end up as:

$$
(P(g(X) = y) = \sum_{x: g(x) = y} P(X = x)
$$
Since $g$ does not necessarily is a one-to-one function, we may need to sum up the values. (For continuous functions we replace the sum for an integral).

# Continuous
If X is continous and f is smooth than $Y = f(X)$ is given:

$$ p_y(y) = p_x(x) |\frac{dx}{dy} | $$

This is the change of variables formula
where:
* $|\frac{dx}{dy} |$ can be viewed as the change in volume as we move from x into y space.

We can extend this to multiple dimension here we need to define the [Jacobian](jacobian.md).

$$p_y (y) = p_x (x) |\det (\frac{\partial x}{\partial y})| $$
$$p_y (y) = p_x (x) |\det J_{y \rightarrow x}| $$
