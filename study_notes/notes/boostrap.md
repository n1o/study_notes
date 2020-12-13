# Boostrap
Monte carlo method to approximate the sampling distribution. It is particulary usefull when the estimator is a complex function of the true parameters. The idea is:

Given we known the true parameters $\theta^*$, we can generate many (say S) fake datasets each of size N, from the true distribution $x_i^s \sim p(\cdot| \theta^*)$ for $s = 1: S, i=1:N$ now we can compute our estimator from each sample $\hat{\theta}^s = f(x_{1:N}^s)$ and use the empirical distribution of the resulting samples as our estimate of the sampling distribution. Since in general $\theta$ is unknown we can use **parametric bootstrap** to generate samples using $\hat{\theta}(D)$ instead. Or **nonparametric boostrap** to sample $x_i^s$ (with replacement ) from the original dataset D.

We can think of Boostrap as a "poor man's" posterior. Since in the case when the prior is not strong, the sampling distribuiton and the posterior can be quite similar. 