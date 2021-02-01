# Map inference in graphical models
We try to find the most likely assignment in an probabilistic graphical model.

$$
\arg \max \sum_c \theta_c (x_c)
$$

* $\theta_c(x_c) = \log \phi_c(x_c)$

Map inference is easier than marginal inference (we do not need to calculate the partition constant Z)but it still not an easy problem in general case. But for some models MAP inference can be solved in polynomial time, while general inference is NP-hard.

By performing marginal inference we sum over all the assignments, one of which is the MAP assignment. We could simply replace summation with maximization to find the assignment with the highest probability, but there are more efficient methods. 

## Example
* [structured predictions](structured_predictions.md)
* Image segmentation, we try to locate an entity in an image and label all its pixels. The input is $x\in[0,1]^{d\times d}$ image pixel matrix and we predict the label $y\in \{0,1 \}^{d\times d}$ where each pixel encodes the object we want to recover. We assume that neighboring pixel have similar values in y.

## [Graph cuts](graph_cut_map_inference.md)
Map inference on a particular class of MRFs to the [min-cut problem](graph_cut.md). 
