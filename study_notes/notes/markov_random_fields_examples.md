# Markov Random Fields example
## Ising model

The Ising model is an example of an MRF that arose from statistical physics. It was originally used for modeling the behavior of magnets. In particular, let $y_s \in \{-1, +1 \}$ represent the spin of an atom, which can either be spin down or up. In some magnets, called ferro-magnets, neighboring spins tend to line up in the same direction, whereas in other kinds of magnets, called anti-ferromagnets, the spins “want” to be different from their neighbors.

We can model this as an MRF. We create a graph in the form of a 2D or 3D lattice and connect neighboring variables. Then we define the following pariwise clique potential:

$$
 \psi_{st}(y_s, y_t) = \begin{pmatrix}
     e^{w_{st}} & e^{-w_{st}} \\ e^{-w_{st}} &  e^{w_{st}}
 \end{pmatrix}
$$
* $w_{st}$ is the strength between nodes s and t. If two notes of a graph are not connected, then we set it to 0.

Here the weight matrix $W$ is symmetric, and we ofthen assume that all the edges have strength J. 

If all the weights are positive, $J > 0$, then neighboring spins are likely to be in the same state; this can be used to model ferromagnets, and is an example of an associative Markov network. If the weights are sufficiently strong, the corresponding probability distribution will have two modes, corresponding to the all $+1$ state and the all $-1$ state. These are called the ground states of the system.

If all of the weights are negative, $J < 0$, then the spins want to be different from their neighbors; this can be used to model an anti-ferromagnet, and results in a frustrated system, in which not all the constraints can be satisfied at the same time. The corresponding probability distribution will have multiple modes. Interestingly, computing the partition function $Z(J)$ can be done in polynomial time for associative Markov networks, but is NP-hard in general. 

## Hopfield networks

A Hopfield network is a fully connected Ising model with a symmetric weight matrix, $W = W^T$ . These weights, plus the bias terms $b$, can be learned from training data using (approximate) maximum likelihood. 

The main application of Hopfield networks is as an associative memory or content addressable memory. The idea is this: suppose we train on a set of fully observed bit vectors, corresponding to patterns we want to memorize. Then, at test time, we present a partial pattern to the network. We would like to **estimate the missing variables**; this is called **pattern completion**. 

They also can be interpreted as **recurrent neural networks**. 

A **Boltzmann machine** generalizes the Hopfield / Ising model by including some hidden nodes, which makes the model representationally more powerful. Inference in such models often uses Gibbs sampling, which is a stochastic version of ICM.

## Potts model

It generalize Ising model into multiple discrete states. 

