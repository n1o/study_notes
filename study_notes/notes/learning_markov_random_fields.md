# Learning Markov Random Fields

[Markov Random fields](markov_random_fields.md) are more expressive than [directed graphical models](directed_graphical_models.md), unfortunately this makes them harder to deal with.

Lets assume an MRF of the form:

$$
p(x_1, \cdots, x_n) = \frac{1}{Z(\varphi)} \prod_{c \in C} \phi_c(x_c; \varphi) \\
Z(\varphi) = \sum_{x_1, \cdots, x_n} \prod_{c \in C} \phi_c (x_c; \varphi)
$$

We can parametrize p as follows:

$$
p(x_1, \cdots, x_n) = \frac{1}{Z(\varphi)}\exp (\sum_{x \in C}\log \phi_c(x_c; \varphi)) \\
= \frac{1}{Z(\varphi)} \exp (\sum_{c \in C} \sum_{x_c'}1 \{ x_c' = x_c \} \log \phi_c(x_c'; \varphi)) \\
= \frac{\exp (\theta^T f(x))}{Z(\theta)}
$$

* $f(x)$ is a vector of indicator functions
* $\theta$ is the set of all the model parameters defined by $\log \phi_c(x'_c,\varphi)$
* $Z(\theta)$ is the partition function (differs for each set of parameters $\theta$). In Bayesian networks we have $Z(\theta) = 1$ for all $\theta$, in MRF we do not do this modelling assumptions, which makes it more flexible but harder to learn.

## Exponential families
The distribution:

$$
p(x;\theta) = \frac{\exp(\theta^T f(x))}{Z(\theta)}
$$

Is an example of [exponential families](exponential_family.md), which have the following properties:

* log-concave in their natural parameter $\theta$
* $f(x)$ is the vector of sufficient statistics, that fully describe the distribution p
* they make the fewest unnecessary assumptions about the data distribution.

## [Maximum likelihood learning](maximum_likelihood_markov_random_field.md)
Here we assume the following log likelihood:
$$
\frac{1}{|D|} \log p(D;\theta) = \frac{1}{|D|}\sum_{x \in D}\theta^T f(x) - \log Z(\theta)
$$

Unfortunately optimizing this objective is intractable, because the gradient is intractable.

## Approximate learning 

We can reduce maximum-likelihood learning to inference in a sense that we may repeatedly use inference to compute the gradient and determine the model weights using gradient descent. We can leverage this to perform approximate inference as:

* [Gibs sampling](gibs_sampling.md)
* [Persistent contrastive divergence](persistent_contrastive_divergence.md). Here after a step of gradient descent, the model will change only a little, thus we keep sampling from the same Gibbs sampler instead of a new one.

### Pseudo likelihood

We replace the likelihood 

$$
\frac{1}{D} \log p(D;\theta) =\frac{1}{|D|} \sum_{x \in D} \log p(x;\theta)
$$

with the following approximation:

$$
l_{\text{LP}} (\theta;D) = \frac{1}{|D|} \sum_{x \in D} \sum_{i} \log p(x_i|x_{N(i)};\theta)
$$

* $x_i$ is the ith variable in x
* $N(i)$ are the neighbors of i in the graph g (markov blanket of i)

Here $\log p(x_i|x_{N(i)};\theta)$ involves only one variable $x_i$ and the partition function is just a sum over all the values of one variable.

The pseudo-likelihood assumes that $x_i$ depends mainly on its neighbors in the graph, and ignores the dependencies on other, more distant, variables.

Pseudo-likelihood is concave and works well in practice (there are some exceptions)

## Moment matching
If we take the log-likelihood:

$$
\frac{1}{|D|} \log p(D;\theta) = \frac{1}{|D|}\sum_{x \in D}\theta^T f(x) - \log Z(\theta)
$$

If we differentiate it we get:

$$
\frac{1}{|D|} \sum_{x\in D} f(x) - E_{x \sim p}[f(x)]
$$

This is the difference between the expectation of natural parameters under the empirical distribution and the model distribution. Since $f$ in MRF is a vector of indicator functions for each variable of a clique one entry of $f = I[x_c - \bar{x}_c]$, the gradient is equal:

$$
\frac{1}{|D|} \sum_{x \in D} I[x_c = \bar{x}_c] - E_{x \sim p}[I[x_c = \bar{x}_c]]
$$

Thus by training MRF we force marginals to match the empirical marginals. This property is knows as moment matching. Since in maximum-likelihood we choose a distribution q to minimize the inclusive KL divergence $KL(p||q)$ across q in an exponential family, the minimizer $q^*$ will match the moments of the sufficient statistics to the corresponding moments of p. This is the reason why minimizing $KL(p||q)$ is called moment matching.

## [Learning in conditional random fields](learning_in_conditonal_radom_fields.md)

Here we extend learning to [conditional random fields](conditional_random_fields.md)