# Sparse autoencoder

It is an example of [regularized autoencoder](autoencoder.md) where the hidden code $h$ is larger than the input $x$. Normally this would result in an overcomplete autoencoder. 

To avoid overfitting we introduce a sparsity penalty $\Omega(h)$ to the loss function:

$$
L(x,g(f(x))) + \Omega(h)
$$
* $g$ decoder
* $f$ encoder
* $h$ hidden state

Sparsity forces learning unique statistical features of the data