# Teacher Forcing

During the training the model receives the ground truth output $y^{(t)}$ as an input at $t+1$.

![](../.images/machine_learning/teacher_forcing.png)

During test time we propagate only the predictions made form the hidden units.