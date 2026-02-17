# W2 - Probability for Learning
**Bernoulli distribution** - A binary distribution with one input, $\mu$, the probability of one output.
**Gaussian distribution** - A normal distribution with two inputs, $\mu, \sigma$, the mean and std.

With noise distributions in real life, we can fit a Gaussian to them by maximising likelihood.
![4a85c5e75feed16c67ea0505f0c9bed3.png](./4a85c5e75feed16c67ea0505f0c9bed3.png)
A likelihood may be bigger than 1. They are not probabilities.
Objective: find $\mu$ and  $\sigma$ should that the likelihood product of sample values is maximal.
![7753671558bf9a83cd0231c369a54d29.png](./7753671558bf9a83cd0231c369a54d29.png)
This causes likelihoods to be extremely small, with potential underflow. Can instead minimise **negative log likelihood**:
![1849e9e6657f4a3f77c8642b954f834f.png](./1849e9e6657f4a3f77c8642b954f834f.png)
This simplifies to the squared loss equation; a consequence of assuming Gaussian noise.
The model can be trained by minimising the empirical average of the loss, and predict the mean.
Similarly, cross-entropy loss comes from taking negative log likelihood of a Bernoulli.

**Split-Gaussian** - Different std for left / right of the mode, $m$.
![47d34c44410ef34477820f896418eaa6.png](./47d34c44410ef34477820f896418eaa6.png)

**Excess risk** - The difference between the model distribution risk and the true distribution risk.
![5b29e7121f87e8e4ed09fe3b22310ae2.png](./5b29e7121f87e8e4ed09fe3b22310ae2.png)
This is the **Kullback-Leibler divergence**.
![80eb8c1801352fd8acd7dcc9c08dea3c.png](./80eb8c1801352fd8acd7dcc9c08dea3c.png)