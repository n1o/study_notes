# Deep recurrent neural networks

Most [RNN](recurrent_neural_networks.md) consists of 3 blocks of parameters.

1. From input to hidden
2. From previous hidden state to the next hidden state
3. From hidden state to the output

![](../.images/machine_learning/deep_rnn.png)

There are multiple options how to implement deep RNN.
* we can have a hierarchy of hidden states
* we can add an extra step between hidden states
* we can have skip connection between hidden states

