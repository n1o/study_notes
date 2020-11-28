#  Rules Determinants

1. Determinant of an $n \times n$ identity matrix is 1. Since the determinant is the product of pivots. In the identity matrix we have only 1's.

2. Determinant changes sign when two rows are exchanged.

$$\begin{vmatrix}c & d \\ a & b \end{vmatrix} = - \begin{vmatrix}a & b \\ c & d \end{vmatrix}$$

3. Determinants are linear functions of each row separately:
If the first row is multiplied by $t$, the determinant is multiplied by $t$. If first rows are added then determinants are added. This rule apply when other rows do not change!
$$\begin{vmatrix}ta & tb \\ c & d\end{vmatrix} = t \begin{vmatrix}a & b \\ c & d \end{vmatrix}$$


4. If at least two rows of $A$ are equal, then $det(A) = 0$
We go out from rule 2. If we would change 2 identical rows then $A$ does not change. But row exchanges should swap the signs.

5. Subtracting a multiple of one row from another row leaves $det(A)$ unchanged. 
   $$\begin{vmatrix}a & b \\ c - la & d -lb \end{vmatrix} = \begin{vmatrix}a & b \\ c & d \end{vmatrix}$$

6. Matrix with a row of zeros has det $A$ 
   $$\begin{vmatrix}0 & 0 \\c &d \end{vmatrix} = 0$$
   
   And since we can swap rows the zero row can be anywhere.

7. If A is triangular then the determinant is the product of diagonal entries
   $$\begin{vmatrix}a & b \\0 &d \end{vmatrix} = ad, \space \begin{vmatrix}a & 0 \\c &d \end{vmatrix} = ad$$


8. If A is singular then $det(A) = 0$. If as is invertible then $det(A) \ne 0$


9. The value $det(AB) = det(A)det(B)$

$$\begin{vmatrix}a & b \\c &d \end{vmatrix} \begin{vmatrix}p & q \\r &s \end{vmatrix} = \begin{vmatrix}ap + br & aq + bs \\ cp + dr & cq + ds \end{vmatrix}$$


10.  The transpose $A^T$ ha sthe same determinant as A 
        $$\begin{vmatrix}a & b \\c &d \end{vmatrix} = \begin{vmatrix}a & c \\b &d \end{vmatrix}$$

