# Conditional random fields (CRFs)

A **conditional random fields (CRF)** , sometimes called **discriminative random field**, is just a version of [MRF](markov_random_fields.md), where all the clique potentials are conditioned on the input feature:

$$
p(y|x) = \frac{1}{Z(x)} \prod_c\phi_c(y_c|x_c) \\
Z(x) = \sum_{y \in Y} \prod_c\phi_c(y_c|x_c)
$$

The partition constant depends on x, therefore we can say it is a function of x. We can say that conditional random fields instantiate a new Markov Random Field for each input x.

## Features
In general we assume that the potential functions are:

$$
\phi_c(x_c,y_c) = \exp(w_c^Tf_c(x_c,y_c))
$$
* $f_c(x_c,y_c)$ describes the compatibility between $x_c$ and $y_c$

Here $x$ can be arbitrary complex, since it is always observed it does not affect computation.
This can be generalized, for an example we model $p(x,y)$ using an MRF, we fit two distribution to the data $p(y|x)$ and $p(x)$. But if we are interested only in predicting y given x, we can skip modeling $p(x)$ (we may not have enough data to fit booth). THis can speed up computation.
## Chain CRF
If we assume that $p(y|x)$ is a chain CRF, with two types of factors, (an example image factors) $\phi(x_i|y_i)$ for $i=1,\cdots, n$, which assigns higher values to $y_i$ which are consistent with input $x_i$, and pairwise factors $\phi(y_i, y_{i+1})$ for $i=1,\cdots,n-1$. 

We can view $\phi(x_i|y_i)$ as probabilities $p(y_i|x_i)$ and $\phi(y_i|y_{i+1})$ are some co-occurrences.
