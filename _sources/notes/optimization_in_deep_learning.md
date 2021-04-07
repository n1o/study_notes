# Optimization in deep learning

Most optimization techniques stop when some criteria is met, not when a local minima is found. In machine learning we want to optimize some performance metric P, which in many cases is not tractable, instead we optimize a loss function $J(\theta)$ that we optimize while hopping we also improve P.

$$
J(\theta) = E_{(x,y) \sim \tilde{p}_{\text{data}}} L(f(x;\theta), y)
$$

* $\tilde{p}_{\text{data}}$  is the empirical distribution

We would prefer to optimize:

$$
J^*(\theta) = E_{(x,y) \sim p_{\text{data}}} L(f(x;\theta), y)
$$

* $p_{\text{data}}$ is the data generating distribution

In most cases the data is too large thus we have to evaluate [subsamples (mini batch)](batch_minibatch_aglorithms.md) of the data.

## Challenges in optimizing Neural Networks

### Ill-conditioning

Ill conditioning will cause [SGD](gradient_descent.md) to get stuck (even small step wont lead to improvement). Gradient descent step of $-\epsilon g$ will introduces an error to the loss function:

$$
\frac{1}{2}\epsilon g^THg - \epsilon g^Tg
$$

The gradient is ill conditioned if 

$$\frac{1}{2}\epsilon g^THg > \epsilon g^Tg $$

To determine ill conditioning we can monitor $g^Tg$ and $g^THg$. If $g^Tg$ does not shrink but $g^THg$ grows by an order of magnitude we mut decrease the learning rate to compensate for the strong curvature.

### Local minima
Neural networks have many local minima, since in most cases the model is [non identifiable](non_identifiable_models.md). In a NN we can swap in a layer the incoming weight vector of unit i with the incoming weight vector of unit j and the same for the outgoing weights and have the same model. Thus for a neural network with m layers and n units there are $n!^m$ possible rearrangements.

### Saddle point

Hessian has mixed sign eigenvalues. Points lying along eigen vectors associated with positive eigen values have greater cost than the saddle point, while points associated with negative eigen values have lower cost. In high dimensions it is more likely that we have a saddle point than a local minima. Newtons method is especially sensitive to saddle points.

### Vanishing gradient
If we repeatedly multiply by a matrix W,like in [recurrent neural networks](recurrent_neural_networks.md) after n steps we get:

$$
W^t = V\text{diag}(\lambda)^t V^{-1}
$$

Thus we power up the eigen values. If they are close to 1 it should be fine, otherwise they explode or vanish. If they vanish gradient has no information how to steer learning, and if they explode learning becomes unstable.

## Parameter initialization
[Parameter initialization](neural_networks_parameter_initialization.md) plays an important role in optimizing a neural network.

## Batch normalization

Training neural networks is tricky, since gradient descent update assumes that weights that are not updated are fixed. But this is not true. To mitigate this we introduce [batch normalziation](batch_normalization.md).