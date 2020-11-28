# Derivation of BIC


If we take the [Gaussian approximation](gaussian_approximation.md) to the marginal likelihood and drop the irelevant terms:s


$$p(D) \approx e^{-E(\theta^*)} (2\pi)^{D/2} |H|^{-\frac{1}{2}} \\
\log p(D) \approx \log p(D|\theta^*) + \log p(\theta^*) - \frac{1}{2}\log|H|$$

* $E(\theta^*) = \log p(\theta^*, D)$

* $p(D| \theta^*)$ is also known as **Occams factor** and it measures the model complexity

If we assume uniform prior $p(\theta)\propto 1$ we can replace $\theta^*$ by the MLE $\hat{\theta}$ and drop $\log p(\theta^*)$

Thus we remain with

$$
\log p(D) \approx \log p(D|\hat{\theta}) - \frac{1}{2}\log|H|
$$

We need to approximate $\log |H|$ also alled **Occmas factor** since it measures the model xomplexity (volue of the osterioir distribution). 
$$H = \sum_{i=1}^N H_i$$ 

* $H_i = \nabla \nabla \log p(D_i| \theta)$

Each $H_i$ can be approximated by a fixed matrix 

$$H_i \approx \hat{H}$$

* $\hat{H}$ is a fixed matrix

Than we have:

$$\log |H| = \log|N\hat{H}| = \log(N^d|\hat{H}|) = D \log N + \log |\hat{H}|$$

* $D = \dim(\theta)$
* $H$ is full rank

($N^d$ is from [rules of determinats](rules_of_determinants.md) sice we multiply each row by N).

Now $\log |\hat{H}|$ is independent of N, it will be overwhelmed by the likelihood hence we can approximate the marignal likelihood as:

$$\log p(D) \approx \log p(D\ |\hat{\theta})- \frac{D}{2} \log N$$
