# Empirical Bayes

In [hierarchical Bayesian models](hierarchical_bayesian_models.md), we need to compute the posterior on mulitple levels of latent variables. An example of a two level model:

$$p(\eta , \theta |D) \propto p(D| \theta)p(\theta| \eta) p(\eta) $$

Even if we assume an uninformative prior on $p(\eta)$this can be expensive. There is a computational shortcut, that we approximate the posterior on the hyper-parameter with a point estimate, $p(\eta| D) \approx \delta_{\eta}(\eta)$ where $\eta = \arg\max  p(\eta|D)$. In general $\eta$ is much smaller that $\theta$ in dimensionality, and it is less prone to overfitting so we can use a uniform prior, than it simplifies to:



$$ \hat{\eta}= \arg\max p(D| \eta) = \arg \max [\int p(D|\theta) p(\theta |\eta) d\theta]$$

This is also called **Empirical bayes (EB)** or **type II maximum likelihood**. And we can see that we maximize the hyperprior so it matches our data well. (Or we can say that we learn the hyper-prior from the data) . In machine learning it is sometimes called the **evidence procedure**.