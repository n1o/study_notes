# Learning manifolds with autoencoders

* learning autoencoders can be viewed as learning the structure of a manifold

A manifold can be characterized by it set of tangent planes. At a point $x$ on a d-dim manifold, the tangent plane is given by d-basis vectors that span the local directions of variations allowed on the manifold.


> ![](../.images/machine_learning/autoencoder_manifold_mnist.png)
> These local directions specify how we can change x infinitisemaly while staying on the manifold.

Training an autoencoder involves:

1. Learning an representation $h$ of the training data x, where x can be approximately recovered using $h$ and a decoder. We re not required to reconstruct inputs that are not possible under the data-generating distribution

2. Satisfying constraints or regularization, this limits the capacity an results in solution that are less sensitive to the input.

If we combine the booth approaches we are able to capture information about the data generating distribution. We capture only the variance required to reconstruct the training data. The encoder learns mapping from the input space x, to a representation space, this mapping is sensitive to changes along the manifold, but not sensitive to changes orthogonal to the manifold.