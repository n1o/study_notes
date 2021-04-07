# RMS Prop
Extends [Adagrad](adagrad.md) to avoid the effect of a monotonically decreasing learning rate. It maintains an decaying average of squared gradients. Works good in nonconvex settings. This average is updated according:

$$
\hat{s}^{(k+1)} = \gamma \hat{s}^{(k)} + (1-\gamma)(g^{(k)} \odot g^{(k)})
$$

* $\odot$ is element wise product
* $\gamma \in [0,1]$ is the decay rate often set to $0.9$

The update rule is the same as for Adagrad but with the decaying average:

$$
x_i^{(k+1)} = x_i^{(k)} - \frac{\alpha}{\epsilon + \sqrt{\hat{s_i}^{(k)}}} g_i^{(k)} \\
x_i^{(k+1)} = x_i^{(k)} - \frac{\alpha}{\epsilon + \text{RMS}(g_i)}g_i^{(k)}
$$
* $\text{RMS}(g_i)$ is a shorthand for the decaying root mean squared

## Algorithm
Initialize:

$\alpha$ learning rate, $\gamma$ decay rate, $\epsilon$ is a small number, $s=0$ sum of squared gradient

Iterate:
$$
g =\nabla f(x) \\ 
s = \gamma s + (1 - \gamma)*(g \cdot g) \\
\text{return } x - \alpha * g / (\sqrt{s} + \epsilon)
$$
