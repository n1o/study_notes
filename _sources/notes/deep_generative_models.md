# Deep generative models

The form of a directed [latent-variable model](latent_variable_models.md) is:

$$
p(x,z) = p(x|z)p(z)
$$
* $x \in X$ are observed (possible continuous or discrete)
* $z \in R^d$ are latent


A deep generative model assumes that we have many hidden layers:

$$
p(x|z_1)p(z_1|z_2)p(z_2|z_3)\cdots p(z_{m-1}|z_{m})p(z_m)
$$

This allows us to learn hierarchies of latent observations.

## Learning deep generative models
Given a dataset $D=\{x^1, x^2, \cdots, x^n \}$ we are interested in:

* learn the parameters $\theta$ of p
* approximate posterior inference over z, given x (find latent factors)
* approximate marginal inference over x, given x with missing parts (perform fill in)

We make the following assumptions

* Intractability, computing the posterior $p(z|x)$ is intractable
* Big data, the size of dataset D is too large to fit in memory, thus we can only work with sub-samples of D

### Traditional approach
#### [EM](em_algorithm.md)
We cannot perform EM since
* the E step approximates the posterior $p(z|x)$ which is intractable
* the M step we learn $\theta$ by looking at the entire dataset which does not fit into the memory
#### [Mean-field](mean_field_method.md)
The time complexity of mean filed is exponential with the size of the markov blanket of the target variable. The markov blanked for z is complicated since it contains V structures, thus potentially we have to condition on all the z variables which is intractable.
#### [Sampling](markov_chain_monte_carlo_inference.md)
Sampling does not scale well.

### [Auto encoding variational bayes](auto_encoding_variatonal_bayes.md)
Allows us to perform inference and learning efficiently.