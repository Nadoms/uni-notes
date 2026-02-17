# W3 - Transformer Language Models
## Transformer Architecture
- Built entirely on attention, dropping the RNN part
- Encoder-decoder architectures
- Encoder-only architectures, like BERT
- Decoder-only architectures, like GPT

Attention time and memory scale quadratically with sequence length, because every token attends to all other tokens. This is parallelisable.

Encoders contain a self-attention and feed-forward layer.
Decoders contain a masked self-attention, a cross-attention (from encoder outputs) and a feed-forward layer.

## BERT
Motivation: both left and right contexts are important to understand words and sentences.

**Masked language modelling** - Mask certain tokens in a sentence and predict what they were.
- Too little masking is expensive
- Too much masking makes the task impossible
- 15% of tokens are selected for masking
- 80-10-10 corruption for masking, random replacement, leaving it unchanged