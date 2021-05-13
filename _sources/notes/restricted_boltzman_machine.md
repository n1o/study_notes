# Restricted Boltzman Machine

* [deep learning model](neural_networks.md) that is also an [undirected graphical model](markov_random_fields.md).
* single layer [latent variable model](latent_variable_models.md)
* [energy based model](energy_based_models.md) with a single visible and hidden unit
    $$
    E(U,V) = -b^Tv - c^Th - v^TWv
    $$
    * $b,c,w$ are unconstrained learned real values

* the model is divided int two groups, $h$ (hidden) and $v$ (visible) units and the interactions between them is defined by a matrix $W$

![](../.images/machine_learning/restricted_boltzman_machine.png)
  * There are not interactions between visible or hidden units (Hense the name restricted)

## Conditional distributions

$$
p(h|v) = \prod_i p(h_i|v) \\
p(v|) = \prod_i p(v_i|h) 
$$

* the individual conditionals are:
    $$
    p(h_i = 1|v) = \sigma(v^TW_{:,i} + c_i) \\
    p(h_i = 0|v) = 1 - p(h_i = 1|v)
    $$

## Learning
* we can use block Gibbs sampling alternating between sampling all of the hidden units $h$ and sampling all of the visible units $v$ 
* the derivative of the energy function is 
  $$ \frac{\partial}{\partial w_{i,j}} E[v,h] = -v_ih_j$$