# Unsupervised learning

One of the goals of unsupervised learning is to find a simpler data representations like:

1. Lower-dimensional, we compress information about x to smaller representation
2. Sparse representation, here we increase the dimension so we do not loose information but most dimensions are zero, where the data is distributed along different axis.
3. Independent representation, disentangle various sources of variation in the data source, so the dimensions of the representation are statistically independent.

## [PCA](principal_component_analysis.md)
PCA learns an representation that is lower dimensional and whose elements have no linear correlation with each other. It learns an orthogonal linear transformation of the data that projects an input x to a representation z.