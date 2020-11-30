# Wishart distribution
Generalization of the Gamma distribution to positive definite matrices. It is used to model uncertainity in covariance matrices, and in their iverses $\Lambda =\Sigma^{-1}$. 

## PDF:
$$ Wi(\Lambda | S,v) = \frac{1}{Z_{Wi}}|\Lambda|^{(v - D - 1)/2} \exp (-\frac{1}{2} tr(\Lambda S^{-1})) $$

Where:
* v is called the degrees of freedom
* S is the scale matrix. 
* $Z_{Wi} = 2^{vD/2} \Gamma_D(v/2)|S|^{v/2}$ is the normalization constant
* $\Gamma_D(a)$ is the multivariate [gamma function](gamma_function.md)

The normalization constant exists only if $v > D-1$. 

## Moments:
$$X \sim Wi(S, v)$$

### Mean
$$E[X] = vS$$

### Mode
$$(v - D -1)S $$
Where it exists only if $v > D +1$

## Connection to Gamma distribution:
If D = 1: 

$$ Wi(\lambda| s^{-1}, v)= Ga(\lambda| \frac{v}{2}, \frac{s}{2})$$

This makes marginal distributions Gamma.

### Connection with Gaussian distribution:
Let $x_i \sim \mathcal{N}(0,\Sigma)$, then the scatter matrix $S = \sum_{i=1}^N x_ix_i^T$ has a Wishart distribution. $S \sim Wi(\Sigma, 1)$. Hence $E[S] = N \Sigma$. 


# Example:

![Samples drawn from wishart](../.images/wishart_dist_visualization.png)

$S = [3.1653, -0.0262; -0.0262, 0.6477], v=3$