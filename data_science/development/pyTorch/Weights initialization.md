### Problem
-  if the all weights in the same layer has the same value. 
-  To understand why this is important let's see what happens when we initialize all of the weights with the same value of one and bias to zero.
	After training the model, we see that our model does a horrible job of predicting the decision function. 
	Examining the model parameters we can see that the weight in the same layer has the same value. 
	This is because each neuron will have the same output and such have the same gradian update. 
	As a result it is recommended that we randomly initialize our parameters.
	Thats why its crucial  to randomly initialise weights
- How do we choose distribution - ?
	![[Pasted image 20230720123520.png]]
	If it is too wide, then for the numbers close to the edge gradient would be very big
	if its too narrow, numbers would be to close to each other so we can consider these as almost the same number that are contradicting the idea of random initialization
	And since the size of weights are inversely proportional to the gradient, the problem of the vanishing gradient will arise
- to fix the #vanishing_gradient problem we can use the adjust the weights of the distribution according to the number of neurons 
- n PyTorch by default if we use linear to create a linear object with “ L in” neurons, we simply make the lower bound of the range of the distribution the negative of the inverse of square root of L in.
- Another method is the Xavier initialisation
	![[Pasted image 20230720124611.png]]
- The HE initialization method aims to address the vanishing/exploding gradient problem that can occur during the training of deep neural networks. This problem arises when gradients become either too small (vanishing) or too large (exploding), hindering the convergence and stability of the network.
	HE initialization sets the initial weights of neurons in a way that helps stabilize the training process and enables efficient learning. It does so by scaling the weights according to the number of inputs to each neuron.

	The HE initialization for a layer with _n_in_ input units (neurons) is performed as follows:

	1. The weights are randomly initialized from a Gaussian distribution with a mean of 0 and a standard deviation of _sqrt(2 / n_in)_.

	This initialization approach ensures that the weights have an appropriate scale, which is essential for preventing vanishing or exploding gradients. The _sqrt(2 / n_in)_ scaling factor helps maintain a balance between preserving signal variance in the forward pass and reducing signal variance in the backward pass during backpropagation.