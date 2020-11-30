# Kernels for document comparison

We compare two "term frequency inverse document frequency" vectors. 

1. Term ferquency
$$
    tf(x_{ij}) = \log (1 + x_{ij})
$$
By log transforming we reduce the impact of words that are frequent within one document.
2. Inverse document ferquency

$$
idf(j) = \log \frac{N}{1 + \sum_{i=1}^N I(x_{ij} > 0)}
$$
* $N$ total number of documents
* denominator counts the number of documents contianing term j

If we put it togeter we get:

$$
\text{tf-idf}(x_i) = [tf(x_{}ij) \times idf(j) ]_{j=1}^V
$$

Now we can use this to measure document similarity by using it inside cosine similarity:

$$
\mathcal{k}(x_i, x_{i'}) = \frac{\phi(x_i)^T\phi(x_{i'}) }{||\phi(x_i) ||_2 ||\phi(x_{i'})||_2}
$$