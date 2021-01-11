# Kalman smoothing algorithm
[Kalman filtering](kalman_filtering.md) updates the belief as the data arrives. 

**Kalman smoothing** computes the posterior:

$$p(z_t| y_{1:t})$$

after we observed all the data, this reduces the posterior uncertainty significantly.

It is analogous to the forward-backward algorithm in [HMM](hidden_markov_models.md), with some small differences.