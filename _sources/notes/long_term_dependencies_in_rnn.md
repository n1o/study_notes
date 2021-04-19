# Long term dependencies in [RNN](recurrent_neural_networks.md)

If we propagate the gradient over many stages it tends to vanish or explode. Even if this does not happen, the difficulty of long term dependencies arises from exponentially smaller weights given to long term interactions (involved of many multiplications of the gradient) compared to short-term ones. 

RNN involve the composition of the same function multiple times, once per time step. This composition can result in extremely nonlinear behaviour. Especially if the function composition resembles matrix multiplication. 

If we power up a matrix we power up its eigen values. Thus the matrix either explodes or vanishes. 

This makes sequences of length just 10-20 hard.