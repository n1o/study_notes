# Fisher information matrix
Measures the curvature of the expected negative log likelihood, hence it measures the stability of MLE.

First we define the observed information matrix at some point $\hat{\theta}$

$$
J(\hat{\theta}) \triangleq - \nabla^2_{\theta} \log p(D|\theta)|_{\hat{\theta}}
$$

If we take the expected value of it  we get the Fisher information matrix:
  
$$
I_N(\hat{\theta}) \triangleq E [J(\hat{\theta})]
$$
  