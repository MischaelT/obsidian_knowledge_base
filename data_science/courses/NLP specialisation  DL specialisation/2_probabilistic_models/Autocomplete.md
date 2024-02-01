🏷️: #nlp 
### N-gram and probabilities
- N-gram is the sequence of N words
	![[Pasted image 20230722102053.png]]
	![[Pasted image 20230722102214.png]]
	![[Pasted image 20230722102319.png]]
	![[Pasted image 20230722102417.png]]
	![[Pasted image 20230722102449.png]]
### Sequence probability
	![[Pasted image 20230722102908.png]]
	Problem is that the corpus almost never contains the exact sentence or even its longer subsequences. Hence, you can easily end up getting a probability of 0. The _Markov assumption_ indicates that only the last word matters. Hence:![[Pasted image 20230722103406.png]]
### Start and the end of the sentence
- We usually start and end a sentence with the following tokens respectively: `<s> </s>`
	When computing probabilities using a unigram, you can append an `<s>` in the beginning of the sentence. To generalize to an N-gram language model, you can add N-1 start tokens `<s>`.
	Otherwise, the first word would be n-1 gram, instead of n-gram
	![[Pasted image 20230722104900.png]]
### N-gram language model
- Count matrix![[Pasted image 20230722142607.png]]
	The count matrix captures all n-grams appearing in the corpus.
- Probability matrix
	![[Pasted image 20230722143039.png]]
	represents the probability of each concrete n=gram 
-  connect the probability matrix with your definition of the language model from this week's overview. The language model can now be a simple script that uses the probability matrix to estimate the probability of a given sentence. It estimates the probability by splitting the sentence into a series of n-grams and then finding their probability in the probability matrix. Alternatively, the language model can predict the next elements of a sequence by extracting the last n minus one gram from the end of a sequence. After that, the language model finds the corresponding grow in the probability matrix, and returns the word with the highest probability.
  - Log probability to avoid underflow
	  ![[Pasted image 20230722143526.png]]
### LM evaluation
- Perplexity can be considered as complexity of a text
- ![[Pasted image 20230722143820.png]]
- Perplexity is used to tell us whether a set of sentences look like they were written by humans rather than by a simple program choosing words at random. A text that is written by humans is more likely to have a lower perplexity score.
- perplexity as closely related to #entropy, which measures uncertainty.
- smaller the perplexity == better the model
	![[Pasted image 20230722145212.png]]
- sometimes log perplexity is used instead of perplexity
### Out of vocab words
- A vocabulary is a set of unique words supported by your language model. In some tasks like speech recognition or question answering, you will encounter and generate words only from a fixed set of words. Hence, a **closed vocabulary**.
- **Open vocabulary** means that you may encounter words from outside the vocabulary, like a name of a new city in the training set. Here is one recipe that would allow you to handle unknown words.
	- Create vocabulary V
	- Replace any word in corpus and not in V by ``<UNK>`
	-  Count the probabilities with `<UNK>` as with any other word
### Smoothing
- sometimes some n grams can be absent in training corpus, so the probability of occurring such would be close to zero
	![[Pasted image 20230722150903.png]]
### Backoff
- ![[Pasted image 20230722151028.png]]
- With backoff, if N-gram information is missing, you use (N-1)-gram. If that's also missing, you would use (N-2)-gram and so on until you find nonzero probability. Using the lower level N-grams i.e (N-1)-gram, (N-2)-gram down to uni-gram. It distorts the probability distribution especially for smaller corporal. Some probability needs to be discounted from higher-level N-grams to use it for lower-level N-grams. This Katz backoff method uses discounting. 
	In very large web scale corpus is a method called Stupid backoff has been effective. With Stupid backoff, no probability discounting is applied. If the higher order N-gram probability is missing, the lower order N-gram probability is used. Just multiplied by a constant. A constant of about 0.4 was experimentally shown to work well.
### Interpolation
-  to use the linear interpolation of all orders of N-grams. That means that you would always combine the weighted probability of the N-gram and -1 gram down to uni-grams. For example, when calculating the probability for the tri-gram John drinks chocolate, you could take 70% of the estimated probability for tri-gram. So John drinks chocolate plus 20% of the estimated probability for by-gram, drinks chocolate and 10% of the estimated uni-gram probability of the word chocolate.
	![[Pasted image 20230722151403.png]]