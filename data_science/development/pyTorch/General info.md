- in pytorch every network consists of tensors, n-dim array
- To make a result pytorch will apply several tensor operations

## 1-d Tensors
- tensor can consist of different types
```python
import torch
a = torch.tensor([1,2,3,4])
a[0] = 1
a.dtype = integer
a.type()
a.ndimensions() // number of dimensions

a_col = a.view(num_row,num_col) // to change the dimensions of a tensor
//the ndimensions() would give 2

torch.from_numpy()
torch_tensor.numpy()
```
- tensors can be sliced and tensors are changeable
- Operations over the tensors:
	- Vector addition and subtraction. Tensors in this case must be the same type
	- Multiply tensor by a scalar
	- Product of two tensors: just multiply element by element
	- dot product: u_transposed * v: how the tensors are similar to each other.
	- we can apply functions to torch.tensors
- 'torch.linspasce(start, stop, number)' : generates number of evenly specified values from start to stop

## 2-d Tensors

```python
a = [[1,2,3], [1,2,3]]
a.ndimensions :: 2
a.shape() :: (2, 3)
a.size() :: (2, 3)
```
### Indexing and slicing 

![[img/Pasted image 20230514153037.png]]

- `A[row][col]`
### Differentiation
![[img/Pasted image 20230514154016.png]]