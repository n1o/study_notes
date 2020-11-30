# Laplace distribution (Double exponential)
This distribution is robust to outliers, and puts more weight to values closer to 0 than a Gaussian distribution. This property is useful to encourage sparsity in a model.

$$X \sim Lap(\mu, b)$$

## PDF:

$$Lap(x| \mu, b) \triangleq \frac{1}{2b}\exp {( - \frac{|x - \mu |}{b} )}$$

Here:
* $\mu$ is a location parameter
* $b$ is a scale parameters

# Moments

## Mean
$E[X] = \mu$

## Variance
$var[X] = 2b^2$
