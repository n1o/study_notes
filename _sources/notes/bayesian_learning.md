# Bayesian Learning

Lets compare Bayesian Learning to [maximum likelihood learning](maximum_likelihood_learning.md).

Lets assume the following example:

We model the outcome of a biased coin $X = \{\text{heads}, \text{tails} \}$.

1. We tos the coin 10 times and we observe 6 heads. The MLE estimate of the probability of observing heads is:

$$
\theta_{\text{MLE}} = \frac{\#\text{heads} }{\#\text{heads} + \#\text{tails}} = \frac{6}{10} = 0.6
$$

2. We toss the coin 100 times and we observe 60 heads. The MLE estimate is the same as before:

$$
\theta_{\text{MLE}} = \frac{60}{100} = 0.6
$$

Thus we have tossed the coin 100 times but our confidence is the same.

## Bayesian learning setup
In Bayesian learning we explicitly model the uncertainty over booth X ans $\theta$, thus we model booth as random variables. 

In bayesian learning we define a prior distribution $p(\theta)$ that encodes our initial belief. (Subjective belief). And we update our belief based on the observed data.

$$
p(\theta|D) = \frac{p(D|\theta)p(\theta)}{p(D)} \propto p(D|\theta) p(\theta) \\ 
\text{posterior} \propto \text{likelihood} \times \text{prior}
$$

Thus we can incorporate prior knowledge in our models.