# Boosting

The boosting approach uses a generalization of linear predictors to address two major issues.

* the bias-complexity tradeoff

  > the balance between approximation error and estimation error

* the computational complexity of learning

  > When a weak learner can be implemented efficiently, boosting provides a tool for aggregating such weak hypotheses to approximate gradually good predictors for larger, and harder to learn, classes.



The AdaBoost algorithm outputs a hypothesis that is a linear combination of simple hypotheses. AdaBoost enables us to control the tradeoff between the approximation and estimation errors by varying a single parameter.

> AdaBoost stemmed from the theoretical question of whether an efficient weak learner can be "boosted" into an efficient strong learner.





# AdaBoost

An algorithm that has access to a weak learner and finds a hypothesis with a low empirical risk.