# Generalized linear mixed models

We generalize multi-task learnining scenario to llow the response to include information at the group level $x_j$ as well as on the item level $x_{ij}$. We can also allow the parameters to vary across groups $\beta_j$, or to be tied across groups, $\alpha$. This gives the following model:

$$ E[y_{ij}| x_{ij}, x_i] = g(\phi_{1}(x_{ij}^T \beta_j + \phi_2(x_j)^T \beta'_j + \phi_3(x_{ij}^T \alpha + \phi_4(x_j)^T \alpha')) $$

* $\phi_k$ are basis functions.

* $\beta_j$ their number grows with each group, and they are also called **random effects** since they wary across groups

* $\alpha$ are called fixed effects, since they are viewed as fixed but unknown constant.
  Hente these models are called **mixed models** and if $p(y|x)$ is a GLM they are called **generalized linear mixed effect models** 


## Computational issues

They are bloody hard to fit, and in general ve use MCMC or Variational EM.