# Gaussian process latent variable model
This can be viewed as an combination of probabilistic PCA and kernels.

[Probabilistic PCA](principal_component_analysis.md) model is defined as:

$$
p(z_i) = \mathcal{N}(z_i|0,I) \\
p(y_i|z_i, \theta) = \mathcal{y_i| Wz_i, \sigma^2I}
$$

We can find the MLE of this problem by computing the eigenvectors of $Y^TY$

The dual of this problem we use a prior $P(W) = \prod_j \mathcal{N}(w_j| 0, I)$. We want to maximize $Z$ and integrate $W$ out. 

$$
p(Y| Z, \sigma^2) = \prod_{d=1}^D \mathcal{N}(y_{:.d}| 0, ZZ^T + \sigma^2I) \\
= (2\pi)^{-DN/2}|K_z|^{-D/2} \exp(-\frac{1}{2}tr(K_z^{-1}YY^T))
$$

* $K_z = ZZ^T + \sigma^2I$

This method can also be solved by finding the eigne values. If we use an linear kernel we can recover PCA but we can use an more general kernel $K_z = K + \sigma^2I$ where $K$ is a Gram matrix for Z.

Unfortunately no longer we can use the eigenvalue method, instead we use a gradient-based optimizer. Our loss function is:

$$
l = - \frac{D}{2} \log |K_z| - \frac{1}{2}tr(K_z^{-1}YY^T)
$$

The gradient is given by 
$$
\frac{\partial l}{\partial Z_{ij}} = \frac{\partial l}{\partial K_z} \frac{\partial K_z}{\partial Z_{ij}}
$$

* $\frac{\partial l}{\partial K_z} = K_z^{-1}YY^T K_z^{-1} - DK_z^{-1}$
* $\frac{\partial K_z}{\partial Z_{ij}}$ depends on the kernel used

In kernelized PCA, we learn a kernelized mapping from the observed space to the latent space, whereas in GP-LVM, we learn a kernelized mapping from the latent space to the observed space.

GP-LVM inherits the usual advantages of probabilistic generative models, such as the ability to handle missing data and data of different types, the ability to use gradient-based methods (instead of grid search) to tune the kernel parameters, the ability to handle prior information.