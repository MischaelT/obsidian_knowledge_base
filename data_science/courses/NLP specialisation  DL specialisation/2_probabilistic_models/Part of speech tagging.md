🏷️: #nlp 

- To help identify the parts of speech for every word, you need to build a transition matrix that gives you the probabilities from one state to another.![[Pasted image 20230716171545.png]]
- In the diagram above, the blue circles correspond to the part of speech tags, and the arrows correspond to the transition probabilities from one part of speech to another. You can populate the table on the right from the diagram on the left. The first row in your **A** matrix corresponds to the initial distribution among all the states. According to the table, the sentence has a 40% chance to start as a noun, 10% chance to start with a verb, and a 50% chance to start with another part of speech tag.
- The initial probabilities help determine the most likely POS tag for the first word in a sentence. These probabilities are usually estimated based on the frequency distribution of POS tags in a training corpus.
- The probabilities near the arrows called transition probability from one state to another
- General way to write a transition matrix:	![[Pasted image 20230716171619.png]]
- Emission probabilities is the probability of current hidden state being concrete value![[Pasted image 20230716172616.png]]
- ![[Pasted image 20230716172857.png]]
## Calculating the probabilities

- ![[Pasted image 20230716173455.png]]
	The number of times that blue is followed by purple is 2 out of 3. We will use the same logic to populate our transition and emission matrices. 
	![[Pasted image 20230716173612.png]]
## Populating the transition matrix

- ![[Pasted image 20230716175126.png]]
- In the table above, you can see that green corresponds to nouns (NN), purple corresponds to verbs (VB), and blue corresponds to other (O). Orange (�π) corresponds to the initial state. The numbers inside the matrix correspond to the number of times a part of speech tag shows up right after another one.
- To go from O to NN or in other words to calculate ![[Pasted image 20230716175312.png]] you have to compute the following:
	![[Pasted image 20230716175338.png]]
- Unfortunately, sometimes you might not see two POS tags in front each other. This will give you a probability of 0. To solve this issue, you will "smooth" it as follows:
	![[Pasted image 20230716175408.png]]

## Populating the Emission matrix
- ![[Pasted image 20230716175719.png]]
	To populate the matrix, we will also use smoothing.