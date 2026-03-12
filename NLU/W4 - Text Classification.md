# W4 - Text Classification
**Naive Bayes** - Assuming data is independent, and modelling based on conditional probabilities of data and their labels.
There are two event models:
- Multi-variate Bernoulli model, a document is a binary vector over word space.
- Multinomial model, capturing word frequency in documents.

**Bayes Rule**:
![610c7572cef4bb8d8eb4aff02771e17b.png](./610c7572cef4bb8d8eb4aff02771e17b.png)
To find the most likely label $y$ given a set of words $X$, one can just maximise the likelihood * prior with respect to labels $Y$.

Instead of explicitly modelling the likelihood, we can assume all features are independent:
![1a28c4fe0ccd6c2bb935a137f54bd579.png](./1a28c4fe0ccd6c2bb935a137f54bd579.png)
This is what Naive Bayes classifiers do.

We can do **add-one smoothing** to avoid zero probabilities.
![c8d1faade9fec1ba8ef57234e73614ae.png](./c8d1faade9fec1ba8ef57234e73614ae.png)

Pretraining vs Fine-tuning
- Billions of tokens -> thousands of labelled examples
- Unlabelled text -> labelled text
- High compute -> lower compute
- Learning language -> learning task behaviour
