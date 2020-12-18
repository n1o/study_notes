# Collaborative Filtering
It is an approach that uses 2 sources of data. First is the between user similarity and the second is the between item similarity.

Lets image that we want to recommend M items to a set of N users, where a user if owns an item it will give it an rating $R_{ij} = \text{rating of ith user of the jth item}$, or $R_{ij} = 0$ if the user has not rated the item. This gives an rise to a an $N \times M$ matrix of ratings. If we have a large number of items and users this matrix will be sparse. Now we assume that each user and each user has an latent vector of dimennsion $D$. For users this vector describes his preferences, and for items this vector discribes its profile.

Now our goal si to find an $U = N \times D$ matrix that describes the preferences of each user and an $V = M \times D$ matrix that describes each item in terms of its latent variable. 

Now if we take the product of $U \cdot V$ now we get an approximation how a user would reate an item he has not seen. 

## Algorithms

* [Probabilistic matrix factorization](probabilistic_matrix_factorization.md)