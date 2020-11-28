# Inverse Gamma
It is the inverse of a [Gamma distribution](gamma_distribution.md):

$$
Y \sim IG(a,b) \\
Y = \frac{1}{X} \\
X \sim Ga(a,b
$$

# PDF
$$ IG(x| a, b) \triangleq \frac{b^a}{\Gamma(a)} x^{- (a+ 1)}e ^{- b/x} $$

# Moments
## Mean
$E[X] = \frac{b}{a -1}$

Exists only if $a > 1$
## Variance
$var[X] = \frac{b^2}{(a - 1) ^2 (a - 2)}$ 

Exists only if $a > 2$

## Mode
$mode(X) = \frac{b}{a +1}$

