# Mahalanobis distance
Is a measure of distance between a point P and a distribution $D$. It is a mutli-dimensional generalization of the idea of how many [standard deviations](expectations.md) away P is from the mean of D. This distance is zero if P is at the mean of D, and grows away from the mean along each principal component axis. It corresponds to standard Eucliedan distance in the transformed space.

It is unitelss and scale-invariant and it takes into account the correlations of the dataset.

$$
D_m(x) = \sqrt{(x - \mu ) S^{-1} (x - \mu)}
$$

* $x=(x_1, x_2, \cdots, x_N)^T$
* $\mu = (\mu_1, \mu_2, \cdots, \mu_N)^T$
* $S$ is the covariance matrix

Here $A \in R^{n \times n}$ and $v \in R^n$