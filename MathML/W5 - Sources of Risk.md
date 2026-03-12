# W5 - Sources of Risk
## Causes of Risk
Overall risk is composed of:
- Algorithm / compute limitations
- Data limitations
- Model limitations

**Empirical risk minimiser ($f_{erm}$)** - Given a function class, and dataset, this model minimises the empirical risk.

**Best-in-family model ($f^*$)** - The best model within the chosen function class, found with infinite data and a perfect learning algorithm.

**Bayes model ($y^*$)** - The model we would achieve with infinite data, a perfect learning process, and infinite model capacity.

![a54371ea440a08585838ab481f4a13ad.png](./a54371ea440a08585838ab481f4a13ad.png)

The risk improvements that each of these models compose the **excess risk**.
![6021538a7c99d109c0d6dfd4e49b8b10.png](./6021538a7c99d109c0d6dfd4e49b8b10.png)

**Optimisation error** - There is a computational or algorithmic limitation, preventing us from getting the perfect model(s) given our data.

**Estimation error** - There is a sample limitation, preventing us from minimising population risk within our model family.

**Approximation error** - There is a structural limitation, as we are confined to a function class which the Bayes model may not be in.

## Expanding the Function Class
By expanding the function class, we give space for the model to become more complex (and potentially overfit).
The approximation error can only ever decrease as the class expands (including previous models), as the best-in-family model can only get better.
![ab1704cac37a5c70403f95f0997077b9.png](./ab1704cac37a5c70403f95f0997077b9.png)
However, estimation error will become more delicate, generally increasing, with the more ERMs there are capturing noise.
![be9feffedb48def3d081c441586bd6b3.png](./be9feffedb48def3d081c441586bd6b3.png)
Variance ties in with optimisation and part of estimation, bias ties in with approximation and part of estimation too.

## Double Descent
**Over-parameterisation** - There are more model parameters than training examples.
When a model is over-parameterised, its risk can undergo **double descent**.
![60f2b536cd6161f3006266666dec0d81.png](./60f2b536cd6161f3006266666dec0d81.png)

**Implicit regularisation** - In over-parameterised scenarios, stochastic gradient descent prefers smaller weights, meaning some ERMs are preferred over others.
![8cd5caa173deb37f763091f424dccf01.png](./8cd5caa173deb37f763091f424dccf01.png)