# W3 - The Problem with Learning
Sample data is random, causing all other quantities stemming from it to be random variables with distributions.
If our sample data is not representative of the population, not i.i.d., there is a major risk of overfit.

Risk can be traced to either:
**Random variance** - Caused by random nature of sampling, or overfitting.
**Systematic bias** - Caused by learning algorithm, bias in sampling, underfitting, etc.
![fe2d4d7c6bdb72eb466f00654ffa9f4e.png](./fe2d4d7c6bdb72eb466f00654ffa9f4e.png)

We know the population risk is the unknown average loss:
![0a08b38d78d1d8bdd7c33786492b4336.png](./0a08b38d78d1d8bdd7c33786492b4336.png)
where $f_{S_n}$ is a model trained on a training set.
**Expected risk** - The average population risk over all possible training sets.
![912ebb7fe0f6879a043c34f87811850a.png](./912ebb7fe0f6879a043c34f87811850a.png)
**Expected model** - The prediction obtained by the average of models trained on all possible training sets.
![d66659743c26f1331fe77ac12cd29c6c.png](./d66659743c26f1331fe77ac12cd29c6c.png)
This is what allows us to assess our learning algorithm.

Expected squared loss contains terms for bias and variance:
![56c17dbb9896a6c93e585e52b37d683b.png](./56c17dbb9896a6c93e585e52b37d683b.png)
This is NOT risk. This is the expected loss with respect to changing the model's training set.

And the expected risk for squared loss:
![a805740b0da705e2bbf25664c8f99cd4.png](./a805740b0da705e2bbf25664c8f99cd4.png)
The squared loss of the model, averaged over the true data distribution (risk), averaged over all models trained on the training sets.
![d5a1f36d1eb39e0287da01c19e4df8e7.png](./d5a1f36d1eb39e0287da01c19e4df8e7.png)
This decomposes into terms for noise, bias and variance. Other types of losses decompose into different terms.

When we overfit, the bias decreases, and the variance increases. The goal is to minimise risk from bias and variance.
![1ba94e19eab92cb7da73c5f1cca31cc9.png](./1ba94e19eab92cb7da73c5f1cca31cc9.png)
Noise is the variance in the labels. It is the "base" variance.

In summary, extremely complex models can have high variance in their results when changing out their training sets.
Models which are too basic will have high bias as they are not utilising the input enough regardless of the training set.

Bias-variance decomposition does not hold for every kind of loss, e.g. zero-one loss where you predict yes or no for one value.

For expected risk of cross-entropy loss, written in KL divergences:
![35c6fc76a746fbd2f2a0224d74152e0a.png](./35c6fc76a746fbd2f2a0224d74152e0a.png)