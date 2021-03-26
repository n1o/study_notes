# Tangent distance
Nonparametric nearest neighbor algorithm where the distance metric is derived using manifolds near which probability concentrates. If we want to classify examples and if they lie on the same [manifold](manifold_learning.md) they share the same category.  

If we want to compare $x_1,x_2$ we compare the distance between the manifold they belong $M_1, M_2$

In general finding the manifold $M_i$ is difficult, thus we approximate it by its tangent plane at $x_i$ and than we measure the distance between two tangents or between tangents and points. This can be solved by a low dimensional linear system.
