# Graphical models

A graphical model is a way to represent a [joint distribution](probability.md) by making [CI assumptions](probability_independence.md), in particular, the nodes in the graph represent random variables, and the (lack of) edges represent CI assumptions. 

## [Directed graphical moels](directed_graphical_models.md)

The edges in the graph are directed.

## [Markov random field](markov_random_fields.md)
The edges in the graph have no orientation.

## Inference

There are two common types of questions we ask.

### Marginal inference
What is the probability of a given variable in our model after we sum everything else out:
$$
p(y=1) =\sum_{x1} \sum_{x_2} \cdots \sum_{x_n} p(y=1|x_1, x_2,\cdots,x_n)
$$

### Maximum a posteriori (MAP) inference
What is the most likely assignment to the variables in the model:

$$
\max_{x_1, x_2,\cdots, x_n} = p(y=1|,1, x_2, \cdots, x_n)
$$

In general an exact answer is NP-hard. Tractable computation depends on the structure of the graph that describes that  probability. In cases when exact inference is not tractable we result to approximate inference.

### Approximate inference
* [variable elimination](variable_elimination.md)