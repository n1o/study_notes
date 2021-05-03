# Autoencoders

* neural network that attempts to copy its input to its output. 
* internally it has a hidden layer $h$, that describe the **code** that represents the input

>It contains two parts:
>1. Encoder $h = f(x)$
>2. Decoder $r = g(h)$
>
>![](../.images/machine_learning/autoencoder_basic.png)
>
> The idea is to learn $g(f(x)) \approx x$, where we do not reconstruct the input perfectly. This forces to learn aspects of the data that are most important.


* we can connect autoencoders to [latent variable models](latent_variable_models.md)
* encoder and decoder can be an neural network.

## [Under-complete autoencoders](under_complete_autoencoder.md)
We want the decoder encoder pair not to learn the identity function: $g(f(x)) \ne I(x)$. In the undercomplete autoencoder this is achieved by constraining the hidden code to be lower dimensional than the input. 

## Regularized autoencoder

We allow large hidden code $h$ but we add some penalty to avoid overfitting.

## [Stochastic Autoencoder](stochastic_autoencoder.md)

Booth encoder and decoder is an stochastic model.

## [Denosing Autoencoder](denoising_autoencoder.md) (DAE)

Here we learn a encoder function that that takes an corrupted input and the networks tries to remove this corruption.

## [Manifold](autoencoder_manifold.md)

We can view learning an autoencoder as trying to learn the manifold of the training data.

## [Contractive autoencoders](contractive_autoencoders.md)

We regularize the hidden code $h=f(x)$ encouraging the derivatives of $f$ to be as small as possible.

## Applications
* dimension reduction
* information retrieval