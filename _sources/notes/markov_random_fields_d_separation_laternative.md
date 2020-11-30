
# [D-separation](d-separation.md) alternative for Markov Random Fields

We cannot convert DGM to an UGM just by dropping the orientation of the edges. (To give an example we cannot convert a v-structure $A \rightarrow B \leftarrow C$ into $A-B-C$ which states that $A \perp C | B$ but it muss not hold for the first). To avoid inccorect CI statements, we have to add edges between the "unmarried" parents A and C, and then drop the arrows from the edges, forming a fully connected undirected graph. This process is called **normalization**:

Example of normalization:

![](../.images/machine_learning/directed_model_to_markov_random_field.png)

We need to interconnect 2,3 since they have an common child 5, and we interconnect 4,5,6 since they have a common child 7. 

**Downside of normalization** is that we loose some CI information, and therefore we cannot use the normalized UGM to determine the Ci properties of DGM.