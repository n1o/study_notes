# Posterior predictive distribution

We use the posterior distribution to generate new data and compare it to the observed quantities. The idea behind posterior predicitve check, is that if we manage to create a model that captures the data generative process well, than the data generated from the posterior distribution should be similar to the observed data.

We draw:

$$
p(\tilde{y}|D) = \int p(\tilde{y}|\theta) p(\theta|D)d\theta
$$

We can use this distribution to check if the data generated from the model is similar to the observed data. This procedure is also known as **posterior preditive check**. If this fails we know that our model is wrong.