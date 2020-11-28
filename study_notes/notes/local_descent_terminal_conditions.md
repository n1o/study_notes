# Terminal conditions
There are four common termination conditions for [descent direction methods](local_descent.md)

1. **Maximum iterations**,  we terminate if the number of iterations exceeds an threshold $k > k_{\text{max}}$
2. **Absolute improvement**, we check the change in the function if it is too small we terminate $f(x^{(k)}) - f(x^{(k+1)}) < \epsilon_d$ 
3. **Relative improvement**, we also look at the change in the function, but uses step factor relative to the current function value $f(x^{(k)}) - f(x^{(k+1)}) \le \epsilon_r(f(x^{(k)}))$
4. **Gradient magnitude**, we terminate if the gradient is too small $||\nabla f(x^{(k+1)}) || \le \epsilon_g$

In cases of local minima, we should do some random restarts.