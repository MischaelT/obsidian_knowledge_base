- A neural network is a function that can be used to approximate most functions using a set of parameters.
![[Pasted image 20230719130205.png]]

- Each linear function and activation is known as an artificial neuron.
- ![[Pasted image 20230719130635.png]]
- On the left before split there are hidden layers, on the right after its the output layer
```python
# Define the class Net

class Net(nn.Module):
    
    # Constructor
    def __init__(self, D_in, H, D_out):
        super(Net, self).__init__()
        # hidden layer 
        self.linear1 = nn.Linear(D_in, H)
        self.linear2 = nn.Linear(H, D_out)
    
    # Prediction
    def forward(self, x):
        x = self.linear1(x)
        x = self.linear2(sigmoid(x))
        yhat = sigmoid(self.linear2(x))
        return yhat
```

### More hidden layers

- Lets imagine that we have such dataset:
	![[Pasted image 20230719131630.png]]
- Lets use the NN with 6 hidden layers
- ![[Pasted image 20230719131508.png]]
- We will have such sum of functions:
	![[Pasted image 20230719131818.png]]
	![[Pasted image 20230719131848.png]]
	![[Pasted image 20230719131910.png]]
	![[Pasted image 20230719131927.png]]
- An NN with more hidden layers can built more complex decisions function

### Multiple Dimensional Input
- Consider the following samples in 2d space
	![[Pasted image 20230719132322.png]]
- Here is what we got by using two neurons
	![[Pasted image 20230719132543.png]]
- What we got by using 3 neurons
	![[Pasted image 20230719132641.png]]
- By using 4 neurons
	![[Pasted image 20230719132730.png]]
- Here what we got if we think about the problem in more dimensions
	![[Pasted image 20230719132913.png]]
	We need a surface that would correctly divide two classes
### Multi-class NN
- In PyTorch in order to classify multiple classes, you simply set the number of neurons output layer to match the number of classes in the output of the problem.  
	For example, if the output of the problem consists of 3 classes, you should add three neurons to the output layer of your model. 
	![[Pasted image 20230719133930.png]]
- Each neuron has its own set of parameters and can be expressed as a row in a matrix.
	![[Pasted image 20230719134327.png]]
	Consider an example where we have four neurons in the hidden layer. 
	We replace the features x with the activations of the neurons from the hidden layer. For each class in the output layer we have a neuron. The column in the matrix represents each neuron. In this case, as we have three classes, our matrix has three columns. As with other linear transforms, we have three biases. The number of rows in the matrix is the number of neurons in the previous layer. In this case, we have four neurons in the previous layer. As a result, we have four rows in our matrix.
	To make a prediction for a given input it's similar to using a Softmax classifier. For each class we get an input, we select the index of the column with the largest value as the class, in this case the class is two.