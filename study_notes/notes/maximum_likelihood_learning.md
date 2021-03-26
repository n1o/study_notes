# Maximum Likelihood Learning (Estimation)

Lets assume that we want to learn the full probability distribution, so we can answer any probabilistic inference query we want. This can be viewed as density estimation, where we want to construct a distribution $p$ as close to the true distribution $p^*$. This closeness can be evaluated as:

$$
KL(p^*||p) = \sum_x p^*(x) \log \frac{p^*(x)}{p(x)} = -H(p^*) - E_{x \sim p^*}[\log p(x)]
$$

We can simplify since $H(p^*)$ is independent of p, thus minimizing KL divergence is the same as maximizing the expected log-likelihood:

$$
E_{x \sim p^*}[\log p(x)]
$$

Here we want to find $p$ that assigns high probability to instances sampled from $p^*$. (We do not compute $H(p)$ thus we do not know how far from optimum we are). The equation above is also the equation for cross entropy. Thus we can view this as minimizing the cross entropy between the model distribution and the data distribution.

In general we do not know $p^*$, thus we approximate the expected log likelihood with the empirical log-likelihood (MC estimate):

$$
E_{x\sim p^*}[\log p(x)] \approx \frac{1}{|D|} \sum_{x \in D}\log p(x)
$$

* $D$ is a dataset drawn i.i.d from $p^*$

The maximum likelihood learning is to estimate:

$$
\max_{p \in M} \frac{1}{|D|} \sum_{x \in D} \log p(x)
$$

* $M$ is a set of possible models we compare

We can [prove](mle_kl_divergence_proof.md) the statement above using the empirical distribution.

## Loss function
A loss function generalizes the concept of maximum likelihood learning. A loss function $L(x,p)$ measures the loss that a model distribution p makes on a particular instance x. Thus our goal is to find the model that minimizes the expected loss.

$$
E_{x \tilde p^*} [L(x,p)] \approx \frac{1}{|D|} \sum_{x\in D}L(x,p) 
$$

>The log loss function corresponds to the maximum likelihood estimation

## Empirical Risk and Overfitting
Empirical risk minimization can easily overfit, since we observe only a fraction of the data not the whole data generative process. Thus our model will not generalize. For choosing a good model it is important to take [bias-variance tradeoff](bias_variance_tradeoff.md) into account.

Here we may ask how to avoid overfitting (having high variance). A good an efficient way is to introduce a regularizer term $R(p)$ to the loss function $L(x,p)$ which will penalize complex p.

### Generalization error

If we train we minimize:

$$
\max_{p \in M} \frac{1}{|D|} \sum_{x \in D} \log p(x)
$$

However, we are interested in minimizing:

$$
E_{x \sim p^*}[\log p(x)]
$$

Thus we cannot guarantee the quality of our model. Since D is just an sample from the true model, and we might get unlucky.


## Relationship to cross entropy
If we minimize an negative log likelihood function it is the same as minimizing the cross entropy between the empirical distribution and the distribution defined by the model. 

An example is minimizing the mean squared error, this is the same as minimizing the cross entropy between the empirical distribution and a Gaussian model. Where we try to match the model distribution to the empirical distribution of the data $\hat{p}_{\text{data}}$


## Properties

As the number of training samples approaches $\infty$ the MLE estimate of a parameter converges to the true value of the parameter. For this to happen the following conditions has to be met.

* the true distribution $p_{\text{data}}$ must lie within the model family $p_{\text{model}}(.,\theta)$ otherwise no estimator can recover $p_{\text{data}}$
* the true distribution $p_{\text{data}}$ must correspond to exactly one value of $\theta$ otherwise the MLE can recover the correct $p_{\text{data}}$ but we cannot recover the true value of $\theta$