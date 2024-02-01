🏷️: #dropout #regularisation

- Dropout, a regularisation method used to prevent over fitting use exclusively for neural networks.
	Dropout involve two phases: 
	1. The training phase is where we implement the dropout method. 
	2. The evaluation phase, where we turn off the drop out method to test the performance of our model.
- The dropout is implemented by multiplying the activation function with the Bernoulli random variable r. The Bernoulli distribution is a discrete probability distribution where the random variable r takes on the value 0 with probability p, and takes on the value 1 with the probability 1 - p. By doing this we make some neurons be equal to zero with the probability of p
-  ![[Pasted image 20230719142722.png]]
	![[Pasted image 20230719142743.png]]
	![[Pasted image 20230719142801.png]]
