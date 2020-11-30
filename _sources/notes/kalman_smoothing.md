# Kalman smoothing algorithm

[Kalman filtering](kalman_filtering.md) works online, where it sequentially computes $p(z_t| y_{1:t})​$ for each t. However in offline setting we can compute $p(z_t|y_{1:T})​$ afther all the data has arrived. In this setting the posterior uncertainity will be significantly reduced. 

The algorithm is known as **Kalman smoothing** and it is analogous to the forward-backward algorithm in [HMM](hidden_markov_models.md), with some small differences.