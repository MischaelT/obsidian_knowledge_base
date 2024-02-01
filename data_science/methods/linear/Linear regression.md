🏷️: #linear_algebra  #linear_model #linear_regression #classification 
- Types of error of the model
- ![[Pasted image 20230514170709 1.png]]
- Multiple linear regression
	- multiple independent variables
	-![[Pasted image 20230514171518 1.png]]
	- The first element of the feature set would be set to one, because it turns in theta zero parameter. The intercept or biased parameter.
	- ![[Pasted image 20230514171905 1.png]]
- Logistics regression
	-  subtype of linear regression that allow to classify the data.
	- ![[Pasted image 20230522162154 1.png]]
	- ![[Pasted image 20230522162729 1.png]]
	- ![[Pasted image 20230522163000 1.png]]
	- #sk_learn

```
- # SoftMax Regression

SoftMax regression is similar to logistic regression, the SoftMax function converts the actual distances i.e. dot products of 𝑥 with each of the parameters ��θi​ for 𝐾 classes in the range from 0 to 𝐾-1. This is converted to probabilities using the following formula.

![[Pasted image 20230522164858 1.png]]

The training procedure is almost identical to logistic regression using cross-entropy, but the prediction is different . Consider the three-class example where �∈{0,1,2}y∈{0,1,2} i.e �y can equal 0,1,2.  We would like to classify �x. We can use the SoftMax function to generate a probability of how likely the sample belongs to each class. We then  make a prediction using the ������argmax function:

![[Pasted image 20230522164915 1.png]]


🏷️: #linear_algebra #linear_regression #linear_model
![[img/Pasted image 20230515174302.png]]
## Training

![[img/Pasted image 20230515181726.png]]
## Loss

![[img/Pasted image 20230515182239.png]]

- loss function is referred to as the parameter space, as it contains different lines corresponding to different parameters
## Gradient Descent

- Gradient descent is a method to find the minimum of a function, it can be applied to functions with multiple dimensions.
-![[img/Pasted image 20230515183002.png]]
- In Gradient descent we iteratively calculate this equation, we start off with a guess,  we update the parameter by adding a value proportional to the derivative.
##### When to stop gradient descent?
- We can run gradient descent, for a set number of iterations is a popular way, in this case we run it for 3 iterations.  But for the final iteration we miss the minimum. 
- Another method to stop gradient descent is to see if the loss starts increasing,