# Sparse Linear models

A set of [generalized linear models](generalized_linear_model.md) of the form $p(y|Z) = p(y| f(w^Tx))$ for some link function $f$, where we ecnourage the weight vector w to be **sparse**. This approach offers significant computational advantages like:

1. If the number of dimensions D is larger than N. We want to find the smallest subset of features that can accurately predict the response in order to prevent overfitting.
2. Useful i context of sparse kernel machines. 

