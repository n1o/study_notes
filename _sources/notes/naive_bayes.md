# Naive Bayes Classifier

Perform classification:
$$p(y=c|x)$$

* $x$ is an vector valued with length $D$


We assume conditional independence between features in the likelihood $p(x|y=c)$

$$p(x| y = c, \theta) = \prod_{j=1}^D p(x_j| y = c, \theta_{jc}) $$

This modeling is called a **naive Bayes classifier (NBC)** (features are rarely independent)

Depending on the types of features we define the likelihood as:
* For continous features as a Gaussian distribution $p(x| y = c, \theta) = \prod_{j=1}^D \mathcal{N}(x_j | \mu_{jc}, \sigma^2_{jc})$.
* Binary features a Bernoulli distribution $p(x|y=c, \theta)=\prod_{j=1}^D Ber(x_j| \mu_{jc})$. Here $\mu_{jc}$ is the probability that feature j occurs in class c. This is also known as the multivariate Bernoulli naive Bayes.
* For categorical features. We assume $p(x| y=c, \theta) = \prod_{j=1}^D Cat(x_j, \mu_{jc})$. Here $\mu_jc$ is a histogram over K possible values for $x_j$ in  class C.

## Maximum Likelihood estimation for NBC

For a single point we have:

$$p(x_i, y_i | \theta) = p(y_i|\pi) \prod_j p(x_{ij}| \theta_j) =\prod_c \pi_c^{I(y_i = c)} \prod_j \prod_c p(x_{ij}| \theta_{jc})^{I(y_i = c)} $$

Hence if we take the log probability:

$$ \log p(D|\theta) = \sum_{c=1}^C N_c \log \pi_c + \sum_{j=1}^D \sum_{c=1}^C \sum_{i :y_i = c} \log p(x_{ij}| \theta_{jc}) $$

Thus we need to find $C$ terms for $\pi_c$ and $CD$ terms for $\theta_{jc}$

The class prior are only the empirical fractions:
$\hat{\pi_c} = \frac{N_c}{N}$ where $N_C$ is the number of examples in class c.

For the likelihood $\theta_{jc}$ depends on the distribution

* **Bernouli**

$$ \hat{\theta}_{jc} = \frac{N_{jc}}{N_C} $$

This algorithm runs in O(CD).


## Bayesian Naive Bayes (Laplace smoothing)
As with all MLE estimates it can easily overfit. A simple solution is to be Bayesian. And for simplicity we use a factored prior:

$$ p(\theta) = p(\pi) \prod_{j=1}^D \prod_{c=1}^C p(\theta_{jc})$$

Where we use a $Dir(\alpha)$ prior for $\pi$ and a $Beta(\beta_0, \beta_1)$ for each $\theta_{jc}$ for the Bernouli likelihood. If we set $\alpha =1, \beta=1$ than it corresponds to **add-one** smooting or **Laplace smoothing**.

The new estimates become:

$$ \bar{\pi}_c = \frac{N_C + \alpha_c}{N + \alpha_0} $$

* **Bernouli**
$$ \bar{\theta}_{jc} = \frac{N_{jc} + \beta_1}{N_c + \beta_0 + \beta_1}$$


where:
* $\alpha_0 = \sum_c \alpha_c$.

## Feature Selection
If we have a lot of features (This is especially true in NLP where presence of each word could represent a feature.) We need a systematic way to filter out some features (This filtering is also known as screening). 

One way is to use Mutial information between featuers and target values, to keep only those features that have the highest [mutual information](./mutual_information.md). It can be obtained as an by-product of fitting an naive Bayes classifier.