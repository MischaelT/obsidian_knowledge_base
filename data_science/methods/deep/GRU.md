🏷️: #gru #deep_learning #sequence_models

![[Pasted image 20230903100613.png]]

![[Pasted image 20230903100627.png]]

The first gate Γ�Γu​ allows you to decide how much you want to update the weights by. The second gate Γ�Γr​, helps you find a relevance score. You can compute the new ℎh by using the relevance gate. Finally you can compute _h,_ using the update gate. GRUs “decide” how to update the hidden state. GRUs help preserve important information.

GRUs take more time to compute. This means that training and prediction would take more time for a GRU than for a vanilla #rnn. However, GRUs allow you to propagate relevant information even for long sequences, so when selecting an architecture for NLP you should assess the tradeoff between computational time and performance.