
# Chi-Squared distribution
Chi squared is related to the distribution of the sample variance, and can be used to estimate the true [variance](expectations.md) of the distribution.

$$
S \sim X^2_v 
$$

## Moments

## Mean
$$E[S] = v$$

## Variiance
$$Var(S) = 2v$$

# Connection to Gaussian
A Chi-Square with $v$ degrees of freedom can be defined as a sum of $v$ [standard normals](gaussian_distribution.md).

$$ S \sim X^2_v \\  S = \sum_{i=1}^{v} Z_i^2  \\ Z_i \sim N(0,1)$$

# Connection to [Gamma](gamma_distribution.md)

$$X^2_v \triangleq Ga(\frac{v}{2}, \frac{1}{2})$$


