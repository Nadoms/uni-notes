# Machine Learning Basics
Neural networks can make predictions on a set amount of input values, unchanging.

## Recurrent Neural Networks
**RNNs** have feedback loops, meaning they can make predictions on variable amounts of input values.
![da2e36f20b5d87506dae1b3371f5580e.png](./da2e36f20b5d87506dae1b3371f5580e.png)
This is useful for sequential data.
The summation in the middle allows all values to influence the output.
RNNs can be unravelled based on how many inputs there are.
![2ee90ca05eb45df5feb050f3c25d1e9b.png](./2ee90ca05eb45df5feb050f3c25d1e9b.png)

### Vanishing / Exploding Gradient Problem
The more we unravel an RNN, the harder it is to train.
This is because the $w_2$ weight's effect exponentially influences the final output as the input gets longer.
The gradient either gets so big that it keeps missing the optimum, or so small that it never reaches the optimum.

## Long Short-Term Memory
LSTMs uses 2 paths in the network, one for long-term memories and one for short term.
![43bcaaf32068c90cf3a82e0eded9afb6.png](./43bcaaf32068c90cf3a82e0eded9afb6.png)
The **Forget Gate** determines what percentage of the long-term memory will the remembered using the Sigmoid activation function.
The **Input Gate** processes an input to update the long-term memory using Sigmoid for % rememberance and Tanh for the value. This is added to the previous LTM.
![25fe673168d1ce1c9cae675ca2a26016.png](./25fe673168d1ce1c9cae675ca2a26016.png)
The **Output Gate** updates the short-term memory using the same process as the input gate. This overwrites the previous short-term memory fully.
![5f8b1e5709cfb4452bad712ced6920bb.png](./5f8b1e5709cfb4452bad712ced6920bb.png)