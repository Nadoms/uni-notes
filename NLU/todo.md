- open information extraction
- casual language modelling / reasoning
- BPE
- "MCC" eval metric - its matthews correlation coefficient. if its 0 its like if the model is randoma nd useless and
- inverse doc freq uses log
- static embedding vectors vs contezxtual embedding ???
- "head" of a word - what the word needs to give meaning kinda. can be verb or noun.
- back prop computes the gradients
- BLEU
- do this website thing


in an rnn hidden states blah.  c is what goes in between encoder and decoder.
attentiuon recalcs c at every step. avoids info bottleneck. uses dot product for attention.
dot product is bigger when vectors are similar

transformer uses self attention, every position attends to every other position. keys vals querys are from same seq
bidirectional attention like bert encoede.
casual attention, only 1...i, like gpt decode. the upper end is masked.
positional embeddings are needed bc self-attention is invariant to position otherwise.

bert tokens are subwords. 512 tokens total. CLS for pos 0, SEP for separations.
masked language modelling is a training task. select 15% of tokens, of them  replace 80% with MASK, 10% wuith random, 10% unchanged.
next sentence pred is another. make pairs of sentences. half it is the real next sentences, other time t is a random ass sentence.
berts value is in transfer, post learning general language.

VADER is a sentiment calssifier which runs on punctuationn, caps, intensifiers, et.c

natural language inference if to decide entailment, contradicatioon, or neutral. for a pair of premise and hyp.

bootstrapping grows sentiment lexicon by linking words of similar polarity. for sentiment analysis. good -> brilliant

sparse vectors have many zeros, high-d. e.g. tf-idf.
dense vectors are lower-d. can be static dense (word to vec, glove), which are fixed after training, or contextual dense (transformer).

distributional semantics - words which appear in similar areas usually will mean the same. e.g. knight in shining armour. knight and armour are linked.

static dense embedding methods:
word2vec has 2 obj, skip-gram and CBOW. guveb a word, predict its context
glove ugh, idk
fastText
1 vector peeer word. cant distinguish meaning for same word.
term freq is log of term count + 1
inverse doc freq is log too.

ppmi, positive pointwise mutual information. measures co - occurrence of two words beyond what chance would say. goes 0 to inf
shouldnt be negative bc u cant really saaay words are mutually exclusive easily.

in a hmm, viterbi is finding the most likely tag given word seq

BPE is byte pair encoding, used for subword. it starts with individual characters and iterates to merge the most frrrequent pair of symbol. byte pair encoding is the one which goes l o w e r, lo w er, low er.