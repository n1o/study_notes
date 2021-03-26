# Output units in neural networks

The last layer unit of a [neural network](neural_networks.md). And they determine the form of the cross entropy (loss) function.

## Linear units for Gaussian distribution

[Affine transformation](affine_function.md) with no nonlinearity
  

$$
\hat{y} = w^Th + b
$$

* $h$ is the output of an previous hidden unit

Can be used to produce the mean of a conditional [Gaussian](gaussian_distribution.md)

$$
p(y|x) = N(y; \hat{y}, I)
$$

## Sigmoid Unit for Bernoulli output 
Used for binary classification

$$
p(y|x) = Bernoulli(y; \hat{y}) \\ 
\hat{y} = \sigma(w^Th + b)
$$

* $\sigma$ is the [sigmoid function](sigmoid_and_soft_plus.md)

## Softmax unit for multinomial
If the output distribution consists of n possible values we can use the [softmax function](softmax_function.md)

$$
\text{softmax}(z)_i = \frac{\exp(z_i)}{\sum_j \exp(z_j)} \\ 
\log \text{softmax}(z)_i = z_i - \log \sum_j \exp(z_j)
$$

Thus we pass a linear function $z = W^Th + b$ trough a softmax function. The softmax function directly penalizes the most active incorrect prediction. If the answer at the largest of the softmax is correct than $-z_i$ and $\log \sum_j \exp (z_j)$ roughly cancel. Tus it will contribute only little to the overall training loss, the cost is dominated by examples are not correctly classified.

## [Mixture density networks](mixture_density_networks.md)
The output of a NN is a mixture of Gaussians.