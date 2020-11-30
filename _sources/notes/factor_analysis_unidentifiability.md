# Factor analysis unidentifiability

Just like with mixture models, [FA](factor_analysis.md) is also unidentifiable. This makes it hard for interpretation. An example we take a orthogonal rotation matrix $R$ that sattisfy $RR^T = I$ Now if we rotate $W$

$$
\tilde{W} = WR
$$

The likelihood function of this modified matrix is the same as for the unmodified matrix:

$$
cov[x] = \tilde{W}E[zz^T] \tilde{W}^T + E[\epsilon^T \epsilon]  \\
= WRR^TW^T + \Psi = WW^T + \Psi
$$

Geometrically, multiplying $W$ by an orthogonal matrix is like rotating $z$ before generating $x$, but since $z$ is drawn from an isotropic Gaussian, this makes no difference to the likelihood. Consequently, we cannot unique identify $W$, and therefore cannot uniquely identify the latent factors, either.

To solve this we can:

* Force $W$ to be **orthonormal** (PCA)
* Force $W$ to be **lower triangular**

* **Sparsity promoting priors on the weights** whe encourage entries in $W$ to be zero.  (Also called sparse factor analysis, this encourages interpretability)
* **Choosing an informative rotation matrix** (Varimax)

* **Use of non-Gaussian priors for the latent factors** $p(z_i)$ is not a Gaussian distribution (**ICA**)
