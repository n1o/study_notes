# Mixture density networks

It is a [neural network](neural_networks.md) whose output is a mixture of [Gaussians](gaussian_distribution.md).

$$
p(y|x) = \sum_{i=1}^n p(c=i|x)N(y_i; \mu^{(i)}, \Sigma^{(i)(x)})
$$

* $p(c=i|x)$ is the mixture prior, obtainable using softmax 
* $\mu^{(i)}$ is the center of the ith component, if y is d dimensional an NN must produce a $n$ d dimensional vectors.
* $\Sigma^{(i)(x)}$ it is the covariance matrix in general it is chosen to be diagonal