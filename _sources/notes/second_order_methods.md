// TODO shorten
# Second order methods
We use the Hessian in the search for the minima.

# [Newtons Method](newtons_method.md)

# Secant method

It applies Newton method using estimates of the Hessian using $\nabla f$. Thus it requires knowing the gradient. 

The secant method uses the last two iterates to approximate the second derivative:

$$f''(x^{(k)}) \approx \frac{f'(x^{(k)}) -f'(x^{(k-1)})}{ x^{(k)} - x^{(k-1)}}$$

We can substitute this into newtons method:

$$ x^{(k+1)} = x^{(k)} - \frac{x^{(k)} - x^{(k-1)}}{ f'(x^{(k)}) - f'(x^{(k-1)})} f'(x^{(k)})$$

The algorithm for secant point requires an additional initial design point. It suffers from the same problems as Newtons method, and it takes longer to converge due to the approximation.


# Quasi Newton
Similarly as the secant method, it approximates the Hessian. To be more specific the Inverse Hessian. The Quasi newton has the from:

$$ x^{(k+1)} = x^{(k)} - \alpha^{(k)} Q^{(k)} g^{(k)}$$

* $\alpha^{(k)}$ is a scalar step 
* $Q^{(k)}$ is the approximation of the inverse hessian at $x$

We start $Q^{(1)} = I$ and at each iteration we update it. There are two main variants:

1. Davidon-Fletcher Powell (DFP)
2. Byorden Fletcher Goldfarb Shanno (BFGS)

Booth algorithms use the following definitions:


$$ \gamma^{(k+1)} = g^{(k+1)} - g^{(k)}$$
$$ \delta^{(k+1)} = x^{(k+1)} - x^{(k)}$$

## Davidon Fletcher Powell

$$Q \leftarrow Q - \frac{Q \gamma \gamma^T Q}{\gamma^T Q \gamma} + \frac{\delta \delta^T}{\delta^T \gamma}$$

* $\gamma = \gamma^{(k)} = g^{(k+1)} - g^{(k)}$
* $\delta = \delta^{(k)} = x^{(k+1)} - x^{(k)}$

This update has the following properties:
1. $Q$ remains symmetric and positive definite
2. If $f(x) = \frac{1}{2}x^TAx + b^Tx + c$ then $Q^{-1} =A^{-1}$. Thus DFP retains the convergence properties of conjugate gradient method.
3. For higher-dimensional problems, storing and updating Q can be significant compared to other methods like conjugate gradient method.


## Byorden Fletcher Goldfarb Shanno (BFGS)

$$ Q \leftarrow Q - \Big( \frac{\delta \gamma^T Q + Q \gamma \delta^T}{\delta^T \gamma} \Big) + \Big( 1 + \frac{\gamma^T Q\gamma}{\delta^T \gamma} \Big) \frac{\delta \delta^T}{\delta^T \gamma} $$

BFGS does better than DFP with approximate line search but it still requires $n\times n$ dense matrix. For very large problems space is a concern. Limited memory BFGS (L-BFGS) can be used to approximate BFGS.

### L-BFGS
Stores only the last m values for $\delta$ and $\gamma$ rather than the full inverse Hessian where $i = 1$ indexes the oldest value and $i=m$ indexes the most recent. The process for computing the descent direction at x begins by computing $q^{(m)} = \nabla f(x)$ the remaining vector $q^{(i)}$ for i from m-1 to 1 are computed using:

$$q^{(i)} = q^{(i=1)} - \frac{(\delta^{(i+1)})^T q^(i+1)}{(\gamma^{(i+1)})^T \delta^{(i+1)}}\gamma^{(i+1)}$$

These vectors are then used to compute an another $m+1$ vectors staring with:

$$ z^{(0)} = \frac{\gamma^{(m)} \odot \delta^{(m)} \odot q^{(m)} }{(\gamma^{(m)})^T \gamma^{(m)}} $$

and proceding with $z^{(i)}$ from i to m according to:

$$z^{(i)} = z^{(i-1)} + \delta^{(i-1)} \Big( \frac{(\delta^{(i-1)})^T q^{(i-1)}}{(\gamma^{(i-1)})^T \delta^{(i+1)}} - \frac{(\gamma^{(i-1)})^T z^{(i-1)}}{(\gamma^{(i-1)})^T \delta^{(i-1)}} \Big)$$

The descent direction is $d = -z^{(m)}$

For minimization the inverse Hessian $Q$ must remain positive definite. The initial Hessian is often set to the diagonal of:

$$
Q^{(1)} = \frac{\gamma^{(1)} (\delta^{(1)})^T}{(\gamma^{(1)})^T \gamma^{(1)}}
$$

Computing the diagonal for the expression above and substituting the result into $z^{(1)} = Q^{(1)} q^{(1)}$ results in $z^{(1)}$

In general Quasi Newton performs well.
