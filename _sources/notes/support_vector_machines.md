# Support vector machines (SVM)
In general we have the following model:

$$
    J(w, \lambda) = \sum_{i=1}^N L(y_i, \hat{y}) + \lambda ||w||^2
$$

If we use quadratic loss we get ridge regression if we use log loss we get logistic regression. Unfortunatelly those do not yeild sparse solution. If we would use a loss function that ensures sparsity, such that the predictions would depend only on a subset of the training data, known as **support vectors**.

**Support vetor machines** are the combination of kernel trick and the modified loss function that encourages sparsity. 

SVMs are very unnatural from a probabilistic point of view. First, they encode sparsity in the loss function rather than the prior. Second, they encode kernels by using an algorithmic trick, rather than being an explicit part of the model. Finally, SVMs do not result in probabilistic outputs, which causes various difficulties, especially in the multi-class classification setting.

## Regression
We can use SVMs for [regression](svm_regression.md)

## Classification
In general we perform binary [clasification](svm_classification.md). Multiclass is done using **one-vs-rest** classifier. But here we have to tackle class imbalance.