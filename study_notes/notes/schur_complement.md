# Schur Complement

We can perform elimination by blocs for a matrix M:

$$ M = \begin{bmatrix} A & B \\ C & D \end{bmatrix} $$

We want to get $0$ below A this can be achieved with:

$$\begin{bmatrix} I & 0 \\ -CA^{-1} & I  \end{bmatrix} \begin{bmatrix} A && B \\ C && D  \end{bmatrix} = \begin{bmatrix} A && B \\ 0 && D - CA^{-1}B  \end{bmatrix} $$


Where $D - CA^{-1}B$ is called **Schur complement** also denoted $M / A$
