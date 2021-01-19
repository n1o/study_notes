---
more: https://web.stanford.edu/~boyd/papers/pdf/prox_algs.pdf
---
# Proximal algorithms

We consider a convex objective function:

$$f(\theta) = L(\theta) + R(\theta)$$

* $L(\theta)$ is convex and differentiable
* $R(\theta)$ is convex but not necessarily differentiable


Then the proximal operator has the form:

$$prox_R(y) = \arg \min_z (R(z) + \frac{1}{2}|| z - y ||_2^2)$$

* $prox_R(y)$ is the proximal operator

The goal of proximal operator is to minimize R but stay also close to y. The key is to efficiently compute the proximal operator for different R.

## Proximal operators

### L1 norm
$$
R(\theta) = \lambda || \theta||_1  \\ 
prox_R(\theta) = \text{soft}(\theta, \lambda) 
$$

### L2 norm
$$
R(\theta) = \lambda || \theta||_0  \\ 
prox_R(\theta) = \text{hard}(\theta, \sqrt{2\lambda}) 
$$

### Indicator function

$$
R(\theta) = I_C(\theta) \\ 
prox_R(\theta) = \argmin_{z \in C} || z - \theta ||_2^2 = proj_C(\theta)
$$

This is the projection operator. For convex sets this is easy to compute.

1. For rectangular box $C = \{ \theta : l_j \le \theta_j \le \mu_j \}$ 
$$
proj_C(\theta) = \begin{cases}
    l_j & \theta_j \le l_j \\
    \theta_j & l_j \le \theta_j \le \mu_j \\
    \mu_j & \theta_j \ge \mu_j
\end{cases}
$$
2. For euclidean ball $C = \{ \theta: ||\theta||_2 \le 1 \}$
$$
 proj_c(\theta) = \begin{cases}
     \frac{\theta}{|| \theta||_2} & ||\theta||_2 > 1 \\
     \theta & ||\theta||_2 \le 1
 \end{cases}
$$
3. The projection on the 1-norm ball $C = \{ \theta: ||\theta||_1 \le 1 \}$ 

$$
proj_C = soft(\theta, \lambda)
$$
* $\lambda = 0$ if $||\theta||_1 \le 1$ otherwise $\lambda$ is the solution to $\sum_{j=1}^D \max (|\theta_j| - \lambda, 0) = 1$

# Proximal gradient method
We can extend gradient descent to also perform proximal operator. The basic idea is to perform an quadratic approximation of the loss function arround $\theta_k$

$$
\theta_{k+1} = \argmin_z R(z) + L(\theta_k) + g_k^T(z - \theta_k) + \frac{1}{2t_k} ||z - \theta_k||_2^2
$$

* $g_k^T = \nabla L(\theta_k)$
* $\frac{1}{t_k}I \approx \nabla^2L(\theta_k)$ approximate the Hessian so we have first order method

We can simplify by dropping terms that do not depend on z and multiply by $t_k$. The gradient is zero.

$$
\theta_{k+1} = \argmin_z [t_k R(z) + ||z - u_k||_2^2 ] = prox_{t_kR}(u_k) \\
u_k = \theta_k - t_k g_k \\
g_k = \nabla L(\theta_k)
$$

Depending on $R(\theta)$ we get:
* $R(\theta) = 0$ we get gradient descent
* $R(\theta) = I_C(\theta)$ we get projected gradient
* $R(\theta) = \lambda ||\theta||_1$ we get iterative soft threshing 