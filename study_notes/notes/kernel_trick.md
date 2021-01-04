# Kernel trick 

We replaces all the inner products of the form $<x, x'>$ with a call to the kernel function $k(x, x')$. This is called the **kernel trick**.  It turns out that many algorithms can be kernelized in this way. Note that we require that the kernel be a [Mercer kernel](kernel.md) for this trick to work.

## Nearest neighbor classification

In nearest neighbours we need to compute the Euclidean distance of the test vector to all the training points and find the closest. We can kernelize:

$$
||x_i = x_{i'}||_2^2 = <x_i, x_{i'}> + <x_{i'}, x_{i'}> - 2 <x_i, x_{i'}>
$$

### [K-medoids](k_medoids.md) clustering
We can kernelize the distance function.

$$d(i,i') = ||x_i -x_{i'}||_2^2$$

This algorithm works in $O(n_k^2)$ per cluster where K-means takes $O(n_kD)$ to update each cluster.

## [Ridge-regression](ridge_regression.md)
Let $x \in R^D$ be some feature vector, and X be the corresponding $N \times D$ design matrix. We want to minimize:

$$
J(w) = (y - Xw)^T(y - Xw) + \lambda ||w||^2
$$

The optimal solution is given by:

$$
w = (X^TX + \lambda I_D)^{-1}X^Ty = (\sum_{i}x_ix_i^T + \lambda I_D)^{-1}X^Ty
$$

To kenerlize we need $XX^T$ not $X^TX$ but using the [matrix inversion lehma](matrix_inversion_lehma.md) we can express:

$$
w = X^T(XX^T + \lambda I_N)^{-1}y
$$

We can partially kernelize this if we replace $XX^T$ by a [Gramm](mercer_kernel.md) matrix K, but we still have an leading $X^T$ term.

Lets define the **dual variables**

$$
a = (K + \lambda I_N)^{-1}y
$$
We can rewrite the **primal variables** as

$$
w = X^Ta = \sum_{i=1}^N a_i x_i
$$

The solution vector is just a linear sum of N training vectors. We can express the predictive mean as:

$$
\hat{f}(x) = w^Tx = \sum_{i=1}^N a_i i^T = \sum_{i=1}^N a_i\mathcal{k}(x, x_i)
$$

Chaning to dual variables is an common approach to kernlize stuff.
## Kernel PCA

PCA computes an low-dimensional linear embedding of some data. It requires finding the eigenvectors of the sample covariacne matrix $S = \frac{1}{N} \sum_{i=1}^N x_ix_i^T = (1/N)X^TX$. However we can compute PCA also by finding the eigen vectors of the inner product matrix $XX^T$. This allows us to produce a nonlinear embedding, using the kernel trick.

Linear PCA is limited to use $L \le D$ components, in kPCA we can use up to N components since the rank of $\Phi$ is $N \times D$, where D is the (potentionally infinite) dimensionality of embedded feature vecotrs. 

There is a close connection between kernel PCA and a technique known as multidimensional scaling or MDS. This methods finds a low-dimensional embedding such that Euclidean distance in the embedding space approximates the original dissimilarity matrix.
