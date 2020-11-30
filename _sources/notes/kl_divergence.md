# Kullback-Lieber divergence (KL)

Also known as **Relative** entropy. 

We can view it as a measure of dissimilarity of two probability distributions $p$ and $q$. 

$$ KL(p||q) \triangleq \sum_{k=1}^K p_k \log \frac{p_k}{q_k}$$

Where we can replace the sum for an itegral from pdfs.

We can expand this into:
$$ KL(p||q) \triangleq \sum_k p_k \log p_k - \sum_k p_k \log q_k = -H(p) + H(p,q)$$

Where:
* $H(p,q)$ is the **cross entropy** $H(p,q) \triangleq -\sum_k p_k \log q_k$. 

Here cross entropy is the average number of bits needed to encode data coming from a source with distribution p where we use model q to define our codebook.

From this we can express KL divergence as the average number of extra bits needed to encode the data, due to the fact that we use distribution q to encode the data instead of the true distribution p.

## Properties

1. Cannot be negative. 
2. Zero only if $p=q$


1. and 2. form the *information inequality* or *Gibbs inequality*.
## Profs

**Non Negative**

![Non negativity proof](../.images/machine_learning/kl_divergence_non_negative_proof.jpg)