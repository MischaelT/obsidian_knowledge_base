---
tags:
  - math
  - function
---

- **Softmax** is a mathematical function used in machine learning and neural networks to convert a vector of real numbers into a probability distribution. It takes an input vector and normalizes it into a probability distribution where the sum of all the elements is equal to 1.
- It is commonly used as the last activation function in the output layer of a neural network for multi-class classification problems.
- ![[Pasted image 20230719120455.png]]
-  Why Not Sigmoid?
	Suppose we calculate the Z value using weights and biases of this layer and apply the sigmoid activation function over these values. We know that the sigmoid activation function gives the value between 0 and 1. suppose these are the values we get as output.
	![[Pasted image 20230719120827.png]]
	There are two problems in this case:
	1. First, if we apply a thresh-hold of say 0.5, this network says the input data point belongs to two classes. 
	2. Secondly, these probability values are independent of each other. That means the probability that the data point belongs to class 1 does not take into account the probability of the other two classes.
	This is the reason the sigmoid activation function is not preferred in multi-class classification problems.
- The softmax function, when combined with the argmax operation, is commonly used to make predictions in multi-class classification tasks. The softmax function converts raw scores (logits) into a probability distribution, and the argmax operation then selects the class with the highest probability as the predicted class.
- The division of exponentiated values in the softmax function is a crucial step that transforms the logits (raw scores) into probabilities. This transformation ensures that the resulting values are non-negative and that they sum up to 1, creating a valid probability distribution. Let's understand this process step-by-step:
	1. Exponentiation: The softmax function first exponentiates each element of the input vector (logits). This is done using the exponential function (exp) to ensure that all values become non-negative. Exponentiation amplifies the differences between the logits, which is important for distinguishing the relative importance of each class.
	2. Summation: The next step is to calculate the sum of all the exponentiated values.
	3. Division: Finally, the exponentiated values are divided by the sum obtained in the previous step. This division normalizes the values and ensures that they become probabilities that sum up to 1.
-