# Auto Regressive networks
* directed probabilistic models without latent variables, where conditional probability distribution are represented using NN
* the graph structure is a complete graph
* decomposes a joint probability distribution over visible variables as a product of conditionals 
    $$
    p(x_d|x_{d-1}, \cdots, x_1)
    $$

## Linear Auto-Regressive networks

* each $p(x_d|x_{d-1}, \cdots, x_1)$ is a linear model
* if the variables are continuous, than the linear auto-regressive model is just an another way to formulate a multivariate Gaussian dist, capturing linear pairwise interactions between the observed variables

![](../.images/machine_learning/linear_autoregressivej_networks.png)

## Neural Auto Regressive networks

* same left to right flow as linear auto-reg networks
* joint conditional are parametrized using a NN, which is powerful enough to approx any joint distribution