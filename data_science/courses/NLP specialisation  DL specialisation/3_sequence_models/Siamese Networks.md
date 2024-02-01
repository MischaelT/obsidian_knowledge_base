A **Siamese neural network** (sometimes called a **twin neural network**) is an [artificial neural network](https://en.wikipedia.org/wiki/Artificial_neural_network "Artificial neural network") that uses the same weights while working in tandem on two different input vectors to compute comparable output vectors. Often one of the output vectors is precomputed, thus forming a baseline against which the other output vector is compared. This is similar to comparing [fingerprints](https://en.wikipedia.org/wiki/Fingerprint "Fingerprint") but can be described more technically as a distance function for [locality-sensitive hashing]
![[Pasted image 20230903141053.png]]

These two sub-networks are sister-networks which come together to produce a similarity score. Not all Siamese networks will be designed to contain LSTMs. One thing to remember is that sub-networks share identical parameters. This means that you **only** need to train one set of weights and not two.

The output of each sub-network is a vector. You can then run the output through a cosine similarity function to get the similarity score. In the next video, we will talk about the cost function for such a network.

It is best to describe what a Siamese network is through an example.
![[Pasted image 20230903134334.png]]
Note that in the first example above, the two sentences mean the same thing but have completely different words. While in the second case, the two sentences mean completely different things but they have very similar words.

**Classification**: learns what makes an input what it is.
**Siamese Networks**: learns what makes two inputs the same

Here are a few applications of siamese networks:
![[Pasted image 20230903134355.png]]

### Cost function
![[Pasted image 20230903141729.png]]

Note that when trying to compute the cost for a siamese network we use the triplet loss. The triplet loss usually consists of an Anchor and a Positive example. Note that the anchor and the positive example have a cosine similarity score that is very close to one. On the other hand, the anchor and the negative example have a cosine similarity score close to -1. Now we are ideally trying to optimize the following equation:
![[Pasted image 20230903142018.png]]
### Triplet loss

**Triplet loss** is a [loss function](https://en.wikipedia.org/wiki/Loss_function "Loss function") for [machine learning](https://en.wikipedia.org/wiki/Machine_learning "Machine learning") algorithms where a reference input (called anchor) is compared to a matching input (called positive) and a non-matching input (called negative). The distance from the anchor to the positive is minimized, and the distance from the anchor to the negative input is maximized.

The intuition behind the simplest loss function that uses triplets is to minimize the difference between the similarity of A and N. And the similarity of A and P. This is equivalent to maximizing the similarity between the anchor and the positive example. While minimizing the similarity between the anchor and their associated negative examples. You already know that as a difference gets bigger or smaller along the x axis, the loss gets respectively bigger or smaller along the y axis. But no doubt when the diff is less than zero, the loss decreases towards negative values. And for some similarity functions, this simple loss function can even go to negative infinity.

![[Pasted image 20230903143805.png]]

to solve that problem, we can limit our loss function in the following way:
![[Pasted image 20230903143833.png]]
That would be the plot: 
![[Pasted image 20230903143822.png]]
However, you don't want your model to have a barely acceptable performance. 
You need your model to be confident enough and distinguish between negative and positive values with ease. So you need your model to learn until the model achieves a specific value for the difference between similarities. That's why you would want to use a margin alpha industry put loss.
![[Pasted image 20230903143225.png]]
![[Pasted image 20230903144102.png]]
#### Selecting a triplets
Selecting triplets, A, P, and N for training involves two steps. First, select a pair of questions that are known to be duplicates to serve as the anchor and positive example from the training set. Second, select a question that is known to be different in meaning from the anchor to form the anchor and the negative pair. If you were to select triplets randomly, you would be likely to choose anchors, positives, and negative examples that will lead to losses close to zero. And remember that the network will have nothing to learn from those triplets when the loss gets to zero. So you can train more efficiently if you choose triplets that create a challenge to the model. 
So instead of selecting random triplets, you specifically select so called hard triplets. These are triplets that are more difficult for the model to tell apart the negative and the positive example. In those, the similarity between anchor and negative is very close too but they are still smaller than the similarity between anchor and positive. When the model encounters a hard triplet, it needs to adjust its way to yield similarities that line up with the real world labels. So by selecting hard triplets, you focus the training process and the problematic cases. So the model gets the most information on how to improve its performance.


### Computing the cost

To compute the cost, we will prepare the batches as follows:
![[Pasted image 20230903154126.png]]

Note that each example, has a similar example to its right, but no other example means the same thing. We will now introduce hard negative mining.
![[Pasted image 20230903154233.png]]
Each horizontal vector corresponds to the encoding of the corresponding question. Now when you multiply the two matrices and compute the cosine, you get the following:
![[Pasted image 20230903154246.png]]

The diagonal line corresponds to scores of similar sentences, (normally they should be positive). The off-diagonals correspond to cosine scores between the anchor and the negative examples.
Now that you have the matrix with cosine similarity scores, which is the product of two matrices, we go ahead and compute the cost.
![[Pasted image 20230903154850.png]]
We now introduce two concepts, the **mean_neg,** which is the mean negative of all the other off diagonals in the row, and the **closest_neg,** which corresponds to the highest number in the off diagonals.
![[Pasted image 20230903154922.png]]
### One-shot learning

Imagine you are working in a bank and you need to verify the signature of a check. You can either build a classifier with K possible signatures as an output or you can build a classifier that tells you whether two signatures are the same.
![[Pasted image 20230903155141.png]]
Hence, we resort to one shot learning. Instead of retraining your model for every signature, you can just learn a similarity score as follows:
![[Pasted image 20230903155151.png]]
### Training / Testing

After preparing the batches of vectors, you can proceed to multiplying the two matrices. Here is a quick recap of the first step:

![[Pasted image 20230903155319.png]]

The next step is to implement the siamese model as follows:![[Pasted image 20230903155331.png]]
Finally when **testing**:

1. Convert two inputs into an array of numbers
2. Feed it into your model
3. Compare 𝒗1,𝒗2 using cosine similarity
4. Test against a threshold �τ

``` python
# UNQ_C3 (UNIQUE CELL IDENTIFIER, DO NOT EDIT)
# GRADED FUNCTION: TripletLossFn
def TripletLossFn(v1, v2, margin=0.25):
    """Custom Loss function.

    Args:
        v1 (numpy.ndarray): Array with dimension (batch_size, model_dimension) associated to Q1.
        v2 (numpy.ndarray): Array with dimension (batch_size, model_dimension) associated to Q2.
        margin (float, optional): Desired margin. Defaults to 0.25.

    Returns:
        jax.interpreters.xla.DeviceArray: Triplet Loss.
    """
    ### START CODE HERE (Replace instances of 'None' with your code) ###
    # use fastnp to take the dot product of the two batches (don't forget to transpose the second argument)
    scores = np.dot(v1, v2.T) # pairwise cosine sim    
    # calculate new batch size
    batch_size = len(scores)
    # use fastnp to grab all postive `diagonal` entries in `scores`
    positive = fastnp.diagonal(scores)  # the positive ones (duplicates)
#     print(positive)
    # subtract `fastnp.eye(batch_size)` out of 1.0 and do element-wise multiplication with `scores`
    negative_zero_on_duplicate = scores * (1 - fastnp.eye(batch_size))
    # use `fastnp.sum` on `negative_zero_on_duplicate` for `axis=1` and divide it by `(batch_size - 1)`
    mean_negative = np.sum(negative_zero_on_duplicate, axis=1) / (batch_size-1)
    # create a composition of two masks: 
    # the first mask to extract the diagonal elements, 
    # the second mask to extract elements in the negative_zero_on_duplicate matrix that are larger than the elements in the diagonal
    print(fastnp.eye(batch_size)==1)
    mask_exclude_positives = (fastnp.eye(batch_size)==1)|(negative_zero_on_duplicate > positive.reshape(1, batch_size))
    
    print(negative_zero_on_duplicate)
    print(positive)
    print(mask_exclude_positives)
    # multiply `mask_exclude_positives` with 2.0 and subtract it out of `negative_zero_on_duplicate`
    negative_without_positive = negative_zero_on_duplicate - mask_exclude_positives * 2
    # take the row by row `max` of `negative_without_positive`. 
    # Hint: negative_without_positive.max(axis = [?])  
    closest_negative = negative_without_positive.max(axis = 0) 
    # compute `fastnp.maximum` among 0.0 and `A`
    # where A = subtract `positive` from `margin` and add `closest_negative`
    # IMPORTANT: DO NOT create an extra variable 'A'
    triplet_loss1 = np.max(margin - positive + closest_negative, 0)
    # compute `fastnp.maximum` among 0.0 and `B`
    # where B = subtract `positive` from `margin` and add `mean_negative`
    # IMPORTANT: DO NOT create an extra variable 'B'
    triplet_loss2 = np.max(margin - positive + mean_negative, 0)
    # add the two losses together and take the `fastnp.sum` of it    
    triplet_loss = np.sum(triplet_loss1+triplet_loss2)    
    ### END CODE HERE ###
    
    return triplet_loss
```