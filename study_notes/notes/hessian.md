# Hessian

Matrix that contains all the second partial derivatives of a function.

$$
\nabla^2 f(x)_{ij} = \frac{\partial ^2 f(x)}{\partial x_i \partial x_j}
$$

## Properties
If the Hessian is positive definite than we have a local minima, if it is negative definite it is a local maxima, otherwise it is a saddle point.

## Conditioning number
In multiple dimensions there is a different second derivative for each direction at any given point. The conditioning number of the hessian measures how much the second derivatives differ from each other.

If the conditioning number of the hessian is low, gradient descent performs poorly. This is because in one dimension the derivative increases rapidly while in other directions it increases slowly.

An example, lets assumme the conditioning number is 5, that means that the direction of most curvature has 5 times more curvature than the direction of the least curvature.