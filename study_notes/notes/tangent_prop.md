# Tangent prop

We train an [neural network](neural_networks.md) classifier with extra penalty to be locally invariant to known factors, these factors correspond to movement along the [manifold](manifold_learning.md) near which examples of the same class concentrate.

We achieve local invariance by requiring $\nabla x f(x)$ to be orthogonal to the known manifold tangent vector $v^{(i)}$ at x or equivalently that the directional derivative of $f$ at x in the direction $v^{(i)}$ be small by adding a regularization penalty:

$$
\Omega(f ) = \sum_i ((\nabla f(x))^T v^{(i)})^2
$$

These tangent vectors are usually defined aprior from formal knowledge.