# Inverse Wishart distribution

If $\Sigma^{-1} \sim Wi(S,v)$ than $\Sigma \sim IW(S^{-1}, v + D + 1)$ where IW is the inverse [Wishart](wishart_distributiion.md), and it can be viewed as the generalization of [Inverse Gamma distribution](inverse_gamma.md). 

It is defined if $v > D -1$

$$IW(\Sigma| S, v) = \frac{1}{Z_{IW}} |\Sigma|^{-(v + D +1)/2} \exp (-\frac{1}{2} tr(S^{-1}\Sigma^{-1})) $$

## Moments
$$
X \sim IW(S^{-1}, v+D+1)
$$

### Mean
$$E[X] = \frac{S^{-1}}{v - D - 1} $$

### Mode
$$\frac{S^{-1}}{v - D + 1} $$

## Connection to Inverse Gamma
In case of D = 1
$$ IW(\sigma^{2}| S^{-1}, v) = IG(\sigma^{2}| v/2, S/2)$$
