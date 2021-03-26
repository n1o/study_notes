# Regularization in Neural Networks

The main idea behind [regularization](regularitzation.md) is to reduce the variance of an [estimator](estimator.md) without increasing its bias by much. This leads to better performance on a holdout set. 

Regularization can help to solve undetermined (unidentifiable) problems. In deep learning the best performing models are large and heavily regularized.

## Parameter norm penalties

We extend the objective function by introducing a norm penalty:

$$
\tilde{J}(\theta; X,y) = J(\theta; X,y ) + \alpha \Omega(\theta)
$$

* $\Omega$ is the norm penalty on the weights $\theta$
* $\alpha \in [0, \infty]$ controls the influence of the norm penalty, larger values contribute more regularization, it may be different for different layers

If we minimize $\tilde{J}$ we booth minimize the objective and the penalty. Based on the choice for $\Omega$ we get different solutions.

Regularization is applied only to the weights of [affine transformation](affine_function.md) not the bias terms.

### L2 regularization  (Weight Decay, Thinkov regularization)

$$
\Omega(\theta) = \frac{1}{2}||w||^2_2 \\
w \leftarrow (1 - \epsilon \alpha)w - \epsilon \nabla J(w; X,y)
$$

This results in weight decay, at every step we shrink the weight by a constant factor.

After training weight decay results in shrinking the weights of a regularized proportional to the hessian of the loss function and the regularization strength.

$$
\tilde{w}_i = w^*_i - \frac{\lambda_i}{\lambda_i + \alpha}
$$

* $w^*$ is the unregularized solution
* $\lambda_i$ is the ith eigenvalue of the hessian of the unregularized objective function, if $\lambda_i$ is small than this direction contributes only little and it is shrunk more.
* $\alpha$ controls the strength of regularization

### L1 regularization 

$$
\Omega(\theta) = ||w|| = \sum_i |w_i| \\
\tilde{J} (w;X,y) = \alpha ||w||_i + J(w;X,y) \\
\nabla \tilde{J} = \alpha \text{sign}(w) + \nabla_w J(w;X,y) 
$$

* the gradient does not scale linearly for each w but it is a linear factor with sign $\text{sign}(w)$.

## Noise robustness

If we add a small noise to the weights:

$$
\epsilon w \sim N(\epsilon; 0, \eta I)
$$

This forces the parameters to go into regions where the space is relatively flat, thus a small perturbation of weights will lead only to a small change in the output.

## Label smoothing
We inject noise at the target labels, thus we explicitly model error in the input. An example is to replace hard 0-1 assignment by scaling them up or down by a small number. 

## Early stopping
We stop training when we stop improving.
