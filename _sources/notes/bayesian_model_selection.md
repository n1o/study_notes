# Bayesian model selection
We need to evaluating which model is better. We can either perform K-fold cross validation, which can be inefficient an more efficient ways is to compute the posterior over models:

$$p(m|D) = \frac{p(D|m)p(m)}{\sum_{m \in M}p(m,D)} $$

Now to find the most probable model we can compute:
$$\hat{m} =  \arg \max p(m|D) $$

If use an uniform prior over $p(m)$ than the upper equations reduces to maximizing:

$$p(D|m) = \int p(D| \theta)p(\theta|m)d\theta $$

This quantity is called the [**marginal likelihood**, **integrated likelihood**, or **evidence**](computing_evidence.md) for model m.

Finding the marginal likelihood involves interating over the all the models and [prevets from overfitting](bayesian_occams_razor.md).


If we manage to find the marginal likelihood we may compute [bayes factor](bayes_factor.md) to compare two models.