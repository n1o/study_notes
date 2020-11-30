# Jeffrey prior

General purpose technique for creating [uninformative priors](uninformative_prior.md). The key assumption is that $p(\phi)$ is uninformative, than any re-parametrization of the prior $\theta = h(\phi)$ , for some funcion h, should also be uninformative.

We start by change of variables formula:

$$p_{\theta}(\theta) = p_{\phi}(\phi)|\frac{d\phi}{d\theta}|$$

so in general the prior will change, but if we pick:

$$ p_{\phi}(\phi) \propto (I(\phi))^{1/2} $$ 

where:

*  $I(\phi)$ [Fisher information](fisher_information_matrix.md) and it measures the curvature of the expected negative log likelihood, hence it measures the stability of MLE.

Now if:

$$\frac{d \log p(x|\theta)}{d \theta} = \frac{d \log p (x|\phi)}{d\phi} \frac{d\phi}{d\theta} $$

Now we square and take the expectation over x:

$$I(\theta) = -E [(\frac{d \log p(X|\theta)}{d \theta})^2] = I(\phi)( \frac{d\phi}{d\theta})^2$$

$$I(\theta)^{1/2} = I(\phi)( \frac{d\phi}{d\theta})^{1/2}$$

Now the transformed prior is:

$$ p_{\theta}(\theta) = p_{\phi}(\phi)|\frac{d\phi}{d\theta}| \propto I(\phi)( \frac{d\phi}{d\theta})^{1/2} = I(\theta)^{1/2}$$

Hence $p_{\theta}(\theta) = p_{\phi}(\phi)$ are the same.

## Intuition behind Jeffrey prior

It puts less prior weight on parameter values where the likelihood is flat (Since Fisher information measures curvature of the log likelihood), thus preventing the prior from having undue influence.