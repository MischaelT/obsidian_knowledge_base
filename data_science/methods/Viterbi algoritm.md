---
tags:
  - nlp
  - markov
---
- The purpose of the Viterbi algorithm is to make an inference based on a trained model and some observed data. It works by asking a question: given the trained parameter matrices and data, what is the choice of states such that the joint probability reaches maximum? In other words, what is the most likely choice given the data and the trained model? 
- The Viterbi algorithm makes use of the transition probabilities and the emission probabilities as follows.![[Pasted image 20230716180847.png]]

- To go from �π to �O you need to multiply the corresponding transition probability (0.3) and the corresponding emission probability (0.5), which gives you 0.15. You keep doing that for all the words, until you get the probability of an entire sequence.![[Pasted image 20230716180919.png]]
- Step 1: Initialisation
	