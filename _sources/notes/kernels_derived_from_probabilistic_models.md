# Kernels derived from probabilistic generative models

Suppose we have a probabilistic generative model of feature vectors, $p(x|\theta)$. Then there are several ways we can use this model to define kernel functions, and thereby make the model suitable for discriminative tasks.

## Probability product kernels

One approach is to define a kernel as follows:

$$
\mathcal{x}(x_i, x_{j}) = \int p(x|x_i)^{\rho}p(x|x_j)^{\rho}dx
$$

* $\rho \ge 0$
* $p(x|x_i)$ is ofthen approximated by $p(x| \hat{\theta}(x_i))$ where $\hat{\theta}(x_i)$ is a parameter estimate computed using a single data vector. 

It may sound strange to fit a model only to a single data vector, but we use this kernel to compare two objects. 

It turns out that one can compute the above equations for a variety of generative models, including ones with latent variables, such as HMMs. This provides one way to define kernels on variable length sequences.

## Fisher kernels
A more efficient way to use generative models to define kernels is to use a Fisher kernel defined as:

$$
\mathcal{k}(x_i, x_j) = g(x)^TF^{-1}g(x_j)
$$

* $g(x) = \nabla_{\theta} \log p (x|\theta)|_{\hat{\theta}}$ 
  * It is the gradient of the log likelihood evaluated at the MLE $\hat{\theta}$ 
* $F = \nabla \nabla \log p(x|\theta)|_{\hat{\theta}}$ 
  * It is the [Fisher information matrix](fisher_information_matrix.md), which is just the Hessian of the log likelihood evaluated at the MLE $\hat{\theta}$

Note that $\hat{\theta}$ is a function of all the data, so the similarity of $x$ and $x'$ is computed in the context of all the data as well. This means that it is enought to fit one model. 

The intuition behind the Fisher kernel is:
> Let $g(x)$ be the direction (in parameter space) in which x would like the parameters to move (from $\hat{\theta}$) so as to maximize its own likelihood; call this the directional gradient.  Then we say that two vectors $x$ and $x'$  are similar if their directional gradients are similar wrt the the geometry encoded by the curvature of the likelihood function.