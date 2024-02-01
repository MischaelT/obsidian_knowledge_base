🏷️: #classification

![[img/Pasted image 20230517132036.png]]
- The K-Nearest Neighbors algorithm is a classification algorithm that takes a bunch of labeled points and uses them to learn how to label other points. 

- This algorithm classifies cases based on their similarity to other cases. In K-Nearest Neighbors, data points that are near each other are said to be neighbors.
### What is the best K?
- leave some values of the data to test sample. Iterate over quantity of neigbours, find one where presision is the best.
- Can be used to predict continious variables. So it can be used for regression models
  
### Evaluation Metrics in Classification

- jakkart index    
	![[img/Pasted image 20230517134625.png]]
- F1 Score
	![[img/Pasted image 20230517135144.png]]
	Precision: how many ground truths values among all values predicted as positives
	Recall: how many ground truths values among all positives.(including the ones that model predicted as negatives)
- Log loss
	![[img/Pasted image 20230517135530.png]]

### Desision trees

![[img/Pasted image 20230517135910.png]]
- ![[img/Pasted image 20230517140244.png]]
- In fact, the method uses recursive partitioning to split the training records into segments by minimizing the impurity at each step. Impurity of nodes is calculated by entropy of data in the node.
- Entropy is the amount of information disorder or the amount of randomness in the data. The entropy in the node depends on how much random data is in that node and is calculated for each node.
- ![[img/Pasted image 20230517140454.png]]
- Which one is better at the first attribute to divide the data-set into two branches? The answer is the tree with the higher information gain after splitting.
- 