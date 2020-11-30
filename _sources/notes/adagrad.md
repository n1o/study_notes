# Adagrad (Adaptive subgradient method)
 Adapts a learning rate for each component of x. Adagrad dulls the influence of parameters with consistently high gradients, and increase the influence of parameters with infrequent updates. Adagrad excels when the gradient is sparse. 

## Steps

$$x_i^{(k+1)} = x_i^{(k)} - \frac{\alpha}{\epsilon + \sqrt{s_i^k}}g_i^k$$

*  $s^k$ is a vector whose ith entry is the sum of the squares of the partials with respect to $x_i$ up to time step k:

$$
s_i^{(k)} = \sum_{j=1}^k (g_i^{(k)})^2
$$
* $\epsilon$ is a small value so we do not divide by zero 

Adagrad is not sensitive to the choice of the learning rate $\alpha$, we can default it to $\alpha = 0.01$. 

## Cons
It primary weakness is that $s$ is strictly non decreasing. This accumulated sum causes the effective learning rate to diminish before convergence.

## Algorithm
Initialize:

$\alpha$ learning rate, $\epsilon$ small value, $s=0$ sum of squares gradient

Iteration:

$g = \nabla f(x), s = g \cdot g$

return $x - \alpha \cdot g / (\sqrt{s} + \epsilon )$