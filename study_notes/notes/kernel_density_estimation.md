# Kernel density estimation (KDE)

Similar to Gaussian mixture model, but instead of choosing K number of cluster centers we allocate one cluster center per data point, so $\mu_i = x_i$. The model:

$$
p(x|D) = \frac{1}{N} \sum_{i=1}^NN(x|x_i, \sigma^2I)
$$

Which can be generalized as:

$$
\hat{p}(x) = \frac{1}{N} \sum_{i=1}^N \mathcal{k}_h(x - x_i)
$$

This is called a Parzen window density estimator, or kernel density estimator  (KDE), and is a simple non-parametric density model. The advantage over a parametric model is that no model fitting is required (except for tuning the bandwidth, usually done by cross-validation). and there is no need to pick K . The disadvantage is that the model takes a lot of memory to store, and a lot of time to evaluate. It is also of no use for clustering tasks. 

Essentially this model results in an smooth histogram.