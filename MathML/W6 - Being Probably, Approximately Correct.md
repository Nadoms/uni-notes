# W6 - Being Probably, Approximately Correct
The optimal empirical risk $f_{erm}$ may differ from the optimal population risk $f_*$, varying the model type.
The difference between these is the estimation error. 
![f2fe9624bb24660d93923e08d4af1e61.png](./f2fe9624bb24660d93923e08d4af1e61.png)

We want to reduce the estimation error arising from the data, by minimising this probability:
![cc3285c4f6ae434a2f2feeeba28e887f.png](./cc3285c4f6ae434a2f2feeeba28e887f.png)
We need to figure out how much data is needed to satisfy this condition.

**Hoeffding's inequality** defines what $\delta$ should be based on the value of $\epsilon$.
![e74a0175cc9d076f3fe899971a6e29cc.png](./e74a0175cc9d076f3fe899971a6e29cc.png)
The upper bound gets exponentially smaller as the amount of data increases.

This can be perfectly mapped onto learning, by looking at a model trained on datasets of size $n$ instead of $n$ samples of individual data points.
![0b1d122b1dd9ff5bb4134387837fad88.png](./0b1d122b1dd9ff5bb4134387837fad88.png)
