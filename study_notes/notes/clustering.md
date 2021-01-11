# Clustering

I the process of grouping similar objects together.

## Similarity based clustering
The input to the algorithm is an dissimilarity matrix or distance matrix D. Here we an easily include domain specific similarity or kernel function.

## Feature based clustering
The input to the algorithm is an feature matrix or design matrix X. We can apply it to raw, potentially noisy data.


We can have the following output

## Flat clustering
We partition objects into disjoint sets. 

## Hierarchical clustering
We create a nested tree of partitions. Algorithms are deterministic, and do not need to specify the number of clusters. 

Produce clusters that are nested inside each other.
There are 2 main approaches to hierarchical clustering:
### Bottom-up (agglomerative ) clustering
The most similar groups are merged at each step.
### Top-down or divisible clustering. 
Groups are split using various criteria.


>Booth methods take as an input a dissimilarity matrix between the objects, and booth are just heuristics, they do not optimize any well defined function. Hence it is hard to asses the quality of the clustering they produce. 