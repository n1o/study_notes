# Matrix inversion lemma

The matrix inversion lehma for a patritioned matrix:

$$ M = \begin{bmatrix} E & F \\ G & H \end{bmatrix}
$$ 

The inverse is:

$$ M^{-1} = \begin{bmatrix} (M/H)^{-1} & -(M/H)^{-1} FH^{-1} \\ -H^{-1}G(M/H)^{-1} & H^{-1} + H^{-1}G(M/H)^{-1}FH^{-1} \end{bmatrix}$$

* $M/H = E - FH^{-1} G$ is the [Schur Complement](schur_complement.md) of M with respect to H

We can express the inverse only in terms of $E$ and $M/E$

$$ M^{-1} = \begin{bmatrix} E^{-1} + E^{-1}F(M/E)^{-1}GE^{-1} & -E^{-1}F(M/E)^{-1} \\ -(M/E)^{-1}GE^{-1} & (M/E)^{-1} \end{bmatrix} $$

* $M/E = H - GE^{-1}F$ is the Schur Complement of M with respect to E

From these we can derive the **Matrix inversion lemma** or **Sherman-Morrision-Woodbury formular**:

$$1.(E - FH^{-1}G)^{-1} = E^{-1} + E^{-1}F(H-GE^{-1}F)^{-1}GE^{-1}$$
$$2.(E - FH^{-1}G)^{-1}FH^{-1} = E^{-1}F(H - GE^{-1}F)^{-1}$$

And the **Matrix determinant lemma**

$$3. |E - FH^{-1}G| = |H-GE^{-1}F||H^{-1}||E|$$

## Application

We can perform an symmetric rank one update to an inverse matrix:

$H = -1; F = u; G = v^T$ then:

$$
(E + uv^T)^{-1} = E^{-1} + E^{-1}u(-1 - v^TE^{-1}u)^{-1} v^TE^{-1} \\ = E^{-1} - \frac{E^{-1} uv^T E^{-1}}{1 + v^TE^{-1}u}
$$

## Proof:
![](../.images/matrix_inversion_lehma_part_1.png)

![](../.images/matrix_inversion_lehma_part_2.jpg)