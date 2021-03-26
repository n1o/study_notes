# Feed forward Neural Network (Multilayered perceptron MLP)

The grand goal is to approximate some function $f^*$ (this can be either a classifier or regressor)

$$
y= f^*(x;\theta)
$$
* $\theta$ is a parameter that is learned so the approximation is tight

The evaluation in MLP starts at the input x goes trough intermediate functions to finally produce an output y. **There are no self loop.**

We compose multiple functions (one of the reasons it is called neural networks since they can be represented as an acyclic graph)

$$
f(x) = f^{(3)}(f^{(2)}(f^{(1)}(x)))
$$

* $f^{(1)}$ is the first layer, also called hidden layer
* $f^{(2)}$ is the second layer, also called hidden layer
* $f^{(3)}$ is the final layer or output layer

We call [hidden layer](hidden_unit_neural_network.md) because the output of these layers are not defined in the training data. Each hidden layer is typically vector valued, the dimension of the hidden layer determines the width of the model. Each layer consists of many units acting in parallel, each representing a vector to scalar function. Each unit resembles a neuron in sense that it receives input from many other units and computes its own activation value.
