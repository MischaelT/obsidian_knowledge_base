- Its the method that allows you to re-size the image
	![[Pasted image 20230720145531.png]]
	W - is kernel, b is bias
	![[Pasted image 20230720145605.png]]
Let's go over the operation of convolution, its similar to dot product, but the output will be the activation map or rectangle tensor. 

We start off in the top right corner of the image, and we'll overlay the kernel with that region of the image. We see the kernel values in red, we will multiply every element of the image by the corresponding element of the kernel. For the first row we'll get the following operation, multiplying the intensity value and summing the results. This process is repeated for the second row, multiplying the intensity value and summing the results. 
![[Pasted image 20230720145746.png]]
Finally, for the final row we multiply the intensity value and sumthe results. We sum those elements together, the result is the first element of z. We shift the kernel to the right represented by the different colors in red. We multiply all the elements of the kernel with the image. This gives us the second element of the activation map. We'll shift the kernel one more column and perform the exact same operation, multiplying every element of the kernel by the corresponding intensity value of the image, adding them all together. This gives us the next value of the activation map. 
We shift the kernel down one row and repeat the process.

The convolution operation works as follows:

1. Input Image: The input image is represented as a 2D matrix of pixel values. Each pixel contains information about the color or intensity at that specific location in the image.
    
2. Filter (Kernel): The filter (also called kernel) is a smaller 2D matrix that defines a specific pattern or feature that the convolution operation aims to detect in the input image. The filter is typically smaller than the input image.
    
3. Sliding Window: The filter is placed on top of the input image, and a mathematical operation called element-wise multiplication is performed between the filter and the corresponding region of the input image. This region is called the receptive field or local region.
    
4. Convolution Sum: The element-wise multiplication results are then summed up, producing a single value that represents the convolution result for that specific position in the output feature map.
    
5. Stride and Padding: The process of sliding the filter over the entire input image is repeated, moving the filter by a certain number of pixels at a time. This movement is controlled by the stride parameter, which determines the step size. Additionally, padding can be applied to the input image to preserve the spatial dimensions of the input and output.
    

The resulting output feature map contains information about the presence of specific patterns or features in the input image. Each element in the feature map represents a localized response to the filter.

```python
conv3 = nn.Conv2d(in_channels=1, out_channels=1,kernel_size=2,stride=2)
```

### Activation Function:
	![[Pasted image 20230720150401.png]]

	![[Pasted image 20230720150458.png]]


- The use of activation functions and max pooling is essential in the context of deep learning and convolutional neural networks (CNNs) for several reasons:
	1. **Non-Linearity:** Activation functions introduce non-linearity into the neural network. Without non-linearity, a neural network would simply be a linear function of its input, and it would not be able to learn complex patterns and representations from the data. Activation functions like ReLU, sigmoid, and tanh introduce non-linearity, enabling the neural network to model and approximate more sophisticated relationships between input and output.
	2. **Feature Extraction:** Activation functions help in feature extraction. By applying an activation function to the output of a convolutional layer, the network can emphasize important features and suppress irrelevant or less significant information. This allows the network to capture meaningful patterns and structures in the input data, making it more effective for tasks like image recognition, object detection, and natural language processing.
	3. **Avoiding Vanishing/Exploding Gradients:** Activation functions play a crucial role in avoiding the vanishing and exploding gradient problems during training. These issues can occur when gradients become too small (vanishing) or too large (exploding) during backpropagation. Properly chosen activation functions, such as ReLU, help mitigate these problems and enable more stable and efficient training.
	4. **Downsampling and Dimensionality Reduction:** Max pooling is used for downsampling the spatial dimensions of the activation maps. It reduces the computational complexity and memory requirements of the model while retaining the most important features. By selecting the maximum value from each region, max pooling effectively summarizes the most relevant information, making the network more efficient and robust.

### Max pooling

- Max pooling is a downsampling technique used in convolutional neural networks (CNNs) for feature extraction. It reduces the spatial dimensions of the input feature map while retaining the most significant information. The process involves dividing the feature map into non-overlapping regions and selecting the maximum value from each region to create a new downsampled feature map. Max pooling helps reduce computational complexity, improve translation invariance, and maintain important features for efficient and effective deep learning.
```python
torch.nn.MaxPool2d(2)
```

### Multiple Input and Output Channels

- In Pytroch, you can create a `Conv2d` object with multiple outputs. For each channel, a kernel is created, and each kernel performs a convolution independently. As a result, the number of outputs is equal to the number of channels. This is demonstrated in the following figure. The number 9 is convolved with three kernels: each of a different color. There are three different activation maps represented by the different colors.
	![[Pasted image 20230720151813.png]]
	Symbolically, this can be represented as follows:
	![[Pasted image 20230720152108.png]]
	For two inputs, you can create two kernels. Each kernel performs a convolution on its associated input channel. The resulting output is added together as shown:
	![[Pasted image 20230720152456.png]]
	When using multiple inputs and outputs, a kernel is created for each input, and the process is repeated for each output. The process is summarized in the following image.
	
	There are two input channels and 3 output channels. For each channel, the input in red and purple is convolved with an individual kernel that is colored differently. As a result, there are three outputs.
	![[Pasted image 20230720152530.png]]