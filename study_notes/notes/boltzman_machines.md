# Boltzman machines
* defined over n-dim binary random vector $x \in \{ 0, 1\}^d$
* energy based model of the form 
  $$p(x) = \frac{\exp{-E(x)}}{Z}, E(x) = -x^Tux - bx $$
  * $u$ models weight matrix
  * $b$ vector of biases
* in the general setting, we have a set of n-dim training sample and $p(x)$ describes the joint distribution over the observed variables where we describe interactions only between visible variables using the weight matrix. This however enables us to learn only linear functions
* if we want to model nonlinear relationships we introduce hidden variables 
  $$x = (h,v) \\ 
  E(v,h) = -v^TRv - v^TWh - h^TSh - b^Tc - c^Th
  $$

## Learning 
* MLE based methods
* all versions have intractable partition function, the MLE gradient has to be approximated
* in MLE learning the learning rule is local
  *  weight connecting two uniits depends only on the stats of the two units 