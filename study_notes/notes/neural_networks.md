# Neural Networks

The key idea of deep learning is that takes an input x and apply an highly nonlinear (non convex) transformation to the data.

$$
y= \phi(x'\theta)^Tw
$$

* $\theta$ is the learned representation that best describes the data

## Learning in NN
Neural networks are nonconvex, finding an optimal value is nearly impossible, thus we find only an sufficiently low one.

The initial weights are initialized to a small random value, with the bias term either zero or an small random value.

In most cases our model defines an distribution 

$$
p(y|x;\theta)
$$

and we find its [MLE](maximum_likelihood_learning.md). Thus the cost function is defined as the cross entropy between the training data and the model predictions and a regularization term.

The shape of $p(y|x)$ is determined by the [output unit](output_units_neural_networks.md) (output layers) which in turn determines the actual loss function. We want this loss functions to have large gradients. If the gradient is small it cannot learn effectively, this happens when the [activation functions](activation_functions.md) saturate in [hidden](hidden_unit_neural_network.md) (or output units).

## Architecture
Architecture of a neural network is its structure, the number of units, what activations we use and how the units are connected.

Most NN are organized in groups as layers, layers organized in a chain structure, each layer being a function of layers that precede it.

$$
h^{(1)} = g^{(1)}(w^{(1)T}x + b^{(1)}) \\ 
h^{(2)} = g^{(2)}(w^{(1)T}h^{(1)} + b^{(2)} ) 
$$

In a chain structure we choose the number of layers and the width of each layer and the activation at each layer.

There are also architectures where we have connection that skip layers.
## [Feed forward networks](feed_forward_nn.md)
Also known as multilayered perceptron.

## [Computer Vision](neural_networks_computer_vision.md)
Overview some of the most popular architectures.