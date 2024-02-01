#linear_algebra #linear_regression #regularisation 

- For training logisti regression we usually do this method that includes the lambda - learning rate.
![[Pasted image 20230907144231.png]]
- We can put b here as well, but it makes a little sense. Because w would be much bigger since it is n dimensional, whereas b is one-dimensional
![[Pasted image 20230907144914.png]]
- In case of matrices, we find so-called the Frobenius norm
![[Pasted image 20230907153407.png]]
- **Cost Function in Neural Networks** In a neural network, our cost function is a function of all the parameters, denoted as w[1], b[1] through w[capital L], b[capital L], where capital L represents the number of layers in the neural network. The cost function can be defined as the sum of losses over our m training examples. To incorporate L2 regularization, we add a regularization term: lambda over 2m times the squared norm of all the parameters w.
  **Defining the Squared Norm** The squared norm of a matrix is given by the sum of the squares of its elements. For our parameter matrix w, which is of dimensions n[l] by n[l minus 1], the indices for this summation are as follows: i ranges from 1 through n[l minus 1], and j ranges from 1 through n[l]. This matrix norm is referred to as the Frobenius norm, denoted as ||w||_F.
- **Gradient Descent with Regularization** Previously, in standard gradient descent, we computed dw (the derivative of the cost function with respect to w) using backpropagation. Then, we updated w as w minus the learning rate times dw. With the addition of the regularization term, we modify this update step.
  Now, we update dw by adding lambda over m times w to it. The update for w[l] becomes w[l] minus alpha (learning rate) times this new dw[l]. This updated dw[l] still correctly represents the derivative of the cost function with respect to the parameters, even with the regularization term.

- **L2 Regularization as Weight Decay** L2 regularization is sometimes referred to as "weight decay." If we substitute our updated dw[l] into the update equation, we get:
  w[l] gets updated as w[l] times (1 - alpha * lambda / m) minus alpha times the gradient from backpropagation.
  The term (1 - alpha * lambda / m) is slightly less than 1, which means you're effectively reducing the size of the weight matrix w[l]. This concept is why L2 regularization is called "weight decay." It's akin to standard gradient descent but with an additional step that slightly shrinks the weight matrix.

So, in summary, L2 regularization in a neural network involves adding a regularization term to the cost function and updating the weights using a modified gradient descent step that introduces weight decay, ultimately preventing overfitting.