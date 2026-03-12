# W1 - Foundations of Supervised Learning
Supervised learning pipeline:
![7c5c0a18b52c84cef387a022a9583c96.png](./7c5c0a18b52c84cef387a022a9583c96.png)

### Data
Sample data is **independent and identically distributed** across an unknown probability distribution.
Training dataset $S$:
![863f45502956ad2ffb5aa558236843f4.png](./863f45502956ad2ffb5aa558236843f4.png)

### Model
A model is simply a mathematical function $y = f(x, w)$
It may function on something like **logistic regression**, outputting a value between 0 and 1 for any input with a sigmoid.

### Loss
A loss function defines how a model misperforms during testing.
Minimising mean squared loss, for regression tasks:
![489e2f30f0666c6a40417f453fc7eb32.png](./489e2f30f0666c6a40417f453fc7eb32.png)
Classification can be performed using probabilities for each class, over a simplex:
![036c05fa13c41e960b41cbd45de33206.png](./036c05fa13c41e960b41cbd45de33206.png)
This allows us to continue calculating loss normally.
Binary cross-entropy can be used for binary classification problems instead.

### Algorithm
Learning algorithms are usually iterative, taking a model from point A to point B in the **Hypothesis Space**:
![25f441cde0033ed87c4470a8bb01d2b0.png](./25f441cde0033ed87c4470a8bb01d2b0.png)
<<<<<<< Updated upstream
**Bayes model, $y^*$** - The theoretical best possible predictor, minimising population risk.
**Empirical risk, $\hat{R}$** - The average loss over a set of examples.
**Population risk, $R$** - The expected loss with respect to the unknown, true probability distribution. The "true" risk.
**Expected label** - The expected value of a probability distribution.

**Theorem**: The Bayes model under squared loss is equal to the expected label.
=======

### Underfitting & Overfitting
We already know about this. Test / training loss will typically follow this shape when starting to overfit:
![7482a2f28b2f29b09d4f32b15eb03682.png](./7482a2f28b2f29b09d4f32b15eb03682.png)

### Risk
**Empirical risk, $\hat{R}$** - The average loss over a set of examples.
**Population risk, $R$** - The expected loss with respect to the unknown, true probability distribution. The "true" risk.
**Generalisation gap** - The difference between the two. $\hat{R} - R$

**Bayes model** - The theoretical best possible predictor, minimising population risk.
**Expected label** - The Bayes model under squared loss.
**Bayes risk** - Simply the risk value of the Bayes model.
>>>>>>> Stashed changes
