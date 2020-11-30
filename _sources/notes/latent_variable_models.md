# Latent Variable Models

Here we assume that observed variables are correlated because they arrise form a hidden common "cause". Model with hidden variables are known as **latent variable models (LVM)**.

In general LVM are harder to fit, than models with no latent variables.  However they have significant advantages:

1. They often have fewer parameters than models that directly represent correlation in the visible space
2. The hidden variables in an LVMM can serve as **bottleneck**, which computes a copressed representation of the data. 

Since latent variables can be used to explain the data generation process in general we are interested to find out something about $p(z| x)$. To find out something about our hidden variables given the observed ones. 