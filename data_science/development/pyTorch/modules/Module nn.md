- from torch import nn
- The "nn" module offers a high-level API for building and training deep learning models. It contains a wide range of classes and functions that are essential for constructing and working with neural networks. Some of the key components included in the "nn" module are:
	1. Neural network layers: PyTorch provides a variety of pre-defined layers such as fully connected layers (`nn.Linear`), convolutional layers (`nn.Conv2d`, `nn.ConvTranspose2d`), recurrent layers (`nn.RNN`, `nn.LSTM`, `nn.GRU`), and more. These layers are building blocks used to construct complex neural network architectures.
    
	2. Activation functions: PyTorch's "nn" module includes popular activation functions such as ReLU (`nn.ReLU`), sigmoid (`nn.Sigmoid`), tanh (`nn.Tanh`), and softmax (`nn.Softmax`). Activation functions introduce non-linearity to the neural network, enabling it to learn complex patterns and make predictions.
    
	3. Loss functions: The "nn" module provides various loss functions like mean squared error (`nn.MSELoss`), binary cross-entropy (`nn.BCELoss`), categorical cross-entropy (`nn.CrossEntropyLoss`), and more. Loss functions quantify the difference between predicted and actual values, serving as a measure of the model's performance.
    
	4. Optimization algorithms: such as stochastic gradient descent (`torch.optim.SGD`), Adam (`torch.optim.Adam`), and others. These algorithms are used to update the parameters of the neural network during the training process, aiming to minimize the loss and improve model accuracy.
    
	5. Utilities and other components: The "nn" module includes additional utilities like dropout (`nn.Dropout`), batch normalization (`nn.BatchNorm2d`), sequential container (`nn.Sequential`), and more. These components enhance the flexibility and functionality of neural network models.
- ![[Pasted image 20230716105242.png]]
- 