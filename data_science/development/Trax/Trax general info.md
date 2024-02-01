🏷️: #nlp #trax
🔗:  https://github.com/google/trax

## Neural Networks

**Trax** has several advantages:

- Runs fast on CPUs, GPUs and TPUs
- Parallel computing
- Record algebraic computations for gradient evaluation
![[Pasted image 20230830092259.png]]
## Layers

A serial layer allows you to compose layers in a serial arrangement:
![[Pasted image 20230830092427.png]]
It is a composition of sublayers. These layers are usually dense layers followed by activation layers.

- In Trax, the function grad allows you to compute the gradient. You can use it as follows:
![[Pasted image 20230830093337.png]]
- Now if you were to evaluate _grad_f_ at a certain value, namely _z_, it would be the same as computing _6z+1_. Now to do the training, it becomes very simple:
![[Pasted image 20230830093358.png]]
- You simply compute the gradients by feeding in y.forward (the latest value of y), the weights, and the input x, and then it does the back-propagation for you in a single line. You can then have the loop that allows you to update the weights (i.e. gradient descent!).