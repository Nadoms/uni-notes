# W5 - Deep Learning For NLP

## Deep Learning
DL emphasises networks with higher numbers of layers compared to NN.
DL refers to building end-to-end NN systems.
DL tasks in NLP:
- Sequence distribution
- Sequence classification
- Sequence labelling
- Seq2seq learning

## Basic NN Architectures
Activation functions:
![aa817ce30bdb0c6635c04b9aca3444dd.png](./aa817ce30bdb0c6635c04b9aca3444dd.png)

**Single neuron** - Multiple inputs in a layer and one output y.
**Single layer perceptron** - One input layer and one output layer.
**Multilayer perceptron** - One input layer, multiple hidden layers and one output layer.
![283917fb54726cc3a7f86ad47de1b65b.png](./283917fb54726cc3a7f86ad47de1b65b.png)

## RNN Architectures
RNNs are used to capture data patterns and encode information in sequential data.
![404705f684c4d56c3e1cd48ac5551b56.png](./404705f684c4d56c3e1cd48ac5551b56.png)

**Vanilla RNN** - Uses standard neuron operation to compute the hidden representation vector.
![af6e4ddd844d6ad28bcdbb721f969936.png](./af6e4ddd844d6ad28bcdbb721f969936.png)
This can result in **vanishing gradient** issues with the training process, causing **dependency loss** between the current and long-distance past states.
![42768f901523fa5052be96d15d9977a1.png](./42768f901523fa5052be96d15d9977a1.png)
This can be modified to fix the vanishing gradient issue.
Long short-term memory:
![bdb7890fe3070ec5d34042934157ae18.png](./bdb7890fe3070ec5d34042934157ae18.png)
Gated recurrent units:
![486f5185875affc45f7dcb96e032321e.png](./486f5185875affc45f7dcb96e032321e.png)

## Advanced RNN Architectures
**Bi-directional RNN** - Consider both left and right context. "The movie is _terribly_ exciting."
Concatenate hidden representations computed by two RNNs using the original and reversed sequences as input.

**Multilayer RNN** - Stack multiple layers of RNNs. The output of one hidden layer is used as the input for the next hidden layer.