# W8 - Large Language Models

## LLM Architecture
- Transformer encoder for e.g. sequence to label for BERT
- Transformer decoder for e.g. sequence generation for GPT
- Transformer encoder-decoder for e.g. sequence to sequence for T5

## LLM Training
**Model parameters** - Input vectors for tokens, neural network weights, projection matrices for attention, etc.
**Objective** - Finding best values for model parameters using training instances
**Objective function** - Performance measure examined using training instances

Two main LLM training steps:
**Unsupervised pretraining** with unlabelled text.
**Supervised fine-tuning** based on downstream NLP tasks.

### Bidirectional Encoder Representations from Transformers (BERT)
- Proposed by Google researchers in 2018
- Uses a transformer encoder stucture, taking a sentence or sentence pair as input
- Pretrained on BooksCorpus and Wikipedia
- Pretrained for masked language model and next sentence prediction

### BERT Pretraining
**MLM**
- Randomly select 15% of tokens in the sentence
- Replace with [MASK], a random token, or keep the same
    - "my dog is cute"
    - "my dog is [MASK]"
    - "my dog is apple"
- Predict which tokens in the sentence are masked

**NSP**
- Extract sentence pairs from the corpus
- Randomly replace sentence B with a random other sentence
    - "my dog is cute [SEP] he likes playing"
    - "my dog is cute [SEP] how do magnets work"
- Perform binary classification if the pair is real

### BERT Fine-tuning
Fine tuning on tasks from **GLUE benchmark**
- Single sentence classification
    - Predict whether a sentence is linguistically acceptable
    - Predict sentiment of movie reviews
- Sentence pair classification
    - Predict semantic equivalence between sentences
    - Predict semantic equivalence between Quora questions
    - Score semantic equivalence between sentences
- Natural language inference
    - Predict whether the 2nd sentence is an entailment, contradiction or neutral
    - Predict an answer to a question give a Wikipedia passage

### Generate Pre-Trained Transformers (GPT)
- Introduced by OpenAI in 2018
- Use a transformer decoder structure, generating output after prompt from input
- Does generative pretraining, predicting each token from previous k tokens

DONE ONLY HALF OF THE LECTURE