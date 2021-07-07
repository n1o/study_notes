# Diffusion models

* diffusion models are trained by progressively adding more and more Gaussian noise to images form the training set and learning to "denoise" the noisy image. 
* if we add enough noise removes all of the information encapsulated in an image, and if the model can reverse the process entirely, we can than generate images from white noise
* diffusion models attempt to match the gradient of the data distribution at all points in the space using denoising score matching, which minimizes the Fisher divergence between the model and the real data distribution, an if two distribution have the same gradient everywhere than they have the same probability distribution