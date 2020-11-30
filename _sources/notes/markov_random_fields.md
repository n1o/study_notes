# Markov random fileds (Undirected graphical models (UGM))

The are esentially graphical models where we do not define edge orientations. This is useful since sometimes defining conditional independence between nodes is not straight forward. 

The main advantages of UGMs over DGMs are:

1. They are symmetric and therefore more “natural” for certain domains, such as spatial or relational data
2. Discriminativel UGMs (aka conditional random fields, or CRFs), which define conditional densities of the form $p(y|x)$, work better than discriminative DGMs,

The main disadvantages of UGMs compared to DGMs are

1. The [parameters are less interpretable](markov_random_fields_parametrization.md) and less modular.
2. Parameter estimation is computationally more expensive.

# [Examples](markov_random_fields_examples.md)
* Ising model
* Hoppfiled model
* Pots model

# Learning
ML and MAP estimation on MRF is quite computationaly expensive. For this reason it is rare to perform Bayeisan inference for the parameters of MRF.

They are done using gradient optimization algorithms.