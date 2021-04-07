# Neural networks parameter initialization
The starting point affects most of the [optimization of a neural network](optimization_in_deep_learning.md). Every unit has to have different initial weights otherwise they would receive the same update.

## Break symmetry 
If two hidden units share the same input have the same activation function must have different weights otherwise during optimization they would be updated the same way.

## Normalized initialization

$$
w_{ij} \sim U(-\sqrt{\frac{6}{m+n}}, \sqrt{\frac{6}{m+n}})
$$

* $m$ the number of inputs
* $n$ is the number of outputs

This initialization is the compromise between the goal for all layers having the same activation variance and the goal of having the same gradient variance.

## Sparse initialization
We have at most k nonzero weights.

## Bias initialization
In most cases we can initialize bias to zero. For some special cases we can have nonzero bias:
* output unit
* [relu units](rectified_hidden_unit.md) set bias to 0.1 to avoid saturation
* for gated LSTM we set bias to 1 since it controls which other unit is able to participate and initially we want all the units to participate.
