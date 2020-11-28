# Dirichlet Compound Multinomial

$$p(x_i | y_i =c ,\alpha ) = \int Mu(x_i| N_i, \theta_c) Dir(\theta_c| \alpha_c) d\theta_c = \frac{N_i!}{\prod_{i=1}^D x_{ij}!} \frac{B(x_i + \alpha_c)}{B(\alpha)}$$

If we would compare the classical multinomial with Dirichlet compound multinomial then:

* Multinomial model is like drawing a ball fom an urn with K collors ball, recording that collor and then replacing it. 
* DMC corresponds to drawing a ball, recording its collor and replacing it with one additional copy. (**Polya urn**)

# Usage
Some NLP, it can be used to capture burstiness phenomenon, which is when we observer an word it will make the probability of observing it again more likely.  
