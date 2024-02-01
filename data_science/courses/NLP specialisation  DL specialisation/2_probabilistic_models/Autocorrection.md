🏷️: #nlp 

To implement autocorrect, you have to follow these steps:

- Identify a misspelled word
	When identifying the misspelled word, you can check whether it is in the vocabulary. If you don't find it, then it is probably a typo.
- Find strings **n** edit distance away: (these could be random strings)
	 ![[Pasted image 20230613093734.png]]
- Filter candidates: (keep only the real words from the previous steps)
	In this step, you want to take all the words generated above and then only keep the actual words that make sense and that you can find in your vocabulary.
	![[Pasted image 20230613093803.png]]
- Calculate word probabilities: (choose the word that is most likely to occur in that context)
	![[Pasted image 20230613094449.png]]

# Minimum edit distance

**Minimum edit distance allows you to:**

- Evaluate similarity between two strings
- Find the minimum number of edits between two strings
- Implement spelling correction, document similarity, machine translation, DNA sequencing, and more

**Remember that the** **edits include**:

- Insert (add a letter) ‘to’:  ‘top’, ‘two’ …
- Delete (remove a letter) ‘hat’: ‘ha’, ‘at’, ‘ht’
- Replace (change 1 letter to another) ‘jaw’: ‘jar’, ‘paw’, …
	replace has a cost of two because it is delete the letter and then insert the new one

Here is a concrete example where we calculate the cost (i.e. edit distance) between two strings.
![[Pasted image 20230613095932.png]]
Note that as your strings get larger it the computational cost increases exponentially and it gets much harder to calculate the minimum edit distance.

# Minimum edit distance algorithm

When computing the minimum edit distance, you would start with a _source word_ and transform it into the _target word_. Let's look at the following example:
![[Pasted image 20230613101434.png]]
To go from /#→# you need a cost of 0. From p→# you get 1, because that is the cost of a delete. p→s is 2 because that is the minimum cost one could use to get from **p** to **s**. You can keep going this way by populating one element at a time, but it turns out there is a faster way to do this. You will learn about it next.
To populate the following table:
![[Pasted image 20230613103440.png]]
There are three equations:

- **D[i,j] = D[i-1, j] + del_cost:** this indicates you want to populate the current cell (i,j) by using the cost in the cell found directly above.
- **D[i,j] = D[i, j-1] + ins_cost:** this indicates you want to populate the current cell (i,j) by using the cost in the cell found directly to its left. 
- **D[i,j] = D[i-1, j-1] + rep_cost:** the rep cost can be 2 or 0 depending if you are going to actually replace it or not.

At every time step you check the three possible paths where you can come from and you select the least expensive one. Once you are done, you get the following:
![[Pasted image 20230613103523.png]]
To summarize, you have seen the levenshtein distance which specifies the cost per operation. If you need to reconstruct the path of how you got from one string to the other, you can use a backtrace. You should keep a simple pointer in each cell letting you know where you came from to get there. So you know the path taken across the table from the top left corner, to the bottom right corner. You can then reconstruct it.

This method for computation instead of brute force is a technique known as dynamic programming. You first solve the smallest subproblem first and then reusing that result you solve the next biggest subproblem, saving that result, reusing it again, and so on. This is exactly what you did by populating each cell from the top right to the bottom left. It’s a well-known technique in computer science!