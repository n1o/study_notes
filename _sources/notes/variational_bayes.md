# Variational bayes

So far we were infering latent varialbes $z_i$ assuming the parameters $\theta$ of the model are known. No we want to infer the parameters themselves. If we make a fully factorized approximation: $p(\theta|D) \approx \prod_k q(\theta_k)$. This method is known as **variational bayes (VB)** . Unfortunately deriving VB algorithms can be heavy on algebra, however, the resulting methods are usualy fast as MAP estimations, but enjoy the benefits of Bayesian approach. 

If we want to infer booth latent variables and parameters, and we make an approximation of the form $p(\theta, z_{1:N} |D) \approx q(\theta) \prod_{i}q_i(z_i)$ we get a method known as **variational bayes EM**.

## Lower bound

In VB, we are maximizing $L(q)$, which is a lower bound on the log marginal likelihood:

$$L(q) \le \log p(D) = \log \int \int p(D| \mu, \lambda) p(\mu, \lambda) d\mu d \lambda $$

(this is an example for an univariate Gaussian)

We can use this lower bound to:
* assess convergence of the algorithm
* assess correctness of code (the bound does not increase monotonically)
* used as an approximation to the marginal likelihood, which can be used for Bayesian model selection.
## Compared to EB

Most of the times VB will give similar results as EB, but the precise behavior depends on the sample size. If the sample size is small, VB's estimate of the posterior over models is more diffuse than EB's, since VB models uncertainty in the hyper-parameters. 
