# Bayesian view of exponential family

The bayesian analysis is considerably simplified if the prior is conjugate to the likelihood.  Informaly we can say that the prior $p(\theta| \tau)$ has the same from as the likelihood $p(D|\theta)$. For this to make sence, we require that the likelihood have finite sufficient statistics, so we can write $p(D|\theta ) = p(s(D)| \theta)$. This suggest that the only family of distributions for which conjugate priors exist is the exponential family.

## Likelihood

The likelihood of the exponential family is given by:


$$p(D| \theta) = [\prod_{i=1}^N h(x_i)] g(\theta)^N \exp( \eta(\theta)^T [ \sum_{i=1}^N s(x_i)]) \\ 
\propto g(\theta)^N \exp (\eta (\theta)^T s_N)$$

* $s_N = \sum_i s(x_i)$ sufficient statistics

In terms of canonical parameters this becomes:

$$p(D| \eta) \propto \exp(N \eta^T \bar{s} - NA(\eta))$$

* $\bar{s} = \frac{1}{N}s_N$

## Prior

The natural conjugate prior has the form:

$$p(\theta| v_0, \eta_0 ) \propto g(\theta) ^{v_0} \exp(\eta (\theta)^T \tau_0)$$


* $\tau_0 = v_0 \bar{\tau_0}$

This separates out the size of the prior pseudo-data $v_0$ from the mean of the sufficient statistics on this pseudo-data $\bar{\tau_0}$. Then the canonical form of the prior becomes:

$$p(\eta| v_0 , \bar{\tau}_0) \propto \exp (v_0 \eta^T \bar{\tau}_0 - v_0 A(\eta))$$

## Posterior

$$p(\phi|D) = p(\theta|  v_N, \tau_N) = p(\theta| v_0 + N, \tau_0 + s_N)$$

So we see that we just update the hyper-parameters by adding. In canonical form this becomes:

$$p(\eta|D) \propto \exp (\eta^T (v_0 \bar{\tau}_0 + N \bar{s}) - (v_0 + N)A(\eta))  \\  
= p(\eta| v_0 + N, \frac{v_0 \bar{\tau}_0 + N\bar{s}}{v_0 + N})$$

Here we se that the posterior hyper-parameters are a convex combination of the prior mean hyper-parameters and the average of the sufficient statistics.