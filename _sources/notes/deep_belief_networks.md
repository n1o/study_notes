# Deep belief networks
* deep generative model that has several layers of binary latent variables 
* every unit is connected to every unit in the neighboring layer
* the top two layers have undirected connections, the rest is connected pointing to the layer closer to the data


![](../.images/machine_learning/deep_belief_networks.png)

## Sampling
* use [Gibbs](gibs_sampling.md) to sample from the top two layers, ancestral sampling downwards

## Inference

* intractable, maximizing [ELBO](evidence_lower_bound.md) is intractable since the maximal clique is of the size of the network


## Training

* we train a series of [RMBs](restricted_boltzman_machine.md) each greedily trained started on top of each other