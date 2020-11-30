# Student T
Similar to Gaussian distribution with with heavier tails. 

$$X \sim T(\mu, \sigma^2, v)$$ 

## PDF:

$$T(x| \mu, \sigma^2, v) \propto  [ 1 + \frac{1}{v} (\frac{(x - \mu)^2}{\sigma})]^{-\frac{v+1}{2}}$$

Here 
* $\mu$ is the mean of the distribution
* $\sigma^2 > 0$ is the scale parameter
* $v > 0$ is called the **degrees of freedom**

If $\mathcal{v} = 1, \mu=0, \sigma = 1$ than 95% HDI is between $[-12.7, 12.7]$


# Moments
## Mean
$$E[X] = \mu $$

Is defined only if $v > 1$, this makes the tails so heavy that the integral for the mean does not converges. 

## Variance
$$var[X] = \frac{v \sigma^2}{(v - 2)}$$

Is defined only if $v > 2$

# Connections to Cauchy/Lorentz
If $v =1$ this distribution is also known as Cauchy or Lorentz distribution.

# Distribution

Let $Z \sim N(0,1), V \sim X^2_n$ where $Z\perp V$. Than we can express a Student t distribution with n degrees of freedom:

$$ T = \frac{Z}{V/n}$$


# Symetry arround arguments

Student T distribution is symmetric in its first two arguments

$$
T(\bar{x}| \mu , \sigma^2, v) = T(\mu| \bar{x}, \sigma^2, v)
$$

# t-distribution in place of the Normal for bayesian modelling
t-distribution has heavy tails and can be used to accommodate
1. occasional unusual observations in the data distribution 
2. occasional extreme parameters in a prior distribution of hierarchical model

t-distribution has 3 parameters $t_v(\mu, \sigma^2)$
* $\mu$ is the center 
* $\sigma$ is the scale
* $v$ are the degrees of freedom $v \in (0, \infty)$

If we fit an t-distribution using a large amount of data, we can estimate the degrees of freedom from the data.


# t -distribution as a mixture of Normals
We can draw sample $y_i \sim t_v(\mu, \sigma)$ using a mixture of Normals as:

$$ y_i \sim N(\mu, V_i) $$
$$  V_i \sim \text{Inv-X}^2 (v, \sigma)$$

* $V_i$ are the auxiliary variables
* $v$ is the degrees of freedom of the t-distribution

Now we assume the following distribution $p(\mu, \sigma^2, v| y)$

$$V_i | \mu, \sigma^2, v, t \sim \text{Inv-X}^2 (v+1, \frac{v \sigma^2 + (y_i - \mu)^2}{v+1})  $$

$$ \mu| \sigma^2, V, v, y \sim N(\frac{\sum_{i=1}^n \frac{1}{V_i}y_i }{}) $$

$$ p(\sigma^2| \mu, V, v, y) \propto \text{Gamma}(\sigma^2| \frac{nv}{2}, \frac{v}{2} \sum_{i=1}^n \frac{1}{V_i} ) $$

Unfortunately this is not very efficient because $\sigma$ and $V_i$ are dependent, thus if $\sigma$ is close to zero, than we will saple $V_i$ close to zero and vice versa. 

We can solve this by adding an extra parameters. This random parameter will result in an random walk on a larger space, which unexpectedly improves convergence. Thus our new model is:

$$ y_i \sim N(\mu, \alpha^2U_i) $$

$$ U_i \sim \text{Inv-X}^2(v, \tau^2) $$

* $\alpha$ is the additional scale parameter, it has no meaning hence we can use an uniform prior on a log scale
* $\alpha^2U_i$ are the auxiliary variables
* $\alpha \tau$ plays the role of $\sigma$ in the original model



$$ U_i | \alpha, \mu, \tau^2, v , y \sim \text{Inv-X}^2 (v + 1, \frac{v \tau^2 +((y_i - \mu) / \alpha)^2}{v + 1}) $$

$$ \mu | \alpha, \tau^2, U, v, y \sim N(\frac{ \sum_{i=1}^n \frac{1}{\alpha^2U_i}y_i }{\sum_{i=1}^n \frac{1}{\alpha^2U_i}}, \frac{1}{\sum_{i=1}^n \frac{1}{\alpha^2 U_i}}) $$

$$\tau^2| \alpha, \mu, U, v, y \sim \text{Gamma}(\frac{nv}{2}, \frac{v}{2} \sum_{i=1}^n \frac{1}{U_i}) $$

$$\alpha^2 | \mu, \tau^2, U, v, y \sim \text{Inv-X}^2 (n, \frac{1}{n}\sum_{i=1}^n \frac{(y_i - \mu)^2}{U_i}) $$

We only need $\mu, \sigma$ the rest we can drop
