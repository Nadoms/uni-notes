start of file is on pc

**Uniform deviation bound** - Setting $\epsilon$ forms an epsilon-tube around the population risk.
![6a4069e1745f46677cfbe2aeb638882a.png](./6a4069e1745f46677cfbe2aeb638882a.png)
Having $\hat{R}$ within this tube is what we want.

However we aren't just varying the data in training, we are searching over the function class.
Applying the bound for all functions in the class, not just one:
![37ae6452fab77a599915984f7314f971.png](./37ae6452fab77a599915984f7314f971.png)
$sup$ is which function does the worst case scenario, i.e. the maximum of $|R-\hat{R}|$ across all functions in the class.
$|\mathcal{F}|$ is the size of our function class.
![8f0f791a54cb0c5470b9e7bb39043fe7.png](./8f0f791a54cb0c5470b9e7bb39043fe7.png)

This can be rearranged for n, to be less than $\delta$:
![5c1fbcae8fc52509ab885a71cb4ee3c0.png](./5c1fbcae8fc52509ab885a71cb4ee3c0.png)
Meaning we can choose how close we want to be to population risk, how big our function class is, and the probability of the bad event to obtain a minimum sample count.

As the model class size increases, the data requirement does not increase nearly as much.
![e2f3f4c58e7e611d0de9069be1c44603.png](./e2f3f4c58e7e611d0de9069be1c44603.png)

As the deviation allowed decreases, the sample requirement is inversely quadratic and explodes upwards.
![e339cb24d8faf14853981f757fc26871.png](./e339cb24d8faf14853981f757fc26871.png)

Its only really an issue when our empirical risk predicts a lower risk than the population risk.
By taking only one of the two tails:
![faebf26bb2137a232a9fb08e7953c59d.png](./faebf26bb2137a232a9fb08e7953c59d.png)

Now we can bound the population risk with regards to the empirical risk:
![9e03762d330ea8fd2b9f890a26f79306.png](./9e03762d330ea8fd2b9f890a26f79306.png)
