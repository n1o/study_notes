# Bias Variance tradeoff

If the hypothesis space of our model is very limited, it might not well represent the true distribution $p*$, even if we observe unlimited data. This type of limitation is called **bias**, as the learning is limited how close it can approximate the target distribution.

If the hypothesis space of our model is highly expressive, we might represent the data better. However, when we have small amount of data, multiple models can fit well (better than the true model), but a small perturbation on D will result in very different estimates. This limitation is called **variance**.

The challenge of bias-variance trade off is to select the right hypothesis class. Thus finding an model that is rich enough to be useful, yet not too complex to overfit the training data.