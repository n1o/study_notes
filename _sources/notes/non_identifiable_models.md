# Non Identifiable models

Many models are non-identifiable, especially latent variable models. Non identifiable means that multiple model settings can lead to the same data. 
An example is a [Mixture of Gaussians](gaussian_mixture_model.md) we can permute the latent Gaussians and we would get an valid model.

Non identifiability can be fixed using an proper prior, that forces a single model setting.