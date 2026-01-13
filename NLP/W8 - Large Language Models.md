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

### Generative Pre-Trained Transformers (GPT)
- Introduced by OpenAI in 2018
- Use a transformer decoder structure, generating output after prompt from input
- Does generative pretraining, predicting each token from previous k tokens

### GPT Fine-tuning
Supervised fine-tuning is based on a collection of downstream NLP tasks, like BERT.
Concatenates the input and ou tput in the same sequence with a delimiter.
The representation vector of the last token in the last layer is used for prediction.

## LLM Training Techniques
### Instruction Fine-tuning
- Prepares input-output pairs for training
- Describes all NLP tasks using natural language instructions
- Fine-tune the LLM to understand and process instructions
- Can provide examples to show what the task is about
    - E.g. Translate X to Y: A -> B, C -> D, E -> ?

### Chain-of-Thought Annotation
- Improves LLM performance on unseen reasoning tasks
- Annotate questions with a chain of reasoning
- This can also be done with exemplar

### Human Feedback
GPT-4 was fine-tuned with human feedback from over 50 experts, adversarially testing the model. E.g. against the ability to refuse requests on how to synthesise dangerous chemicals.