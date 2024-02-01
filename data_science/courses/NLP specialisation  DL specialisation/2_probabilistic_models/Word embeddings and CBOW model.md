🏷️: #nlp 

### Intro
Word embeddings are used in most NLP applications. Whenever you are dealing with text, you first have to find a way to encode the words as numbers. Word embedding are a very common technique that allows you to do so. Here are a few applications of word embeddings that you should be able to implement by the time you complete the specialization.
![[Pasted image 20230722170805.png]]
###  Word respresentation types
- Basic word representations could be classified into the following:
	- Integers
		![[Pasted image 20230722170152.png]]
		Its an example where you use integers to represent a word. The issue there is that there is no reason why one word corresponds to a bigger number than another. To fix this problem we introduce one hot vectors (diagram on the right).
	- One-hot vectors
		To implement one hot vectors, you have to initialize a vector of **zeros** of dimension _V_ and then put a 1 in the index corresponding to the word you are representing.
		![[Pasted image 20230722170328.png]]
		- The **pros** of one-hot vectors: simple and require no implied ordering.
		- The **cons** of one-hot vectors: huge and encode no meaning.
		![[Pasted image 20230722170440.png]]
	- Word embeddings
		![[Pasted image 20230722170642.png]]
		From the plot above, you can see that when encoding a word in 2D, similar words tend to be found next to each other. Perhaps the first coordinate represents whether a word is positive or negative. The second coordinate tell you whether the word is abstract or concrete. This is just an example, in the real world you will find embeddings with hundreds of dimensions. You can think of each coordinate as a number telling you something about the word.
		![[Pasted image 20230722171024.png]]
### Creation of word embeddings
- There are many types of possible methods that allow you to _learn_ the word embeddings. The machine learning model performs a learning task, and the main by-products of this task are the word embeddings. The task could be to learn to predict a word based on the surrounding words in a sentence of the corpus, as in the case of the continuous bag-of-words.

- The task is **self-supervised**: it is both unsupervised in the sense that the input data — the corpus — is unlabelled, and supervised in the sense that the data itself provides the necessary context which would ordinarily make up the labels. 

- When training word vectors, there are some parameters you need to tune. (i.e. the dimension of the word vector)
- ![[Pasted image 20230722171547.png]]

#### Classical Methods

- word2vec (Google, 2013)
- _Continuous bag-of-words (CBOW)__:_ the model learns to predict the center word given some context words.
- _Continuous skip-gram / Skip-gram with negative sampling (SGNS)_: the model learns to predict the words surrounding a given input word.
- _Global Vectors (GloVe) (Stanford, 2014)_: factorizes the logarithm of the corpus's word co-occurrence matrix, similar to the count matrix you’ve used before.
- _fastText (Facebook, 2016)__:_ based on the skip-gram model and takes into account the structure of words by representing words as an n-gram of characters. It supports out-of-vocabulary (OOV) words.

#### Deep learning, contextual embeddings

 In these more advanced models, words have different embeddings depending on their context. You can download pre-trained embeddings for the following models.
- BERT (Google, 2018):
- ELMo (Allen Institute for AI, 2018)
- GPT-2 (OpenAI, 2018)

### Continuous Bag of Words Model (CBOW)
##### Description
- To create word embeddings, you need a corpus and a learning algorithm. The by-product of this task would be a set of word embeddings. In the case of the continuous bag-of-words model, the objective of the task is to predict a missing word based on the surrounding words.
	![[Pasted image 20230722173526.png]]
##### Cleaning and tokenisation
	![[Pasted image 20230722173924.png]]
##### Architecture
![[Pasted image 20230722175141.png]]
![[Pasted image 20230722175719.png]]
![[Pasted image 20230722175838.png]]
##### Extracting Word embeddings
There are two options to extract word embeddings after training the continuous bag of words model. You can use �1w1​ as follows:
	![[Pasted image 20230722180621.png]]
If you were to use �1w1​, each column will correspond to the embeddings of a specific word. You can also use �2w2​ as follows:
	![[Pasted image 20230722180714.png]]
The final option is to take an average of both matrices as follows:
	![[Pasted image 20230722180743.png]]
##### Intrinsic and extristic evaluation
**Intrinsic evaluation** allows you to test relationships between words. It allows you to capture semantic analogies as, _“France” is to “Paris” as “Italy” is to `
<?>_ and also syntactic analogies as _“seen” is to “saw” as “been” is to <?>__._`

_Ambiguous_ cases could be much harder to track:

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/WYeHySclSXKHh8knJQlyOg_1b311a595e654d6f8c03dfc66dbc1cbd_Screen-Shot-2021-03-29-at-5.26.53-PM.png?expiry=1690156800000&hmac=t_zmhDrSBqT24pZ-nmQv6leXmjG4GJocRs0jE3-uCxA)

Here are a few ways that allow to use intrinsic evaluation.

![](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/vQBs53_BSlqAbOd_wapaWg_fad8253825684cfdb89980713be06f9e_Screen-Shot-2021-03-29-at-5.28.00-PM.png?expiry=1690156800000&hmac=jHWvfRyS4CIaSwpowIzb52zd2_4frzr_DntHSTcZtzc)

**Extrinsic evaluation** tests word embeddings on external tasks like named entity recognition, parts-of-speech tagging, etc.
- Pros:
	- Evaluates actual usefulness of embeddings
- Cons:
	- Time Consuming
	 - More difficult to trouble shoot