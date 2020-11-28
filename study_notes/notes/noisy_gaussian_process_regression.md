# Noisy Gaussian process Regerssion
Here we assume:

$y = f(x) + \epsilon$

* $\epsilon \sim N(0, \sigma^2_y)$

Here the model is not required to interpolate the data, but it must come close to the observed data. 

The covariance of this model is given by:

$$
cov[y_p, y_q] = \mathcal{k}(x_p, x_q) + \sigma_y^2 \delta_{pq} \\
cov[y|X] = K + \sigma_y^2I_N = K_y
$$

* $\delta_{pq} = I(p = q)$

The second term is diagonal because we assumed that the nise terms are independently added to each observation. 

The join density of the observed data and the latent, noise-free function ($f_*$)on the test points is given:

$$
\begin{pmatrix}
    y \\ f_*
\end{pmatrix} \sim \mathcal{N}(0, \begin{pmatrix} K_y & K_* \\ K_*^T & K_{**} \end{pmatrix})
$$

Here we assume the mean is zero for notational simplicity. The posterior predictive density is:

$$
p(f_*| x_*, X, y) = \mathcal{N}(f_*|\mu_*, \Sigma*) \\
\mu_*  = K_*^TK_y^{-1}y \\
\Sigma_* = K_{**} - K^T_*K_y^{-1}K_*
$$

We can write the posterior mean as:

$$\hat{f}_* = k_*^TK_y^{-1}y = \sum_{i=1}^N \alpha_i \mathcal{k}(x_i, x_*)$$

* $\alpha = K_y^{-1}y$