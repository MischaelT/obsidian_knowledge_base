---
tags:
  - nlp
  - evaluation
  - fine-tuning
aliases:
---
## Model evaluation

##### BLEU score
Bilingual evaluation understudy score
Used primarily in #machine_translation
Measures the similarity between the machine-translated text and the reference translations using n-grams(uni=grams, bi-grams etc) by calculating the precision
The formula looks like as following:

```BLEU = BP * exp(∑ pn)```

where BP is the penalty term for the translations which are shorter than the original message. It is calculated as min(1, (reference_length / translated_length)), where reference_length is the total number of words in the reference translations, and translated_length is the total number of words in the machine-generated translation.

The pn is the precision of n-grams which appears in both machine translation and the reference translations divided by the total numbers of n-grams appeared in reference translation
It is ranges from 0 to 1 where 1 is perfect translation and 0 is completely  incorrect.

The limitations:
	- It heavily relies on n-grams and may not capture the overall fluency of the answer
	- It may penalise the translation which are longer than the reference translations
#### ROUGE score
- stands as Recall-Oriented understudy for Gisting evaluation

- Primarily used for the text summarization tasks comparing the machine summarization to the ones written by human. It uses the overlapping n-grams = the word sequences appeared both on the in the generated and reference summaries

- The formula is
	`ROUGE = ∑ (Recall of n-grams)

- Recall of n-grams is the number of n-grams that appear in both the machine-generated summary and the reference summaries divided by the total number of n-grams in the reference summaries.

- ROUGE score ranges from 0 to 1, with higher values indicating better summary quality. Like BLEU score, a perfect summary would have a ROUGE score of 1, while a completely incorrect summary would have a ROUGE score of 0.

there are several types of Rouge scores:
- **ROUGE-N**: measures the overlap of n-grams (contiguous sequences of n words) between the candidate text and the reference text. It computes the precision, recall, and F1-score based on the n-gram overlap. For example, ROUGE-1 (unigram) measures the overlap of single words, ROUGE-2 (bigram) measures the overlap of two-word sequences, and so on. ROUGE-N is often used to evaluate the grammatical correctness and fluency of generated text.
- **ROUGE-L**:  measures the longest common subsequence (LCS) between the candidate text and the reference text. It computes the precision, recall, and F1-score based on the length of the LCS. ROUGE-L is often used to evaluate the semantic similarity and content coverage of generated text, as it considers the common subsequence regardless of word order.
- **ROUGE-S**: measures the skip-bigram (bi-gram with at most one intervening word) overlap between the candidate text and the reference text. It computes the precision, recall, and F1-score based on the skip-bigram overlap. ROUGE-S is often used to evaluate the coherence and local cohesion of generated text, as it captures the semantic similarity between adjacent words.
 
 ROUGE score also has limitations.
 - It may not fully capture the semantic meaning or coherence of the summary
 - It relies solely on the n-gram overlap, which may not always be an accurate measure of summary quality.
## Evaluation benchmarks

#### GLUE
stands for General Language Understanding Evaluation -- is the collection of NLP tasks, such as sentiment analysis and questions answering
#### Super GLUE
SuperGLUE includes tasks such as multi-sentence reasoning, and reading comprehension and addressing the limitations of the GLU
#### MMLU
stands for Massive Multitask Language Understanding designed specifically for modern LLM
Models are tested on elementary mathematics, US history, computer science, law, and more. 
In other words, tasks that extend way beyond basic language understanding.
#### HELM

The HELM framework aims to improve the transparency of models, and to offer guidance on which models perform well for specific tasks. HELM takes a multimetric approach, measuring seven metrics across 16 core scenarios, ensuring that trade-offs between models and metrics are clearly exposed. One important feature of HELM is that it assesses on metrics beyond basic accuracy measures, like precision of the F1 score. The benchmark also includes metrics for fairness, bias, and toxicity, which are becoming increasingly important to assess as LLMs become more capable of human-like language generation, and in turn of exhibiting potentially harmful behavior.
![[Pasted image 20240208120326.png]]

## Parameter efficient Fine-tuning

With PEFT, most if not all  of the LLM weights are kept frozen. As a result, the number of trained parameters is much  smaller than the number of parameters in the original LLM. In some cases, just 15-20% of the original LLM weights. This makes the memory requirements for training much more manageable.

![[Pasted image 20240208120639.png]]

#### PEFT methods

- Selective: select the subset of the initial parameters to fine-tune
- Reparametrasation: work  with the original LLM parameters, but reduce the number of parameters to train by creating new low rank transformations of the original network weights.
	One of the primary method called LoRA
		stands for Low-rank Adaptation. LoRA is a strategy that reduces the number of parameters to be trained during fine-tuning by freezing all of the original model parameters and then injecting a pair of rank decomposition matrices alongside the original weights.
		![[Pasted image 20240208124853.png]]
		However, in principle, you can also use LoRA on other components like the feed-forward layers. But since most of the parameters of LLMs are in the attention layers, you get the biggest savings in trainable parameters by applying LoRA to these weights matrices.
		![[Pasted image 20240208125443.png]]
	
- additive: carry out fine-tuning by keeping all of the original LLM weights frozen and introducing new trainable components.
	There are two approaches:
	- adapters, which adds the new, trainable layers either in encoder or in the decoder. Right after the attention or feed forward layers
	- soft'prompts: keep the model architecture fixed, but rather focused on manipulating the input to achieve better results. Such provess called prompt-tuning
		With prompt tuning, you add additional trainable tokens to your prompt and leave it up to the supervised learning process to determine their optimal values.  The set of trainable tokens is called a soft prompt, and it gets prepended to embedding vectors that represent your input text. The soft prompt vectors have the same length as the embedding vectors of the language tokens. And including somewhere between 20 and 100 virtual tokens can be sufficient for good performance. However, the soft prompts are not fixed discrete words of natural language. Instead, you can think of them as virtual tokens that can take on any value within the continuous multidimensional embedding space. And through supervised learning, the model learns the values for these virtual tokens that maximize performance for a given task.
		![[Pasted image 20240208130505.png]]