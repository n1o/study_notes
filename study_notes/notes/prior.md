# Priors

Choosing a prior is important, and we can argue that nobody starts with a blank slate or nobody is a tabula rasa.

## [Uninformative priors](uninformative_prior.md)
In case if we do not have a strong belief about our prior, we should let the data speak for itself.

## Transition invariant prior
It is a prior that statisfy the property that the mass between $[A,B]$ is the same as the mass between $[A -c, B-c]$

## Scale invariant prior
Is a prior that statisfy the property that the mass between  $[A,B]$ is the same as the mass between $[A/c, B/c]$


## Robus priors
In case we are not confident in our priors we want to be sure that it will do not have an undue influence on the result. So we choose a prior that has heavy tails, which avoids forcing things to be to close to the prior mean. Unfortunately computing robust priors is expensive.


## Mixture of conjugate priors
Conugate priors by itself are not robust, but are easy to compute. But if we take a mixture of conjugate priors we get a nice ballance. Our prior will be more robust and still easy to compute.


$$p(\theta) = \sum_k p(z = k) p(\theta| z = k) $$

Example:

$p(\theta) = 0.5 \cdot Beta(\theta| 20, 20) + 0.5 \cdot Beta(\theta| 30,10)$

This is a prior of a somewhat fair coin, but we also think it can be biased towards heads.


To compute the posterior is now given as:

$$p(Z = k |D) = \frac{p(Z = k) p(D| Z = k)}{\sum_{k'} p(Z = k') p(D| Z = k')}$$
