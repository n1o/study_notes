# Markov chain monte carlo accuracy

Samples produces by MCMC are autocorrelated, and this reduces their information content relative to independent or perfect samples, we can quantify this as follows:

Suppose we want to estimate the mean of $f(x)$ for some function $f$, where $X \sim p()$. The true mean is:

$$f^* \triangleq E[f(x)] $$

A Monte Carlo estimate is given by:

$$ \bar{f} = \frac{1}{S} \sum_{s=1}^S f(x)$$

* $f_s \triangleq f(x_s)$
* $x_s \sim p(x)$

An MCMC estiamte of the variance of this estimate is given by:

$$
\text{Var}_{\text{MCMC}}[\bar{f}] = E[(\bar{f} - f^*)^2] \\
= E[\{ \frac{1}{S} \sum_{s=1}^S (f_s - f^*) \}^2] \\ 
= \frac{1}{S^2}E[\sum_{s=1}^S (f_s - f^*)^2] + \frac{1}{S^2}\sum_{s \ne t}E[(f_s - f^*)(f_t - f^*)] \\
= \text{Var}_{MC}(\bar{f})+ \frac{1}{S^2}\sum_{s \ne t}E[(f_s - f^*)(f_t - f^*)]
$$

The first term is the Monte Carlo estimate of variance if the samples weren't correlated, and the second term depends on the correlation of the samples. We can measure this as follows.

Define the sample-based autocorrelation at lag t of a set of samples $f_1, \cdots, f_S$ as follows:

$$
\rho_t = \frac{\frac{1}{S -t} \sum_{s=1}^{S-t}(f_s - \bar{f})(f_{s+t} - \bar{f})}{\frac{1}{S-t} \sum_{s=1}^S(f_s - \bar{f})^2}
$$

This is called the **autocorrelation function**.

A simple method to reduce autocorrelation is to use **thinning**, in which we keep every n'th sample. This one however does not increase the efficiency of the underlying sampler, but it does save space, sicne it avoids storing higly correlated samples. 

We can measure the information content of a set of samples by computing the **effective sample size (ESS)**:

$$
S_{\text{eff}} = \frac{\text{Var}_{MC}(f)}{\text{Var}_{MCMC}(f)}
$$
