# Bayesian occam's razor.

Given the following poterior distribution:

$$p(\theta|D,m) =  \frac{p(D|\theta)p(\theta|m)}{p(D|m)}$$

* $m$ is a specific model
* $\theta$ are the parameters of the model
* $D$ the data

To find the marginal likelihood we need to integrate out all the model parameters. 

$$p(D|m) = \int p(D| \theta)p(\theta|m)d\theta $$

This integration protects us from overfitting, since models that have more parameters (are more complex), they do not nescessarily have higher maginal likelihood. (we can compare the marginal likelihood for differend models to [choose a better one](bayesian_model_selection.md))

## Intuition
An intuitive expalining of occams razor is that: Each probablity distribuiton has to sum to one: $\sum_{D'} p(D',m) = 1$. Complex models which can predict a lot of things must spread their probability mass thinlly, and hence will not obtain a large probability for any given data set as a simpler model. (This is also called the conservation of probablity mass)