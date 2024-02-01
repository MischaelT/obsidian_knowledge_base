
N]gram  models have many limitations one of them is that in order to capture dependencies between words far away from each other, your model would have to account for conditional probabilities in very long sequences of words. 
This could be difficult to estimate with us correspondingly large corporate, even in the case of large corporal, your model would need a lot of space and RAM to store the probabilities of all the possible combinations.

Previously, we tried using traditional language models, but it turns out they took a lot of space and RAM. For example, in the sentence below:

![[Pasted image 20230901164743.png]]

An N-gram _(trigram)_ would only look at "did not" and would try to complete the sentence from there. As a result, the model will not be able to see the beginning of the sentence "I called her but she". Probably the most likely word is _have_ after "did not". RNNs help us solve this problem by being able to track dependencies that are much further apart from each other. As the RNN makes its way through a text corpus, it picks up some information as follows:
![[Pasted image 20230901164828.png]]

Note that as you feed in more information into the model, the previous word's retention gets weaker, but it is still there. Look at the orange rectangle above and see how it becomes smaller as you make your way through the text. This shows that your model is capable of capturing dependencies and remembers a previous word although it is at the beginning of a sentence or paragraph. Another advantage of RNNs is that a lot of the computation shares parameters.

RNNs could be used in a variety of tasks ranging from machine translation to caption generation. There are many ways to implement an RNN model:
- One to One: given some scores of a championship, you can predict the winner.
- One to Many: given an image, you can predict what the caption is going to be.
- Many to One: given a tweet, you can predict the sentiment of that tweet.
- Many to Many: given an english sentence, you can translate it to its German equivalent.
### Math behind RNN
![[Pasted image 20230901171115.png]]

![[Pasted image 20230901171227.png]]

![[Pasted image 20230901171338.png]]

![[Pasted image 20230901171413.png]]