# Contractive [autoencoder](autoencoder.md) (CAE)

* autoencoder where we regularize the hidden code $h=f(x)$ encouraging the derivatives of $f$ to be as small as possible.

$$
\Omega(h) = \lambda ||\frac{\partial f(x)}{\partial x}||_f^2
$$

* the penalty is the squared Forbenius norm of the Jacobian matrix of partial derivatives of the encoder function
* we can connect it to the [denoising autoencoder](denoising_autoencoder.md), where we make the reconstruction error resists small but finite pertrubations of the input, while contractive autoencoders make the feature extraction function resist infinitesimal pertrubation of the input.

* CAE encourages to map neighborhoods of inputs to a smaller neighborhood of outputs (contract)
* Goal of CAE is to learn the [manifold structure](autoencoder_manifold.md) of the data, directions of $x$ the Jacobian of f is large, these directions are where $h$ rapidly changes,  and are the most likely approximations of the tangent planes of the manifold.
* Becomes expensive if the encoder becomes more deep, each layer has to be trained separately to be contractive.