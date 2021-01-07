# Variational bayes EM

If we consider a model of the form $z_i \rightarrow x_i \leftarrow \theta$. This includes mixture models, PCA, HMM, etc. There are two kind of unknonws: parameters $\theta$ and latent variables $z_i$. 

It is common to use EM to fit this models, where in E step we infer the posterior over the latent variables $p(z_i| x_i, \theta)$ and in the M step we compute a point estimate of the parameter $\theta$. We can justify this by assuming that the posterior uncertainty in $\theta$ is in general smaller than in $z_i$, since $\theta$ is informed by all N data cases, whereas $z_i$ is only informed by $x$, this makes MAP estimation of $\theta$ more reasonable than MAP estimate of $z_i$

Variational Bayes provides a way to be "more Bayesian", by modelling uncertainty in the parameters $\theta$ as well in the latent variables $z_i$, at a computational cost that is essentially the same as EM.

This method is known as **variational Bayes EM (VBEM)**. The basic idea is to use mean field, where the approximate posterior has the form:

$$p(\theta, z_{1:N}|D)  \approx q(\theta) q(z) = q(\theta) \prod_i q(z_i)$$

The first factorization, between $\theta$ and $z_i$ is crucial assumption to make the algorithm tractable. The second factorization follows from the model, since the latent variables are iid conditional on $\theta$. 

In VBEM we alternate between updating $q(z_i|D)$ (the variational E step) and updating $q(\theta|D)$ (the variational M step). We can recover standard EM from VBEM by approximating the parameter posterior using a delta function $q(\theta|D) = \delta_{\hat{\theta}}(\theta)$.

**Variational E step** is similar to a standard E step, except instead of plugging in a MAP estimate of the parameters and computing $p(z_i|D,\theta)$ we need to average over the parameters. 

**Variational M step** is similar to standard M step, except instead of computing a point estimate of the parameters, we update the hyperparameter, using the expected sufficient statistics. 

The principle advantage of VBEM over regular EM is that by marginalizing out the hyperparameter, we can compute a lower-bound on the marginal likelihood, which can be used fro model selection. 
