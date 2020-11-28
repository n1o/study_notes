# Variance stabilizing transformation

Suppose $E[X] = \mu$ and $var[X] = \sigma^2(\mu)$. Let $Y = f(x)$ we pefrom a taylor series expansion:

$$
Y \approx f(\mu) + (X - \mu)f'(\mu)
$$

Hence 
$$
var[Y] = f'(\mu)^2 var[X - \mu] = f'(\mu)^2 \sigma^2(\mu)
$$

A variance stabilizing transformation is a function $f$ such that $f'(\mu)^2 \sigma^2(\mu)$ is independent of $\mu$

