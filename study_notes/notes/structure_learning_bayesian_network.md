# Structure learning
We try to learn the directed acyclic graph of a [bayesian network](directed_graphical_models.md).

## Score-based approach

We start by defining a criterion to evaluate how well the Bayesian network fits the data, than search over the space of DAGs for a structure with maximal score. This turn into a search problem consisting of two parts.

### Score metrics
Score metrics for a structure G and data D is defined as:

$$
\text{Score}(G:D) = LL(G:D) = \phi(|D|)||G||
$$

* LL(G:D) is the log-likelihood of the data under the graph structure G
* $|D|$ is the number of samples
* $||G||$ is the number of parameters in graph G this penalizes overcomplicated graph structures to avoid overfitting
* $\phi(t)$ is the penalty
  * $\phi(t) = 1$ is either AIC or 
  * $\phi(t) = \frac{\log(t)}{2}$ for BIC, here the influence of model complexity increases as M grows, allowing the log-likelihood term to dominate the score.


#### Bayesian Dirichlet score
Special family of score functions, it defines the probability of data D conditional on the graph structure G:

$$
p(D|G) = \int P(D|G,\Theta_G)P(\Theta_G|G)d\Theta_G
$$

* $P(D|G,\Theta_G)$ is the probability of the data given the network structure and parameters
* $P(\Theta_G|G)$ is the prior for the parameters

This Prior is defined as a [Dirichlet distribution](dirichlet_distribution.md):

$$
P(D|\Theta_G) = \prod_o \prod_{\pi_i} [\frac{\Gamma(\sum_j N'_{i, \pi_i, j})}{\Gamma (\sum_j N_{i, \pi_i,j}') + N_{i, \pi_i, j}}  \prod_j \frac{\Gamma(N'_{i,\pi_i, j} + N_{i, \pi_i, j})}{\Gamma (N'_{i,\pi_i, j})}]
$$

* $\pi_i$ is the parent configuration of variable i
* $N_{i,\pi_i, j}$ is the number of variable i taking value j with parent configuration $\pi_i$
* $N'$ represents the counts in the prior

Since BD integrates over the space we do not need an explicit penalty term.

With a prior structure $P(\Theta_G)$ the BD score is defined as:

$$
\log P(D|\Theta_g) + \log P(\theta_G)
$$

#### [Chow-Liu Algorithm](chow_liu_algorithm.md)
The Chow-Liu algorithm finds the maximum-likelihood tree structure where each node has at most one parent.

### Search algorithms
Approaches listed below are tractable, but provide no guarantee of the quality of the graph.

#### Local Search
We start with an empty graph. At each step we try to change the graph structure by a single operation of adding an edge, removing an edge or reversing an edge, while preserving acyclic property. If we increase the score than we adopt the change otherwise we make an another attempt.

#### Greedy Search (K3 algorithm)
We assume a topological ordering for the graph. For each variable we restrict its parent set to the variable with a higher order. While searching for parent set for each variable, it takes a greedy approach by adding the parent that increases the score most until no improvement can be made.

