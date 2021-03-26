# Neural network universal approximator

Given enough hidden units and at least one nonlinear activation a [neural network](neural_networks.md) may approximate any function with arbitrary low error. However it still may fail if
* the learning algorithm wont find the correct weights
* the learning algorithm overfits

In general it is advised to use deeper neural networks than wider, this can lead to less units needed for better accuracy.

By choosing a deep model, we say that we believe that the learning consists of discovering a set of underlying factors of variations that can be expressed in terms of other simpler underlying factors of variations.