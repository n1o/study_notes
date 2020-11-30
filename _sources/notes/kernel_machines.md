# Kernel machines

We define a **kernel machine** to be a GLM where the input feature vector has the form:

$$
\phi(x) [\mathcal{k}(x, \mu_1), \cdots, \mathcal{k}(x, \mu_K)]
$$

* $\mu_k \in \mathcal{X}$ are a set of K **centroids**

This equations is allso known as a **kernelised feature vector**. This is because we modify the feature vector.

The **main issue with kernel machines** is how do we choose the centroids $\mu_k$.  An approach is to find clusters in the data and then to assign one prototype per cluster  center (many clustering algorithms just need a similarity metric as input). However, the regions of space that have high density are not necessarily the ones where the prototypes are most useful for representing the output, that is, clustering is an unsupervised task that may not yield a representation that is useful for prediction.

We can use this kernelized feature vector for logistic regression by defining $p(y|x, \theta ) = Ber(w^T\phi(x))$. This provides a very simple way to define a nonlinear decision boundary.  And for linear regression by defining $p(y|x, \theta) = N(w^T\phi(x), \sigma^2)$.