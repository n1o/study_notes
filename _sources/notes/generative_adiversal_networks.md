# Generative Adiversal Networks (GAN)

* game theory where a generator competes against an adversary
* generator directly produces samples $x=g(z;\theta)$
* discriminator attempts to distinguish between samples drawn from training data and samples drawn from the generator, it emits the probability $d(x;\theta)$ that x is real 
* we can express this as a zero-sum game
  * $v(\theta^{(k)}, \theta^{(d)})$ determines the payoff of the discriminator the generator receives $-v$ as its own payment 
  * each player tries to maximize its payoff 
    $$
    g^* = \arg \min_g \max_d v(g,d)
    $$
  * the default choice for $v$ is 
    $$
    v(\theta^{(k)}, \theta^{(d)} = E_{x \sim p_{\text{data}}} \log d(x) + E_{x \sim p_{model}} \log(1 - d(x)) 
    $$
* at convergence the discriminator is unable to distinguish real from the fake thus emits probability 1/2 every where 