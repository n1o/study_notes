# Polyak Averaging

Average serveral points that where visited by an optimization algorithm. If t iterations of gradient descent visit points $\theta^{(1)}, \cdots, \theta^{(t)}$ than the Polyak average is:

$$
\hat{\theta}^{(t)} = \frac{1}{t} \sum_{i} \theta^{(i)}
$$

For convex problems this has strong convergence guarantees. For noncovex settings we have to agument it a bit and use an exponentially decaying running average:

$$
\hat{\theta}^{(t)} =  \alpha\hat\theta^{(t-1)}  + (1+\alpha) \theta^{(t)}
$$