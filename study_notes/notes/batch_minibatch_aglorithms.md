# Batch and mini-batch algorithms

The objective function in most machine learning algorithms can be expressed as a sum over the training examples. In most cases we evaluate the expected value of the cost function only on a subset of terms of the full cost function.

The gradient of the loss function is:

$$
\nabla \theta J(\theta) = E_{x,y \sim \tilde{p}_{\text{data}}} \nabla_\theta \log p_{\text{model}}(x,y;\theta)
$$

* $E_{x,y \sim \tilde{p}_{\text{data}}}$ is the expectation over the data which can be expensive if we have a lot of it

In practice we evaluate the expectation only on a random subsample (mini-batch) of the data. This can be justified by looking at the standard error for the [sample mean](estimator.md) 

$$\sigma /\sqrt{n}$$

There is less than linear return for adding more samples.


## Mini-batch size

* Larger more accurate
* smaller batch can have regularization effect 
* gradient based algorithms are robust and can handle small batch size (~100)
* second order methods require +10_000