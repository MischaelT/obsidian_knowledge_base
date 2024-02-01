## Gradient Descent

- Gradient descent is a method to find the minimum of a function, it can be applied to functions with multiple dimensions.
![[img/Pasted image 20230515183002.png]]
- In Gradient descent we iteratively calculate this equation, we start off with a guess,  we update the parameter by adding a value proportional to the derivative.
##### When to stop gradient descent?
- We can run gradient descent, for a set number of iterations is a popular way, in this case we run it for 3 iterations.  But for the final iteration we miss the minimum. 
- Another method to stop gradient descent is to see if the loss starts increasing,
## Stochastic Gradient Descent
- In batch gradient descent, we find the parameters w&b that minimize the entire cost function mathematically. However in stochastic gradient Descent we minimise the parameters with respect with just one sample and the line moves accordingly. It can minimise the error for part of the samples and drastically increase the error for the other ones
- The problem of the Stochastic Gradient Descent is that the approximate cost will fluctuate rapidly with each iteration
- 
``` python
def train_model_SGD(iter):
    # Loop
    for epoch in range(iter):
        # SGD is an approximation of out true total loss/cost, in this line of code we calculate our true loss/cost and store it
        Yhat = forward(X)

        # store the loss 
        LOSS_SGD.append(criterion(Yhat, Y).tolist())
        
        for x, y in zip(X, Y):
            
            # make a prediction
            yhat = forward(x)
        
            # calculate the loss 
            loss = criterion(yhat, y)

            # Section for plotting
            get_surface.set_para_loss(w.data.tolist(), b.data.tolist(), loss.tolist())
        
# backward pass: compute gradient of the loss with respect to all the learnable parameters
            loss.backward()
        
            # update parameters slope and bias
            w.data = w.data - lr * w.grad.data
            b.data = b.data - lr * b.grad.data

            # zero the gradients before running the backward pass
            w.grad.data.zero_()
            b.grad.data.zero_()
            
        #plot surface and data space after each epoch    
        get_surface.plot_ps()
```
##### Mini batch gradient descent
- In that method we use a few samples for each iteration. 
- #question Will that method be efficient?
