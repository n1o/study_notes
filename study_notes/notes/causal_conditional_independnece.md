# [Causal graphical model](graphical_causal_models.md) conditional independence
* we build on the motion of [d-separation](d-separation.md) in [directed graphical models](directed_graphical_models.md)

## X -> Y -> Z

Causal Knowledge -> Solve Problems -> Job promotion

* the general idea that having higher causal knowledge leads to better problem solving and have a higher probability of job promotion
* if we condition on problem solving skill, than causal knowledge becomes independent from job promotion. 
* by knowing one problem solving skill, knowing also causal knowledge leads to no additional information about job promotion

## X <- Y -> Z (Collider)

Causal inference <- Stat -> Machine learning

* if somebody is good in causal inference than he is probably also good in stats and good in ML
* if we condition on stats, we know everything we need to infer ML or Causal skill, thus also knowing either wont tell us anything new 

## X -> Y <- Z (V Structure)

stats -> job promotion <- flatter
* if we know how good we are at stats, but we do not know about promotion we cannot tell anything about flatter skills
* once we know about promotion (if somebody got it) and his stats knowledge is poor than we know that he has good flatter skills
* this is known as explaining away, since knowing the cause already explains the effect, making the other cause less likely

