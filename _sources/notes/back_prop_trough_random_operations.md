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


## Back-Prop trough Discrete stochastic operations
* if the model emits discrete $y$, we cannot apply reparametrization trick

$$
y = f(z,w) \\
w = (\theta, x) \\
$$
* $z$ random noise
* f is a step function since y is discrete, the derivatives of a step function are not useful since they are 0 everywhere except at the step boundary

## Reinforce (REward Increment nonnegative Factor X Offset Reinforcement)
* the core idea is that $J(f(z;w))$ is a step function but $E_{z \sim p(z)} J(f(z,w))$ is a smooth function
* in most cases the expectation is not tractable when $y$ is highly dimensional but it can be estimated without bias using MC average
* we can use the stochastic estimate of the gradient with SGD or other gradient techniques
* this estimation has high variance thus we need to draw a lot of samples to have a good estimator and apply variance reduction techniques