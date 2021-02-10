# MLE for Bayesian Networks
 
Here we look at how to learn parameters of a Bayesian network.

Suppose we are given i.i.i samples $D=\{x_1, \cdots, x_n \}$ and a Bayesian network:

$$
p(x) = \prod_{i=1}^n \theta_{x_i|x_{\text{pa}(x)}}
$$

Now we want to estimate the [MLE](maximum_likelihood_learning.md) of parameters (Conditional probability Densities). Our likelihood is:

$$
L(\theta|D) = \prod_{j=1}^n \sum_{j=1}^m \theta_{x_i^{(j)}|x_{\text{pa}(i)}^{(j)}}
$$

We take logs and combine terms we get:

$$
\log l(\theta|D) = \sum_{i=1}^n\sum_{x_{\text{pa}(i)}}\sum_{x_i} \#(x_i,x_{\text{pa}(i)}) \cdot \log \theta_{x_i|x_{\text{pa}(x)}}
$$

We can decompose the maximization of the log function into separate minimization's for local conditional distribution. If we have discrete variables the MLE estimate has a closed form solution.

$$
\theta_{x_i|x_{\text{pa}(x)}}^* = \frac{\#(x_i, x_{\text{pa}(i)})}{\#(x_{\text{pa}(i)})}
$$

Even if we do not have discrete variables, the log-factors are linearly separable, thus we can estimate each factor separately.