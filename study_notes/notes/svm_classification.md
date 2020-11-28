# [SVM](support_vector_machines.md) classification

We use [hinge loss](hinge_loss.md) as our loss function, and our objective is:

$$
\min_{w, w_0} = \frac{1}{2}||w||^2 + C \sum_{i=1}^N(1 - y_i f(x_i))_+
$$

This is again non differentiable, so we introduce slack variables
$$
\min_{w, w_0, \xi} \frac{1}{2}||w||^2 + C \sum_{i=1}N\xi_i \\ 
\text{ s.t} \\
\xi_i \ge 0 \\
y_i(x_i^T + w_0) \ge 1 - \epsilon_i; i = 1: N
$$

This is an quadratic program. And standard solvers solve it in $O(N^3)$, however there are specialized algorithms like **sequential minimal optimization (SMO)** than in practice take $O(N^2)$ for large problems it is best to use a linear SVM which can be trained in $O(N)$

The solution has the from of 

$$
\hat{w} = \sum_i a_ix_i
$$

* $\alpha_i = \lambda_i y_i$

$\alpha$ is sparse because of the hinge loss. The $x_i$ for which $\alpha_i \ge 0$ are called support vectors; these are the points which are either incorrectly classified, or are classified correctly but are on or inside the margin. 

The prediction is done using:

$$
    \hat{y}(x) =sgn(f(x)) = sgn(\hat{w}_0 + \hat{w}^Tx) \\
    \hat{y}(x) =sgn(\hat{w}_0 + \sum_i \alpha_i k(x_i, x))
$$

Alternatively we can view this as [large margine principle](svm_classification_large_margine_principle.md)