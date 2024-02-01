Gradient Descent with Momentum is an optimization algorithm that uses a momentum term to accumulate past gradients' effects and accelerate the training process. It is especially useful in training deep neural networks, as it helps to overcome some of the challenges associated with the standard gradient descent algorithm. The momentum hyperparameter can be tuned to achieve optimal convergence and faster training.

In standard gradient descent, the model parameters are updated in the opposite direction of the gradient of the loss function with respect to the parameters. The update is proportional to the learning rate, which determines the step size taken in the direction of steepest descent. However, standard gradient descent may have issues with slow convergence or getting stuck in local minima.

Gradient Descent with Momentum addresses these issues by introducing a momentum term that helps the optimizer accumulate past gradients' effects and gain momentum in the correct direction. The momentum term acts as a moving average of the gradients, and it helps to smooth the optimization process, leading to faster convergence and escaping shallow local minima more effectively.

The update equation for Gradient Descent with Momentum is as follows:

1. Initialize a parameter called "velocity" to zero for each model parameter.
2. In each iteration of training, calculate the gradient of the loss function with respect to the parameters.
3. Update the velocity as a weighted average of the previous velocity and the current gradient:
	```python
velocity = beta * velocity + (1 - beta) * gradient
	```
    Here, `beta` is the momentum hyperparameter, usually set between 0 and 1. It controls the influence of the past gradients on the current update.
4. Update the model parameters using the velocity:
	```python
parameters = parameters - learning_rate * velocity
```
    The learning rate determines the step size taken in the direction of the updated velocity.

The momentum term allows the optimizer to gain speed in the relevant directions and dampens oscillations in irrelevant directions. It smoothes the path towards the optimal solution and allows for faster progress along plateaus or shallow regions in the loss landscape.
![[Pasted image 20230720131411.png]]