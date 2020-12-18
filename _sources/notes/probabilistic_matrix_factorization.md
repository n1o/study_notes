
# Probabilistic matrix factorization
Is an [colaborative filtering](colaborative_filtering.md) agorithm where we assume that each rating in $R$ are draws from a Gaussian distribution where the mean for 

$$R_{ij} = U_iV_j^T$$

The precision of this distribution $(1/\sigma^2)$ We also put a Gaussian prior with mean 0 on $U$ and $V$ for regularization. This means that each row of U and V are drawn from a Gaussian with mean 0 and where the precision of these gaussian is a multiple of the Identiy matrix. If the precission of these parameters is not to far from 0 that ensures that the latent variables wont grow to much. 

This prevents learning to strong user preferences and item factor compositions from being learned.