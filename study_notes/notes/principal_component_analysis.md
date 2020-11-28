# Principal component analysis

It is actually an version of [FA](factor_analysis.md) where we restrict $\Psi = \sigma^2 I$ and $W$ to be orthonromal. If $\sigma^2 > 0$ than it is **probabilistic PCA** if $\sigma^2 \rightarrow 0$ we reduce to [classical PCA](classical_pca.md) 

# Probabilistic PCA

It is just [Factor analysis](factor_analysis.md) in which $\Psi = \sigma^2I$ and $\sigma^2 > 0$ and $W$ is orthogonal. Hence the log likelihood of the observed data is given (We assume the data is centered):

$$\log p(X|W, \sigma^2) = - \frac{N}{2} \ln |C| - \frac{1}{2}\sum_{i=1}^N x_i^T C^{-1}x_i = -\frac{N}{2} \ln |C| + tr(C^{-1}\Sigma) $$

* $C = WW^T + \sigma^2I$

* $S = \frac{1}{N} \sum_i^N x_ix_i^T = (1/N)X^TX$ 

The maximum of the log likelihood is:

$$\hat{W} = V (\Lambda - \sigma^2I)^{\frac{1}{2}}R$$

* $R_{L\times L}$ abitrary orthogonal matrix and without loss of generality can be set to I
* $V_{D\times L}$ the first L eigenvectors of S 
* $\Lambda$ diagonal eigen values 

The MLE of the noice variance is:

$$\hat{\sigma}^2 = \frac{1}{D - L} \sum_{j = L+1}^D \lambda_j$$

If $\sigma^2 \rightarrow 0$ then $\hat{W} \rightarrow V$ and ve get classical PCA.

The posterior predictive distribution over latent factors is given by:

$$ P(z_i| x_i, \hat{\theta}) = N(z_i| \hat{F}^{-1} \hat{W}^Tx_i, \sigma^2 \hat{F}^{-1}) \\ 
\hat{F} \triangleq \hat{W}^T \hat{W} + \hat{\sigma}^2I $$

Thus the posterior mean is obtained by an orthogonal projection of the data onto the column space of V. 

This can be fit using [em](probabilistic_pca_em).

There are also some [extension](pca_extensions.md) that enables to use pca for categorical variables on in supervised manner. 