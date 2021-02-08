# Mean filed method

One of the most popular variational inference methods. It assumes that the posterior is fully factorized approximation of the form:

$$q(x) = \prod_{i=1} ^D q_i(x)$$

Our goal is to solve this optimization problem:

$$min_{q_1, \cdots, q_D } KL(q||p) $$

Here we optimize over the parameters of each marginal distribution $q_i$. This can be solved using [coordinate descent method](coordinate_descent.md) over $q_j$, where we iterate over $j=1,2,\cdots, n$ and for each $j$ we optimize $KL(q||p)$ over $q_j$ while keeping the other "coordinates" $q_{-j} = \prod_{j\ne i} q_i$ fixed. The optimization for one coordinate has the following form:

$$ \log q_j(x_j) = E_{-q_j}[\log \tilde{p}(x)] + \text{const} ​$$ 

* $\tilde{p}(x) = p(x,D)$ is the unnormalized posterior 
* $E_{-q_j} [f(x)]$ is a notation that we take expectation over $f(x)$, with respect all the variables except $x_j$ 
* Here at each update step we replace the neighboring values by their mean value, hence the name mean field.
* $\text{const}$ is a normalization constant for the new distribution.

For example if we have 3 variables:
$$
E_{-q_2}[f(x)] = \sum_{x_1}\sum_{x_2}q(x_1)q_3(x_3)f(x_1, x_2, x_3)
$$

When we update $q_j$ we only need to reason about the variables which share a factor with $x_j$ (its markov blanket), the other terms get absorbed into the constant term.

Mean field method can be used to infer discrete or continuous latent quantities, using variety of parametric forms for $q_i$. 

In the end factors $q_j(x_j)$ are not quite equal to the true marginals $p_q(x_j)$ but are often good enough for practical purposes.

## Derivation of the mean filed update equation
//TODO prove this

## Structured mean field

Assuming that all the variables are independent in the posterior is a very strong assumption that can lead to poor results. Sometimes we can exploit **tractable substructures** in our problem, that we can efficiently handle some kind of dependencies. This is called **strucutred mean field** approach. This approach is the same as before, except we group sets of variables together and we update them simultaneously. (We treat all the variables of a group as a single "mega variable"). 

Examples:

* Factorial HMM
