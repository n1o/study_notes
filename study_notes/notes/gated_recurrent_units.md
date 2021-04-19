# Gated Recurrent Units
IT contains a single gating unit that controls the forgetting factor and the decision to update the state unit.

$$
h_i^{(t)} = u_i^{(t-1)}h_i^{(t-1)} + (1+u_i^{(t)})\sigma (b_i + \sum_j U_{i,j}x_j^{(t)} + \sum_j W_{i,j}r_j^{(t-1)}h_j^{(t-1)} )
$$

* $u$ is the update gate
* $r$ is the reset gate

$$
u_i^{(t)} = \sigma(b_i^u + \sum_j U^u_{i,j}x_j^{(t)} + \sum_j W_{i,j}^ur_j^{(t-1)}h_j^{(t-1)} ) \\
r_i^{(t)} = \sigma(b_i^r + \sum_j U^r_{i,j}x_j^{(t)} + \sum_j W_{i,j}^rr_j^{(t-1)}h_j^{(t-1)} )
$$

Reset an update gates can individually "ingore" parts of the sate vector.