# Gaussian discriminant Analysis
We can use NVM to define the class conditional densities in a generative classifier:

$$p(x|y = c, \theta) = \mathcal{N}(x| \mu_c , \Sigma_c) $$

This technique is called the Gaussian discriminant analysis. Now if we set $\Sigma_c$ to be diagonal, we get Naive Bayes.

Now we can use this conditional density to clasify a feature vector:

$$\hat{y}(x) = \arg\max_c [\log p(y =c|\pi) + \log p(x|\theta_c)] $$

If we have an uniform prior we simplify to:

$$\hat{y}(x) = \arg \min_c (x - \mu_c)^T \Sigma^{-1}_c (x - \mu_c)$$

Here we can see that we assigne the observation to that class that has the shortest Mahalanobis distance from a given class mean $\mu_c$.