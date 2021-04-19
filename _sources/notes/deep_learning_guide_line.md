# Deep learning guide line

1. If the input vector is fixed use an fully connected NN
2. If we have a topological structure than CNN
3. If there is a sequence than a gated recurrent net
4. Batch normalization can have a drastic effect on optimization especially for CNN and networks with sigmoidal nonlinearities.
5. We can ommit dropout if we use batch normalization

## Enough data
If we the training error is high than there is no reason to collect more data since we should improve the model.

We should gather more data only when the validation set is much worse than the test set. And we already regularizing have dropout and have tuned hyper parameters.