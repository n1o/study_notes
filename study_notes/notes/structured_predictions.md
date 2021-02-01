# Structured predictions

It is an example of [MAP inference on PGM](map_inference_in_graphical_models.md) over a [conditional random field](conditional_random_fields.md)

$$
\arg \max_y \log p(y|x) = \arg \max_y \sum_{c}\theta_c(y_c,x_c)
$$

* $\theta_c(y_c, x_c) = \log \phi_c(y_c, x_c)$ are clique potentials 

An example to structured prediction is handwriting recognition, where we given images $x_i \in [0,1]^{d \times d}$ of characters in the form of pixel matrices. MAP inference is finding most likely word $(y_i)_{i=1}^n$ encoded by the image.