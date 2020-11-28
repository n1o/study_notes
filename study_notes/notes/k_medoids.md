
# K-medoids

K-medoids are similar to K-means  but instead of representing each cluster’s centroid by the mean of all data vectors assigned to this cluster, we make each centroid be one of the data vectors themselves. Thus we always deal with integer indexes, rather than data objects. We assign objects to their closest centroids as before. When we update the centroids, we look at each object that belongs to the cluster, and measure the sum of its distances to all the others in the same cluster; we then pick the one which has the smallest such sum:

$$
m_k = \argmin_{i:z_i = k} \sum_{i':z_{i'} = k} d(i,i')
$$