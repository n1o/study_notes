# Hidden units in neural networks
In [neural networks](neural_networks.md) the output of hidden units is not defined by the data. 

Hidden are not required to be differentiable everywhere since in most [neural networks](neural_networks.md) no not arrive to a gradient which is zero, however they are not differentiable only at a small number of points.

The general description of a hidden unit is:

$$
g(W^Tx + b)
$$

* $g$ is the [activation function](activation_functions.md) that is desired to be nonlinear, the input is an [affine transformation](affine_function.md) of the input (the input can be the output of an previous hidden unit)

## [RELU hidden units](rectified_hidden_unit.md)
Rectified linear unit are close to linear and are easy to optimize.

## Sigmoid 
$$
g(z) = \sigma(z)
$$

[Sigmoid units](sigmoid_and_soft_plus.md) saturate when z is very positive or negative, they work well only if z is close to 0. Because of this sigmoid activations are not used inside hidden units. 

## Hyperbolic tangent

They closely resemble the identity function when close to 0, and are frequently used in hidden units.

$$
g(z)  = \tanh(z)
$$

Relationship to sigmoid unit
$$
\tanh(z) = 2 \sigma(2z) -1
$$

## Radial basis functions (RBF)

$$
h_i = \exp(-\frac{1}{\sigma^2_i} || W_{:,i} - x||^2 )
$$

This becomes more active as x approaches a template $W_{:,i}$. It is hard to optimize since it saturates to 0 for most x.

## [Softplus](sigmoid_and_soft_plus.md)

This is not advised to use in hidden units.
$$
g(a) = \log ( 1 + e^a)
$$

## Hard Tanh

$$
g(a) = \max(-1, \min(1,a))
$$
