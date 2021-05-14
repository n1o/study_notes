# Leibnitz rule
* it is applicable if we differentiate under integral sign

$$
\nabla_\theta \int p(x)dx = \int \nabla_{\theta} p(x)dx
$$

* this is possible only when 
  * $p$ is a [Lebesgue integrable](lebesgue_integral.md) function of x for every $\theta$
  * $\nabla_{\theta} p(x)$ exists for all $\theta$ and almost all $x$
  * there exists an integrable function $R(x)$ that bound $\nabla_{\theta}$ in sense that $\max_i |\frac{\partial}{\partial \theta_i} p| \le R(x)$