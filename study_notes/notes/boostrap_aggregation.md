# Bootstrap aggregation (Bagging)

The idea behind bootstrap aggregation is to combine multiple models to reduce error. If the errors of the models are uncorrelated than there will be an significant reduction, otherwise the ensemble will perform at least as well as any of its members.

In bagging we construct k different k different datasets by drawing with replacement from the original dataset (on average 2/3 of the original dataset are found in the new dataset), than we train k models.