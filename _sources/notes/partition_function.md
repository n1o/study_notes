# Partition function

* most probabilistic models are defined using the unnormalized distribution 
    $$
    \tilde{p}(x;\theta)
    $$
* to normalize we divide by the partition function 
    $$
    p(x;\theta) = \frac{1}{Z(\theta)} \tilde{p}(x;\theta)
    $$
    * $Z(\theta) = \int \tilde{p}(x)dx \\ =\sum_x \tilde{p}(x)$

* computing the partition function is often non-tractable

## Log likelihood gradient

$$
\nabla_\theta \log p(x;\theta) = \nabla_{\theta} \log \tilde{p}(x;\theta) - \nabla_\theta \log Z(\theta)
$$
* we have two phases
  * positive phase  $\nabla_{\theta} \log \tilde{p}(x;\theta)$
  * negative phase $\nabla_\theta \log Z(\theta)$

* The real challenge is the negative phase, especially for model that have latent variables

    $$
    \nabla \log Z = \frac{\nabla_\theta Z}{Z} = \frac{\nabla_\theta \sum_x \tilde{p}(x)}{Z} =  \frac{ \sum_x \nabla_\theta \tilde{p}(x)}{Z}
    $$

    * for models $p(x) > 0$ for all x, we can substitute $\tilde{p}(x)$ with  $\exp \{\log \tilde{p}(x)\}$
    $$
    \frac{\sum_x \nabla_\theta \exp \{\log \tilde{p}(x) \}}{Z}\\
    = \frac{\sum_x \exp \{\log \tilde{p}(x) \} \nabla_\theta \log \tilde{p}(x) }{Z} \\ 
    = \frac{\sum_x \tilde{p}(x) \nabla_\theta \log \tilde{p}(x) }{Z} \\ 
    = \sum_x \tilde{p}(x) \nabla_\theta \log \tilde{p}(x) \\
    = E_{x \sim p(x)} \nabla_\theta \log \tilde{p}(x)
    $$
    * for continuous $x$ we have
    $$
        \nabla_\theta \int \tilde{p}(x)dx = \int \nabla_{\theta} \tilde{p}(x)dx
    $$
    here we have to apply [leibnitz rule](leibnitz_rule.md) for this $\tilde{p}$ has to have some properties, most ML models have these properties.

* the property:

    $$
    \nabla \log Z  = E_{x \sim p(x)} \nabla_\theta \log \tilde{p}(x)
    $$
    is the basis of monte carlo methods to maximize the likelihood of models with intractable partition functions. This learning can be decomposed into two steps
    1. Positive phase we increase $\log \tilde{p}(x)$ for $x$ drawn from the data (this pushes the energy of the training examples)
    2. Negative phase, decreasing the partition function by decreasing $\log \tilde{p}(x)$ drawn from the model distribution (pushing the energy of samples down from the model) 

    ![](../.images/machine_learning/positive_negative_phase.png)

* computing $E_{x \sim p(x)} \nabla_\theta \log \tilde{p}(x)$ can be done by using MCMC
  * MCMC approach can be viewed as achieving balance between
    * pushing up the model distribution where the data occurs $\max \tilde{p}$
    * pushing down on the model distribution where the model samples occur, thus we reduce the probability of points where the model is incorrect

  * MCMC can be slow there are several approaches how to improve its speed
    * **Contrastive divergence** (CD-k, k step Gibbs sampling), we initialize the chain using samples from the data distribution, initially the negative phase is not very accurate, but as the model improves the negative phase becomes more accurate
      * it fails to suppress high probability regions far away from the training data  
      * only applicable to shallow models

    * **Stochastic maximum likelihood** (SML, SCD-K, k-step Gibbs sampling), we initialize the Markov Chain at every step from the previous step, if the gradient steps are small than the model does not change very much
      * it is efficient for deep models
      * it fails if the step size is too large and the MCMC does not mix between steps