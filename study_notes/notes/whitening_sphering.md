# Whitening or sphereing
Is a process that ensures that the empirical covariance matrix is proportional to $I$, so the data is uncorrelated and of equal variance along each dimension. For each $x$ we compute:

$$\Lambda^{-\frac{1}{2}}U^Tx$$

* $\Lambda$ matrix of eigenvalues of X
* $U$ the eigen vectors of $\Sigma$