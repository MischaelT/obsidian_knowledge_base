🏷️: #function 
- Visualising in 2D
![[Pasted image 20230719121923.png]]
Every point is the vector
- Everything that is closest to the line w1, w2, w3 help us understand the class of the x.
![[Pasted image 20230719122117.png]]
Computing the dot product, and using the argmax function on the computed values, we see that we will classify this sample belonging to class 1. Mathematically, the dot product for the vectors is calculated by performing matrix multiplication for each vector as explained earlier in the previous modules. 
The reason the function is called Softmax since the actual distances i.e. dot products for each input vector with the parameters is converted to probabilities using the following probability functions.
![[Pasted image 20230719125416.png]]