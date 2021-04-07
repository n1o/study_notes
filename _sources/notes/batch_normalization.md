# Batch Normalization

Batch normalization is not a optimization scheme, but an adaptive reparametrization trick used in [neural networks](neural_networks.md). If we train a neural network we update each layer assuming that the other layers do not change, however this is not true and unexpected things might happen. 

Let H be a minibatch of activations of the layer to normalize, arranged as a design matrix with activations for each example appearing in a row of the matrix. We replace H by:

$$
H' = \frac{H - \mu}{\sigma} \\ H_j = \frac{H_{ij} - \mu_j}{\sigma_j}
$$

* $\mu$ is the mean of each unit
* $\sigma$ is the standard deviation of each unit

If we perform gradient descent on the transformed data, gradient will never propose a transformation that increases the mean or standard deviation of a hidden layer.

Batch normalization leads to reduced expressiveness of the network at a given unit. To maintain the expressiveness it is common to replace the batch of hidden units by:

$$
\gamma H' + \beta
$$

* $\gamma, \beta$ are learned parameters allowing the layer to have a mean and standard deviations

This improves the expressiveness while retaining good learning dynamics. If we put it inside a layer of NN we get:

$$
\phi(BN(XW + b)) \\ 
BN(H) = \gamma \odot \frac{H - \mu}{\sigma} + \beta
$$

* $\phi$ is the activation function of a layer
* $XW+b$ is our mini-batch H
## Test time
During test time we replace $\mu$ and $\sigma$ by a running average collected during training.