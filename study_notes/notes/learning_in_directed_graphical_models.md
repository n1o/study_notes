# Learning

In the graphical models literature, it is common to distinguish between [inference](inference_in_directed_graphical_models.md) and learning. Inference means computing (functions of) $p(x_h|x_v,\theta)$, where $v$ are the visible nodes, $h$ are the hidden nodes, and $\theta$ are the parameters of the model, assumed to be known. Learning ususaly means computing the MAP estimate of the parameters given data:


$$\hat{\theta} = \arg \max_{\theta} \sum_{i=1}^N \log p(x_{i,v}| \theta) + \log p(\theta)$$

* $x_{i,v}$ are visible variables in case
* if $p(\theta)\propto 1$ this reduces to MLE


If we adopt a Bayesian view, the parameters are unknown variables and should also be inferred. Thus to a Bayesian, there is no distinction between inference and learning. In fact, we can just add the parameters as nodes to the graph, condition on D, and then infer the values of all the nodes.

## [Plate notatioin](plate_notation.md)

Is an more compact graphical representation for directed graphical models.

## Learning from complete data

In the case that all the variables are fully observed in each case and there are no hidden variables, we say that the data is **complete**. For a DGM with complete data the likelihood is given by:

$$ p(D|\theta) = \prod_{i=1}^Np(x_i|\theta) = \prod_{i=1}^N\prod_{t=1}^V p(x_{it}| x_{i, pa(t), \theta_t}) = \prod_{t=1}^Vp(D_t|\theta_t) $$

* $D_t$ is the data associated with node t (its parents).

There is a product term per CPD, we can say that the likelihood **decomposes** accordingly to the graph structure. 

If the prior factors as well:

$$p(\theta) = \prod_{t=1}^V p(\theta_t)$$

Then crealy the posterior aslo factorizes:

$$p(\theta|D) \propto p(D|\theta)p(\theta) = \prod_{t=1}^V  p(D_t| \theta_t)p(\theta_t)$$

Hence we can factorize the posteror of each CPD independently. Thus factorized priors plus factorized likelihood implies factorized posterior.

Hence if we choose our likelihood and prior functions to be conjugate, the posterior will be the same from as the prior.
