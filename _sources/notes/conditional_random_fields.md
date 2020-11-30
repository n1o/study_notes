# Conditional random fields (CRFs)

A **conditional random fiels (CRF)** , sometimes called **discriminative random field**, is just a version of MRF, where all the clique potentials are conditioned on the input feature:

$$
p(y|x,w) = \frac{1}{Z(x,w)} \prod_c\psi_c(y_c|x,w)
$$

A CRF can be thought as a strucutred output extension of logistic regression, where we model the correlation amongs the ouput labels conditioned on the input features. We usually assume a log-linear representation of the potentials:

$$
\psi_c(y_c|x,w) = \exp(w_c^T\phi(x, y_c))
$$

* $\phi(x| y_c)$ is a feature vector dervied from the lobal inputs x and the local set of labels $y_c$

This is just an discriminative version of a [markov random field](markov_random_fields.md).
