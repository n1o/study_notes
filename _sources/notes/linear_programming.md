# Linear programming 

It is an optimization problem in which the objective function and constraints are linear. It has huge application in multiple fields. Many problems are nonlinear but can be well approximated by linear programs.

## Standard Form

$$
\min_x c^Tx \\
\text{ s.t: } \\
Ax \le b \\
x \ge 0
$$

* $x \in R^n$
## Integer linear programming (ILP)
Here we require that $x \in \{0,1\}^2$. In general this is NP hard and we use heuristics.

### Rounding
Here we relax $x \in \{ 0,1\}^n$ to $0 \le x \le 1$ solve a LP and than round to the closes integer value. It works well in practice and has theoretical guarantees for some classes of ILP.