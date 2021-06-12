# Deep [Boltzman machines](boltzman_machines.md)

* entirely undirected with multiple layers of latent variables, each unit in a layer is independent conditioned on the variables in the neighboring layers
* the hidden units are typically binary but they can be continuous
* [energy based model](energy_based_models.md)
  $$
    p(v,h^{(1)}, h^{(2)}, h^{(3)}) = \frac{\frac{1}{Z}}{\exp \{ v, h^{(1)} , h^{(2)}, h^{(3)}\}} \\
    E(v,h^{(1)}, h^{(2)}, h^{(3)})
    $$
    * here we have 3 hidden layers 

![](../.images/machine_learning/deep_boltzman_machine.png)

* a DBM can be organized into a bipartite graph with odd layers on one side an even on the other:
  
![](../.images/machine_learning/dbm_biparite_graph.png)

  * this organization implies that the variables in the even layer, the variables in the odd become conditionally independent
  * the bipartite ordering implies that we can use the same equations for obtaining conditional as in [restricted boltzman machines](restricted_boltzman_machine.md)
  * we can use blocked Gibbs sampling to update all odd layers (including visible) in one block an the even in the second block

## Generating samples
* MCMC across all layers, with every layer of the model participating in every MC transition

## Inference
* the distribution over layer given the neighboring is factorial we can use mean field [VI](variational_inference.md)

$$
p(h^{(1)}, h^{(2)}, v) \approx Q(h^{(1)}, h^{(2)}|w) = \prod_j q(h_j^{(1)}|v)\prod_kq(h_k^{(2)}|v)
$$

## Layer wise Pre training
* training with stochastic [maximum likelihood](maximum_likelihood_learning.md) usually fails
* we train a RBM in isolation
  * the first layer is trained to model the input data
  * each later RBM is trained to model the previous RBM posterior distribution
  * combine at the end

## Jointly training

### Centered DBM
  * reparametrize the model in order to make the Hessian of the cost function to be better conditioned at the beginning
  * we can train the model without greedy pretraining
  * performance is worse than regular MLP

### Multi-prediciton DBM
* uses alternative training criterion to use back prop but avoid problems with MCMC estimate of the gradient
* this leads to superior classification performance but poor samples