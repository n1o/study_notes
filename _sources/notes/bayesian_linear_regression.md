# Bayesian linear regression

Instead of point estimates sometimes we want to compute the full posterior over $w$ and $\sigma^2$

## Computing the posterior (Known variance)

The linear regression likelihood functions is given as

$$p(y|X, w, \mu, \sigma^2) = \mathcal{N}(y| \mu + Xw, \sigma^2 I_N) $$

We put an inproper prior on $\mu$ (This is because if we center the data, the mean of the ouput is equally to be positive or negative) of the form $p(\mu) \propto 1$ then we can express the likelihood as:

$$p(y|X, w, \mu, \sigma^2) \propto \exp (-\frac{1}{2 \sigma^2} || y - \bar{y}1_N - Xw ||_2^2) $$

* $\bar{y} = \frac{1}{N}\sum y_i$

Now the conjugate prior for a Gaussian is also Gaussian:

$$ p(w|X, y, \sigma^2) = \mathcal{N}(w| w_0, V_0) $$

Than the posterior is a Gaussian Linear system the form:

$$p(w| X, y, \sigma^2) \propto \mathcal{N}(w| w_0, V_0)\mathcal{N}(y|Xw, \sigma^2I_n) = \mathcal{N} (w| w_N, V_N) $$

* $w_N = V_n V^{-1}_0 w_0 + \frac{1}{\sigma^2}V_n X^Ty$
* $V_N^{-1} = V_0^{-1} + \frac{1}{\sigma^2}X^TX$
* $V_n = \sigma^2(\sigma^2V_0^{-1} + X^TX)^{-1}$

If we set $w_0 = 0, V_0  = \tau^2I$ then the posterior mean reduces to the ridge estimate, if we define $\lambda = \sigma^2/ \tau^2$

We can use this for online-learning, where the posterior afther observing the current value will become the prior for the next computation.

## Computing posterior if $\sigma^2$ is unknown

The likelihood is of the form:

$$p(y|X, \sigma^2) = \mathcal{N}(y| Xw, \sigma^2 I_N)$$

The conjugate prior is a Normal Inverse Gamma:

$$p(w, \sigma^2) = NIG(w, \sigma^2| w_0, V_0, a_0, b_0)$$

Hence the posterior is also NIG:

$$p(w, \sigma^2|D) = NIG(w, \sigma^2| w_N, V_N, a_N, b_N)$$

* $w_n =  V_N(V_0^{-1}w_0 + X^Ty)$
* $V_n = (V_0^{-1} + X^TX)^{-1}$
* $a_n = a_0 + n/2$
* $b_n = b_0 + \frac{1}{2}(w_0^TV_0^{-1}w_0+y^Ty - w_N^TV_N^{-1}W_n)$ this can be interpreted as the prior sum of squares plus the empirical sum of squares plus a term due the error in the prior of w. 

The posterior marginals are:

* $p(\sigma^2|D) = IG(a_N, b_N)$
* $p(w|D) = \mathcal{T}(w_N, \frac{b_n}{a_n}V_n, 2a_N)$

The posterior predictive distribution is a Student t. Given m new test inputs $\tilde{X}$

$$p(\tilde{y}| \tilde{X},D) = \mathcal{T}(\tilde{y}|\tilde{X}w_N, \frac{b_n}{a_n} (I_m + \tilde{X}V_n\tilde{X}^T), 2a_N) $$

Here the preditive variance has 2 terms:

*  $\frac{b_n}{a_n} I_m$ this is the measurement noise
*  $\frac{b_n}{a_n} \tilde{X}V_n\tilde{X}^T$this is due the uncertainity in w, this term varies depending how far are we from the observed data. 

It is common to set $a_0 = b_0 = 0$ corresponding to an uninformative prior on $\sigma^2$, and set $w_0 = 0, V_0 = g(X^TX)^{-1}$ for any value of g. This is called **Zellner's g-prior**