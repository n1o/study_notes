# Hypergradient Descent
Accelerated descent methods are either extremely sensitive to the learning rate, or fo to great lengths to adapt the learning rate during execution. The learning rate dictates how sensitive the method is to the gradient signal. (A the rate is too high or too low often drastically affects performance). 

Hyper gradient descent was developed by looking at the derivative of the learning rate to improve the performance of an optimizer.
A hypergradient is the derivative taken with respect to a hyperparameter. Hypergradient reduces the sensitivity to the hyperparameter, allowing to adapt more quickly. 

Hyper gradient descent applies gradient descent to the learning rate of an underlying descent method. The method requires that the partial derivative of the objective function with respect to the learning rate. 

## Gradient Descent
An example of hypergradient descent for gradient descent:

$$
\frac{\partial f(x^{(k)})}{\partial \alpha} = (g^{(k)})^T \frac{\partial}{\partial \alpha}(x^{(k-1)} - \alpha g^{(k-1)}) \\

= (g^{(k)})^T (-g^{(k-1)})
$$

Computing Hypergradient requires keeping track of the last gradient. The update rule becomes:

$$
\alpha^{(k_1)} = \alpha^{(k)} - \mu \frac{\partial f(x^{(k)})}{\partial x} \\
= \alpha^{(k)} + \mu (g^{(k)})^T g^{(k-1)}
$$

* $\mu$ is the hypergradient learning rate.