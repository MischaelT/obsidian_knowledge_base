The LSTM allows your model to remember and forget certain inputs. It consists of a cell state and a hidden state with three gates. The gates allow the gradients to flow unchanged. You can think of the three gates as follows:

**Input gate:** tells you how much information to input at any time point.

**Forget gate:** tells you how much information to forget at any time point.

**Output gate:** tells you how much information to pass over at any time point.

![[Pasted image 20230903114047.png]]

Sigmoid activation functions with different trainable parameters are applied to the input and previous states for the three gates. The use of the sigmoid ensures that the values for the gates are between 0 and 1 In practice, the values encountered in the vectors corresponding to each gate are very close to either zero or one. With a value of zero, the gate is closed, so information doesn't get through. While a value of one will let information flow freely.

Another significant computation made inside an LSTM is the candidate cell state. To get that, you have to transform the information from the previous hidden states and the current inputs. A hyperbolic tangent activation function is typically used in different implementations. It shrinks the information from the previous hidden states and the current inputs to be between negative 1 and 1. This nonlinear transformation has been used in the past because it improves training performance.

With the forget and input gate and the candidate cell state, you can update the cell state. To get the new cell state, you add the information from the candidate cell state that passes through the input gates to the cell state information that passes through the forget gate. Finally, you can compute the new hidden state used to produce output at a given step. To get the new hidden state, you pass transformed information from the new cell state through the output gate. Note that here the new cell state first passes through a hyperbolic tangent activation. Nevertheless, some LSTM architectures ignore this information and pass the new cell state directly through the output gate.

![[Pasted image 20230903114811.png]]


