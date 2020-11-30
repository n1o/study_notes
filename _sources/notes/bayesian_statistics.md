----
source:
- Machine Learning An Probabilistic Perspective
----

# Bayesian Statistics

The main goal of Bayesian statistics is finding the [posterior distribution](posterior_distribution.md). That is the distribution of parameteres of interest given the data.

$$
p(\theta|D)
$$

To find this distribution we must make an couple of assumptions.

1. We describe the data given the parameters $p(D|\theta)$ this is commonly known as *likelihood*
2. Express our belief about the paremters $p(\theta)$ his is known as *prior*

Together this forms the following [equation](bayes_rule.md):

$$
p(\theta|D) \propto p(D|\theta) p(\theta) \\

p(\theta|D) =  \frac{p(D|\theta)p(\theta)}{p(D)}
$$


The later equation contains an aditional term:

$$p(D) = \int_{\theta} p(D|\theta)p(\theta)$$

This is aloso called the [**evidence**](computing_evidence.md) and it is what makes Bayesian statistics hard! Since calculating the integral is notrivial.

# Finding the posterior distribution (Inference)
There are multiple approaches how to find $p(\theta|D)$ depending if we want an exact or approximate solution:

## Analytical solution using conjugate priors

Computing $p(\theta|D)$ can be nontrivial, but for some cases it can be achieved analyticaly. We require that we choose an [conjugate priors](conjugate_prior.md) to an likelihood.

## Markov chain monte carlo
//TODO MCMC
## Variational approximation (Inference)
//TODO VI
# Model averaging
//TODO Model averagings

# Model selection
Sometimes we need to choose the [best model](bayesian_model_selection.md)

# Posterior predictive distribution

The posterior is our belief about the world. We can test if our belief is justified if it manages to predict observed quantities. By drawing from the posterior we get the [posterior predicitve distribution](posterior_predictive_distribution.md)
