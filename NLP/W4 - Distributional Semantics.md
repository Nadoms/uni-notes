# W4 - Distributional Semantics
**Distributional semantics** is about characterising the meaning of a linguistic item, through a multi-dimensional feature vector.
**Feature vector** is just a set of numbers describing an item.
**Semantic similarity** can be quantified between two vectors using cosine or inner product.
**Distributional hypothesis** is that one can infer the meaning of a word just by looking around it.

### Vector Space Model (Simplest)
Make your word vectors by document.
This is a naive approach, as two words may appear in the same document but not be similar.
![4f000c00472ca66d56a942f48fff1ac8.png](./4f000c00472ca66d56a942f48fff1ac8.png)

Or you can make your word vectors by local context, with a context window.
You would have to make a vocabulary to consider words against.
Smaller window = syntax, larger window = semantics.
![7bd5c8ab40549a7bc8440f071efab4c8.png](./7bd5c8ab40549a7bc8440f071efab4c8.png)

VSMs generate high-dimensional, sparse vectors, where most elements are zero.

### Latent Semantic Indexing (Historic)
The method is just the singular value decomposition (SVD).
It doesn't matter. It's archaic.
LSI can do document and term vectors, like a VSM.
You can do truncated SVD by choosing a k value smaller than the rank of the input matrix.
![77041d1565dd9efbcbef7571fc88c145.png](./77041d1565dd9efbcbef7571fc88c145.png)

### Word2vec and GloVe (Classical)
These can produce low-dimensional, dense vectors.
One must define the context, and then pick a prediction task:
- Whether a word appears in the context of a target word (word2vec)
- How many times a word appears in the context of a target word (GloVe)

### W2V: Continuous Bag-of-Words Model
- Look at each word and find its context on either side
- Attempt to classify the word in the middle e.g. [large, scale, value, computation] class: [singular]
![dda57f1fe74e5275f95d39b24e94d032.png](./dda57f1fe74e5275f95d39b24e94d032.png)
- Each context word corresponds to a vector of weights for every word
- Take average of context vectors forming a feature vector
- Select one of the word classes using logistic regression

### W2V: Skip-Gram Model
- Predict context from target instead
- Multilabel classification (one object can have multiple classes)
![c5511d2316133b3d3a84080b3d2c0d3f.png](./c5511d2316133b3d3a84080b3d2c0d3f.png)
- Can be improved through negative sampling
![bb056d8e9173a54077e1f0f9521a33aa.png](./bb056d8e9173a54077e1f0f9521a33aa.png)

### GloVe Model
- Utilises the frequency that a word appears in another word's context
- Word-word co-occurence matrix from entire corpus
- King - man + woman = queen