# W4 - Combining Multiple Models
Complexity is not just about the number of parameters within a model.
Committee of models shouldn't be identical, or non-sensically different.

## Bootstrap Aggregation
**Bootstrapping** - Given a set $S$ of samples, a new set $S'$ is created, sampled uniformly from the original set $S$.
![23938362e86ccffea28b9a24e51e7ff6.png](./23938362e86ccffea28b9a24e51e7ff6.png)

**Bagging** - Bootstrap aggregating, where each bootstrapped sample will be used in a new model.
![2975b6d8e18ec8fb6f0746972cf3faa2.png](./2975b6d8e18ec8fb6f0746972cf3faa2.png)

Probability of any one example being included in a bootstrap is ~63%, but this is OK with more bootstraps and models.
![3a3fcc34730a1560062a47a9eef753bf.png](./3a3fcc34730a1560062a47a9eef753bf.png)
![a0bf87e7d5ba112da541b252a034d5eb.png](./a0bf87e7d5ba112da541b252a034d5eb.png)

### Ambiguity Decomposition
**Ensemble combiner** - How to use the results of many different models as one.
When defining the ensemble combiner as taking the mean of the models, the **ensemble loss** breaks down:
![6f4e0fbaf4c21bba075324ceb70938dc.png](./6f4e0fbaf4c21bba075324ceb70938dc.png)
The loss of the ensemble is less than the mean loss of its parts, precisely by the ambiguity.
**Ambguity** - The mean loss between a model prediction and ensemble prediction. This gives us the reduction in loss.

For cross-entropy, and combining the models as a geometric mean, instead of squared loss and arithmetic mean:
![939076bb15925390dc8346585a55f49e.png](./939076bb15925390dc8346585a55f49e.png)

The ensemble population risk is always better than the average of the models' population risk.
![3657ea11a468698a212f650682f757a4.png](./3657ea11a468698a212f650682f757a4.png)

### Linking Back To Variance
The ensemble approach attempts to reduce variance by averaging models over training sets.

If a set of random variables $f_1(x),...,f_m(x)$ are uncorrelated:
![a4a5566d8b2fcd2058ec336169c412e8.png](./a4a5566d8b2fcd2058ec336169c412e8.png)
The variance of the average variable is less than the average variance of the random variables.
This maps 1-1 onto onto model variance.

![64eb691f063373164d91210e79511430.png](./64eb691f063373164d91210e79511430.png)

For an ensemble of models, we have to consider **diversity** in a three-way tradeoff.
![a4186026c1e328e5f432796a7591f2cd.png](./a4186026c1e328e5f432796a7591f2cd.png)

So for an ensemble of models, the expected risk is:
![272f60b21bae955db759c92130e2842d.png](./272f60b21bae955db759c92130e2842d.png)
Where:
![14a13a6c5dc10120872b50e2f44b76dd.png](./14a13a6c5dc10120872b50e2f44b76dd.png)
Bias is the average bias of each model.
Variance is the average variance of each model.
Diversity is the expected ambiguity term.

Using zero-one loss, we can do binomial stuff to find committee error with majority voting:
![7831da6bc5c3f22732e2537f289f2ca3.png](./7831da6bc5c3f22732e2537f289f2ca3.png)
![f2f5f74b79ab46a1bb7df708f8fc47d5.png](./f2f5f74b79ab46a1bb7df708f8fc47d5.png)
By increasing the number of models, a 30% error rate can reduce to a 2% error rate in this case.