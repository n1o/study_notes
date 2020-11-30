# Beta binomial model
A sequence of coinflips from which we try to infer the probability of heads can be viewed as an analogy to the beta binomial model.

## Likelihood

The full probability of observing an given sequence of coin flips is:

$$Bin(k|n,\theta) \triangleq \binom{n}{k} \theta^k (1-\theta)^{n-k}$$

Here we observe $k$ heads in $n$ flips. In general we do not care about the exact order thus we can ommit $\binom{n}{k}$ thus we can simply it to:

$$P(D|\theta) \propto \theta^{N_1}(1-\theta)^{N_0}$$

* $N_1$ - number of heads
* $N_0$ - number of tails

## Prior

The [Beta](./beta_distribution.md) distribution has support over the interval [0,1] and is proportional to the likelihood:

$$Beta(\theta| a,b) \propto \theta^{a - 1} (1 - \theta^{b - 1}) $$

The full distribution is:

$$Beta(\theta| a,b) \triangleq \frac{1}{B(a,b)} \theta^{a - 1} (1 - \theta^{b - 1}) $$

* $\frac{1}{B(a,b)}$ where $B(a,b)$   

## Posterior

$$
P(\theta| D) = P(D| \theta) P(\theta)  \\
P(\theta| D) \propto Bin(N_1| \theta, N_0 + N_1) Beta(\theta| a,b) \\
P(\theta| D) \propto Beta(\theta| N_1 + a, N_0 + b) \\
P(\theta|D) \propto \theta^{N_1}(1-\theta)^{N_0} \theta^{a - 1}(1-\theta)^{b -1} = \theta^{N_1 + a - 1}(1 - \theta)^{N_0 + b - 1} \\

p(\theta|D) = \binom{N_1 + N_0}{N_1}\frac{1}{B(a,b)} \theta^{N_1 + a - 1}(1 - \theta)^{N_0 + b - 1}
$$

The posterior is just a compromise between the prior and the empirical parameters. With $a$ and $b$ being hyper parameters controlling the strength of the prior. 

### Evidence
$$P(D) = \binom{N}{N_1}\frac{1}{B(a,b)}$$
Is the normalization constant.

## Posterior Mode

The mode is the mode of a Beta distribution

$$\hat{\theta}_{MAP} = \frac{a + N_1 - 1}{a + b + N  -2} $$


If we use an uniform prior ($Beta(1,1)$) than the MAP estimate is the same as MLE estimate. 

$$\hat{\theta} = \frac{N_1}{N} $$

Which is just the empirical fraction of heads.

Where the posterior mean is:

$$\bar{\theta} = \frac{a + N_1}{a + b + N} $$

and it can be expressed as a convex combination of the prior mean and the MLE. This captures the intuition that the posterior is a compromise between what we believe and what the data is telling us.

If we let:

$\alpha_0 = a + b$ which is the sample size of the prior, and control its strength. And let the prior mean be $m_1 = \alpha / \alpha_0$ then:

$$E[\theta|D] = \frac{\alpha m_1 + N}{N + \alpha_0} = \frac{\alpha_0}{N + \alpha_0}m_1 + \frac{N}{N + \alpha_0} \frac{N_1}{N}  = \lambda m_1 + (1-\lambda)\hat{\theta}_{MLE}$$

where:
* $\lambda = \frac{\alpha_0}{N + \alpha_0}$ is the ration of prior to posterior sample size. So the weaker the prior the smaller this ration is. Hence the estimation is closer to MLE.

## Posterior Variance
These are point estimates but they still gives us a sence how much we can trust our posterior distribution.

$$ var[\theta|D] = \frac{(a + N_1)(b + N_0)}{(a + N_1 + b + N_0)^2 (a + N_1 + b + N_0 + 1)}$$

or if $N >> a,b$ we can simply it to:

$$var[\theta|D] \approx \frac{N_1 N_0}{N N N} = \frac{\hat{\theta} ( 1- \hat{\theta}) }{N} $$

Where:

* $\bar{\theta}$ is the MLE. 

Now we can calculate the error bars, we can just take the sqare root of the variance.

## Predicting the outcome of a single event

Now we have a posterior that is essentially a beta distribution. Now we want to infer the probability of heads in a single trial.

$$p(\tilde{x} = 1|D) = \int_0^1 p(x = 1| \theta)p(\theta|D) d\theta $$

$$= \int_0^1 \theta Beta(\theta| a,b)d\theta = E[\theta|D] = \frac{a}{a+b} $$

Hence it is equal to:

$$ p(\tilde{x} |D) = Ber(\tilde{x}| E[\theta|D])$$

## Predicting the outcome of multiple events
We want to predict x heads in M future trials this is given by:

$$ p(x|D,M) = \int_0^1 Bin(x|\theta, M) Beta(\theta| a,b) d\theta $$

$$ = \binom{M}{x}\frac{1}{B(a,b)} \int_{0}^1 \theta^x (1-\theta)^{M - x } \theta^{a -1} (1-\theta)^{b - 1}$$

Where the Integral is just the Normalization constant for $Beta(a+x , M -x + b)$

Nw the posterior predictive distribution is known as the (combound) **beta-binomial** distribution:

$$Bd (x|a,b,M) \triangleq \binom{M}{x} \frac{B(x+ a, M - x + b)}{B(a,b)} $$

Here the distribution has the following mean and variance:

$$E[X] = M \frac{a}{a+b} $$

$$var[x] = \frac{Mab}{(a+b)^2}\frac{(a + b + M)}{a + b + 1}$$

Here if we set $M=1$ we get the same thing as the predicions for a single variable.
