🏷️: #rnn #deep_learning #sequence_models

![[Pasted image 20230903095534.png]]

![[Pasted image 20230903100244.png]]

The computations made in vanilla RNN are the following equations:
![[Pasted image 20230903100333.png]]
### Hidden State Activation
In this notebook you'll take another look at the hidden state activation function. It can be written in two different ways.
All the multiplications here are the matrix multiplication

![[Pasted image 20230903095534.png]]
![[Pasted image 20230903095811.png]]

![[Pasted image 20230903095601.png]]

Where

![[Pasted image 20230903095632.png]]

### Advantages of RNNs

RNNs allow us to capture dependancies within a short range and they take up less RAM than other n-gram models.

### Disadvantages of RNNs

RNNs struggle with longer term dependencies and are very prone to vanishing or exploding gradients.
Note that as you are back-propagating through time, you end up getting the following:

![[Pasted image 20230903112830.png]]

![[Pasted image 20230903113122.png]]
Note that the _sigmoid_ and _tanh_ functions are bounded by 0 and 1 and -1 and 1 respectively. This eventually leads us to a problem. If you have many numbers that are less than |1|, then as you go through many layers, and you take the product of those numbers, you eventually end up getting a gradient that is very close to 0. This introduces the problem of vanishing gradients.
![[Pasted image 20230903113154.png]]
### How to handle these problems
![[Pasted image 20230903112911.png]]
### Bi-directional RNN
Bi-directional RNNs are important, because knowing what is next in the sentence could give you more context about the sentence itself.
![[Pasted image 20230903101911.png]]
So you can see, in order to make a prediction �^y^​, you will use the hidden states from both directions and combine them to make one hidden state, you can then proceed as you would with a simple vanilla RNN.
### Deep RNN
When implementing Deep RNNs, you would compute the following
![[Pasted image 20230903102141.png]]
![[Pasted image 20230903102203.png]]