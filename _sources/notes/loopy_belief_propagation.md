# Loopy belief propagation

It is essentially belief propagation, that is applied to graphs, even if they have loops. This method is simple and ofthen works well in practice, outperforming the mean field. 

Unfortunatelly we have **no guarantees** that if it is applied to loopy graphs, that it will converge. 

An popular version of error correcting code called **turbo codes** (But also low density parity check (LDPC)) can be viewed as an instance of BP applied to a certain king od graph.
