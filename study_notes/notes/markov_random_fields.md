# Markov random field (MRF)

The are essentially [graphical models](graphical_models.md) where we do not define edge orientations. This is useful in cases when Conditional independence is not straight forward to define (Spatial models). 

## Formal Definition
A Markov random field is a probability distribution $p$ over variables $x_1, \cdots, x_n$ defined by an undirected graph G in which nodes correspond to variables $x_i$. 

$$
p(x_1, \cdots, x_n) = \frac{1}{Z} \prod_{c \in C} \phi_c(x_c) \\
Z = \sum_{x_1, \cdots, x_n}\prod_{c \in C} \phi_c(x_c)
$$

* C is the set of [cliques](graph_terminology.md) of G
* $\phi_c$ is the [potential function](markov_random_fields_potential_function.md)
* Z is the partition function (normalization constant)

This definition will satisfy [conditional independence properties of a graph G](markov_random_fields_hammersley_clifford.md).

## [Examples](markov_random_fields_examples.md)
* Ising model
* Hoppfiled model
* Pots model

## Learning
ML and MAP estimation on MRF is quite computationally expensive. For this reason it is rare to perform Bayesian inference for the parameters of MRF. They are done using gradient optimization algorithms.

## Statistical Physics
The [Gibs distribution](gibs_distribution.md) can convert it to an UGM:

$$
\psi_c(y_c|\theta) = \exp(-E[y_c|\theta_c])
$$

This forms the base of [energy based models](energy_based_models.md). Here high probability states correspond to low energy configurations.

## [Directed vs Undirected models](directed_vs_undirected_graphical_models.md)

## Bayesian Networks are special case of MRF
Bayesian networks are MRF where clique factor are conditional probability distributions, they imply directed acyclic structure in graphs

## [Factor graphs](factor_graph.md)
We can view MRFs in a way where factors and variables are explicit and separate in the representation. 