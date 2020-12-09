## Numerically stable ridge regression computation

In general [ridge regression](ridge_regression.md) works better statistically, and it is also easier to numerically fit since $(\lambda I_D + X^TX)$ is much better conditioned especially for large $\lambda$ . But in general we do not want to invert it. ($N^3$)

If the prior is of the from $p(x) = N(0, \Lambda^{-1})$ where $\Lambda$ is the precision matrix. In case of the ridge regression it is $\Lambda = (1/\tau^2)$. To avoid penalizing $w_0$ we just center the data. Now we define the augumented matrices as:

$$\tilde{X} = \begin{bmatrix} X/\sigma \\ \sqrt{\Lambda} \end{bmatrix}, \tilde{y} = \begin{bmatrix} y/\sigma \\ 0_{D \times 1} \end{bmatrix}$$

* $\sqrt{\Lambda}$ is from [Cholesky decomposition](cholesky_decomposition.md) of $\Lambda = \sqrt{\Lambda}\sqrt{\lambda}^T$. 

The estimate for ridge becomes:

$$
\hat{w}_{\text{ridge}} (\tilde{X}^T \tilde{X})^{-1}\tilde{X}^T \tilde{y}
$$

Now if we perfrom [QR decomposition](qr_decomposition.md) of $\tilde{X}$ we get:

$$\tilde{X} = QR$$ 

Now:

$$(\tilde{X}^T\tilde{X})^{-1} = R^{-1}R^{-T}$$

Since R is upper triangular it is easy to invert. 

Now our ridge estimate is:

$$\hat{w}_{ridge}= R^{-1}R^{-T}R^T Q^T \tilde{y} = R^{-1}Q\tilde{y} $$

## $D >> N$

Than we first perform the [SVD](singular_value_decomposition.md) of $X = USV^T$ and define $Z = US$ than the estimation of ridge becomes:

$$ \tilde{w}_{ridge} = V(Z^TZ + \lambda I_N)^{-1}Z^Ty \\ 
= V(S^2 + \lambda I_N)^{-1}SU^Ty$$

Here the intuition is that we replace a D dimensional vectors $x_i$ by N dimensional $z_i$ and perform the penalized fit. And than we transform the N dimensional solution to the D dimensional solution by multiplying by V. Geometrically it can be viewed as the rotation to a new coordinate system, in which all but the first N coordinates are 0. The overal time it takes is $O(DN^2)$. We can connect this result to [PCA](ridge_regression_pca.md).