- Deep neural network is the network  with multiple hidden layers
	```python
	class Net(nn.Module):
    
    # Constructor
    def __init__(self, D_in, H1, H2, D_out):
        super(Net, self).__init__()
        self.linear1 = nn.Linear(D_in, H1)
        self.linear2 = nn.Linear(H1, H2)
        self.linear3 = nn.Linear(H2, D_out)
    
    # Prediction
    def forward(self,x):
        x = torch.sigmoid(self.linear1(x)) 
        x = torch.sigmoid(self.linear2(x))
        x = self.linear3(x)
        return x
	```
	deep NN with 2 hidden layer
- When the quantity of hidden layers increase, it become inconvenient to use constructor from the previous part. That's why we can use nn.ModuleList
	```python
	Layers = [2, 50, 3]
	class Net(nn.Module):
	    
	    # Constructor
	    def __init__(self, Layers):
	        super(Net, self).__init__()
	        self.hidden = nn.ModuleList()
	        for input_size, output_size in zip(Layers, Layers[1:]):
	            self.hidden.append(nn.Linear(input_size, output_size))
	    
	    # Prediction
	    def forward(self, activation):
	        L = len(self.hidden)
	        for (l, linear_transform) in zip(range(L), self.hidden):
	            if l < L - 1:
	                activation = F.relu(linear_transform(activation))
	            else:
	                activation = linear_transform(activation)
	        return activation
	        
	def train(data_set, model, criterion, train_loader, optimizer, epochs=100):
	    LOSS = []
	    ACC = []
	    for epoch in range(epochs):
	        for x, y in train_loader:
	            optimizer.zero_grad()
	            yhat = model(x)
	            loss = criterion(yhat, y)
	            optimizer.zero_grad()
	            loss.backward()
	            optimizer.step()
	            LOSS.append(loss.item())
	        ACC.append(accuracy(model, data_set))
	```
- Consider the following dataset:
	![[Pasted image 20230719135917.png]]
	That would be the result of NN with different quantities of hidden layers
	![[Pasted image 20230719140003.png]]
- 