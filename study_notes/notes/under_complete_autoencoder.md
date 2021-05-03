# Under complete autoencoder

In [auto encoders](autoencoder.md) we want to avoid for the encoder decoder pair to learn the identity function. 

In under complete autoencoder we  constrain the hidden code $h$ to be lower dimensional than the input $x$. This forces the autoencoder to capture only the most salient features

## Loss function

$$
L(x, g(f(x)))
$$

* if $g$ is linear and L is MSE than $h$ spans the same subspace as PCA
* If $g$ and $f$ are nonlinear we have a more powerful model than PCA, but if the capacity is too large we may perfectly copy the data (we do not want)