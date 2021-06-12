# [Back Propagation](back_propagation.md) trough random operations
* in generative models we often wish to extend NN to implement stochastic transformations of x
  * this can be done by extending NN by extra inputs z that are samples from a simple distribution (Unif, Gauss)
  * the NN than continue working deterministically, but the function $f(x,z)$ appears stochastic to someone who as access to z
  * if $f$ is continuous and differentiable we can use backpropagation to compute gradients

## Example:
  * rewrite $y \sim N(\mu, \sigma^2)$ as $y = \mu + \sigma z, z \sim N(0,1)$
  * we backpropagate trough sampling by holding the sampling as a deterministic operation
  * the extra input z, is not a function of any variable whose derivative we want to compute
  * the result tels us how the output would change if we would make an infinitesimal change to $\mu, \sigma$ with the same z

## Reparametrization trick
* we generalize the example above (Gaussian case)
  * express $p(y;\theta) \text{ or } p(y|x;\theta)$ as $p(y;w)$
  * if we sample from $p(y|w)$ we may express $w$ as a function of other variables and express it as:
    * $$y \sim p(y|w) \\ y=f(z,w)$$
    * $z$ is a source of randomness
  * we can compute the derivative of $y$ wtr $w$ using backprop, but w cannot be a function of z 