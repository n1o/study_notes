# Representation learning

* any [feed forward nn](feed_forward_nn.md) can be viewed as representation learning, [hidden layers](hidden_unit_neural_network.md) learn representation for the output layer to best accomplish its task
* representation learning is an tradeoff between preserving as much information about the input and attaining nice properties

## [Greedy unsupervised pretraining](greedy_unsupervised_pretraining.md)

We perform unsupervised pre-training on each layer on the NN separately. An example we train the first layer unsupervised, when we ad the new layer we do not update the previous layers weights anymore. After the pre-training is done we than train the whole neural network with respect to the objective function.

This approach lost its popularity but it is still used in NLP (word embedding)

## [Transfer learning, Domain adaptation](transfer_learning.md)

In transfer learning we  adapt an network that was learned to perform well in task P1 to perform well in task P2.

## [Semi-Supervised Disentangling of causal factors](semi_supervised_disentangling_of_causal_factors.md)

