---
tags:
  - deep_learning
  - transformers
---

The initial sec2sec model was published by Google in 2014. It was supposed to overcome the existen in LSTMs and #GRU #vanishing_gradient  problem

Consist of two parts
- encoder
![[Pasted image 20231112171012.png]]
- decoder
![[Pasted image 20231112171126.png]]


1. **Training the Encoder:**
    - The encoder, which can be an RNN, LSTM, Transformer, or another architecture, takes the input sequences (e.g., sentences in machine translation) and processes them step by step.
    - As it processes each token or word, it updates its hidden state representation, capturing information about the sequence.
    - This learning process happens through backpropagation, where the model adjusts its parameters (weights) to minimize the difference between the predicted output and the actual target output.
2. **Using Encoder's Hidden State:**
    
    - The final hidden state of the encoder often encapsulates a summarized representation of the entire input sequence.
    - This final hidden state is used to initialize the decoder or as part of the context vector in the attention mechanism, enabling the decoder to start generating the output sequence based on the encoded information.
3. **Training the Decoder:**
    - During training, the decoder takes the previously generated tokens (or a start token) and its own hidden state as input.
    - It generates the output sequence step by step while updating its hidden state at each time step.
    - Similar to the encoder, the decoder's parameters are adjusted through backpropagation to minimize the difference between the predicted output and the actual target output.

So, both the encoder and decoder hidden states are learned representations that evolve during the training process. These hidden states encapsulate information about the input sequence (encoder) and the generated sequence (decoder), allowing the model to learn and generate accurate sequences during both training and inference (making predictions on new, unseen data).

One of the major problem of that approach is:
![[Pasted image 20231112171214.png]]
since the memory of encode and decoder are usually fixed in size that means that if the len of the sequence is bigger than the decoder, some of the information will be lost. As seq size increases model performace decreases'


One of the approaches to overcome that problem is to use the sep hidden state for each word, the total limitation of such an approach is the memory inefficiency and receivng a lot of useless information
![[Pasted image 20231112172156.png]]
![[Pasted image 20231112172141.png]]
The sequential nature of models you learned in the previous course (RNNs, LSTMs, GRUs) does not allow for parallelization within training examples, which becomes critical at longer sequence lengths, as memory constraints limit batching across examples. In other words, if you rely on sequences and you need to know the beginning of a text before being able to compute something about the ending of it, then you can not use parallel computing. You would have to wait until the initial computations are complete. This is not good, because if your text is too long, then 1) it will take a long time for you to process it and 2) you will lose a good amount of information mentioned earlier in the text as you approach the end.


The solution - attention mechanism

![[Pasted image 20231112171804.png]]
![[Pasted image 20231112172354.png]]

![[Pasted image 20231112172508.png]]

## Queries, keys and Values
- Effficient and poverful type of attention we will be using
- was firstly published in a "Attention is all whyou need
![[Pasted image 20231128130138.png]]

For example, if we are translating between french and english heure matches with time. So we'd like to get the value for time, in practice to the queries, keys and values are all represented by vectors. Embedding vectors for example. Due to this, you don't get exact matches but the model can learn which words are the most similar between the source and target languages. The similarity between words is called alignment. The query and key vectors are used to calculate alignment scores that are measures of how well the query and keys match. These alignment scores are then turned into weights used for awaited, sum of the value vectors, this weighted sum of the value vectors is returned as the attention vector.

- This process can be performed using scale dot-product attention. The queries for each step are packed together into a matrix Q. So attention can be computed simultaneously for each query. The keys and values are also packed into matrices K and V. These matrices are the inputs for the attention function shown as a diagram on the left and mathematically on the rights.
![[Pasted image 20231128130439.png]]
 unlike the original form of attention, scale dot-product attention consists of only two Matrix multiplications and no neural networks. Since matrix multiplication is highly optimized in modern deep learning frameworks. This form of attention is much faster to compute but this also means that the alignments between the source and target languages must be learned elsewhere.
 - 
Each entry in this matrix is the weight for the correspondent query, key pair word pairs that have similar meanings, K and T, for example, will have larger weights than the similar words like day and time. Through training, the model learns which words have similar meanings and encodes that information and the query and key vectors. Learning alignment like this is beneficial for translating between languages with different grammatical structures. Since attention looks at the entire input and target sentences at once and calculates alignments based on word pairs, weights are assigned appropriately regardless of word order. For example, In the sentence, the agreement on the European Economic Area was signed in August 1992 and this other sentence lack of lasagne economic open. I mean you're not meeting of sangatte revenues, you can see that zone in the area are at different positions, let's have the same meaning. The model has learned to align them appropriately, allowing the decoder to focus on the appropriate inputs words despite different ordering.

![[Pasted image 20231128131225.png]]

![[Pasted image 20231128131346.png]]

Teacher forcing

NMT Model


![[Pasted image 20231217181850.png]]

BLEU Score

ROUGE-N Score

![[Pasted image 20231217182754.png]]

two sentence construction methods: greedy decoding and random sampling. Greedy decoding chooses the most probable word at each step, but it can create repetitive or nonsensical sequences. On the other hand, random sampling selects words based on probabilities, offering more diversity but potentially leading to overly random outputs. Temperature, a parameter in sampling, controls randomness in predictions on a scale of 0-1, influencing the balance between confidence and risk-taking in outputs.

Beam Search

Minimum Bayes Risk