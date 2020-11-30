# Local descent

Basic idea behind local descent is to use local models to incrementally improve a design point until some convergence criterion is met.

## Descent direction iteration
Here we take a step that minimizes the objective value based on a local model. The local model can be obtained using an First or Second order Taylor approximation. Algorithms that follow this general approach are refered as descent direction methods. They start with a design point $x^{(1)}$ and then generate a sequnce of points (iterates) to converge to a local minimum.

This iterative descent direction procedure involves the following steps:
1. Check if $x^{(k)}$ satisfies the [termination condition](local_descent_terminal_conditions.md). If it does, terminate; otherwise procede to the next step.
2. Determine the descent direction $d^{(k)}$ using local information (gradient, Hessian)
3. Determine the step size or learning rate $\alpha^{(k)}$. Some algorithms attempt to optimize the step size so that the step maximally decreases $f$. 
4. Compute the next design point according to: 

$$
 x^{(k+1)} \leftarrow x^{(k)} + \alpha^{(k)} d^{(k)}
$$

Determining $\alpha$ and $d$ we can use different optimization methods.