# Greedy layer wise unsupervised pre-training
* rely on a single layer representation learning algorithm as RBM or single layer [autoencoder](autoencoder.md), [sparse coding](sprase_coding.md) or some latent variable representation.
* we greedily pre-train each layer using unsupervised pre-training, when we ad a new layer than the weights of the previous layer are not adapted anymore. Each new layer should produce a new representation that should be simpler than the previous
* it is not popular anymore, but it is still used in NLP.
* after pre-training we train the network as a whole, thus we fine tune all the layers together 
* we can use it as initialization for unsupervised learning algorithms as deep autoencoders or probabilistic models with many layers of latent variables.
* pretraining provided more consistent convergence

## When this will work?
* on many tasks it is harmful, and it was used to provide a good initialization to avoid local minima, but since we have a lot of data we do not worry about local minima anymore
* popular for word embedding, in general abandoned
* well suited if we have only a few labeled examples


## Downsides
* separate training stages make it hard to tune hyperparameters