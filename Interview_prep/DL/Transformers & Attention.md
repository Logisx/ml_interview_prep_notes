## Self-Attention

Attention means that we apply weights to inputs to make the input be more useful by adding context to it.
![[Pasted image 20250324175539.png]]

In text processing we cannot just use "give more attention to words close to the current word" as language doesn't depend on proximity. So we want to find a way to get weights that will add context to our inputs. (t-token, v-embedding vector, y-input with new context)
![[Pasted image 20250324175805.png]]

Each word embedding has some meaning coded in the value in each position. Words that have a similarity are more likely to be connected in context. If we take dot product of 2 vectors it will show us how similar those are and we can use it as a weight.
![[Pasted image 20250324180051.png]]

We get a new vector for a word input, that now contains info about the word relation to each other word.
![[Pasted image 20250324180438.png]]


## Adding weights (Queries, Keys and Values)

Basically here is a flow chart of the process that we repeat for each word (here an example for the 3rd word). But we have no trainable element here and maybe if we add it we can get better results. (S - stands for scores (non normalized dot prod))
![[Pasted image 20250324180848.png]]

Let's add weights to each part where we use our word vectors. To differentiate them we call those parts Query, Key and Value.
![[Pasted image 20250324181108.png]]

Flow chart of the process with weights. Linear layers are just for adding weights, there are no bias terms. Red lines are backpropagation. We can stack those "self attention" blocks together if needed
![[Pasted image 20250324181311.png]]


## Multi-head Attention

We don't have to oversaturate one attention mechanism if we can spread the "cognitive" load on multiple ones.
![[Pasted image 20250324181831.png]]

We can run those attentions in parallel and each will focus on different meanings and contexts. (h - for "head")
We had to add a concat + dense layer in the end to "sum up" the new embeddings we got.
![[Pasted image 20250324182032.png]]

We can stack those blocks and do kinda deep attention (i see a strong correlation with neural nets here). The right side is just a visualization.
![[Pasted image 20250324182246.png]]


## Transformers

Going over "Attention is all you need". The left chart is SCALED self-attention (scaling by 1/sqrt(len(v))).
![[Pasted image 20250324182612.png]]

The original paper was about machine translation. The left side is encoder, the right is decoder. For some other tasks we need only the encoder, so let's focus on those.
![[Pasted image 20250324182841.png]]

We can stack encoder block N times and use N as hyperparam. Number of heads is also a hyperparam.
![[Pasted image 20250324183009.png]]

Positional encoding is a way to add context on where the current word vector is located in a sequence. There multiple ways to do that: you can use some function or train the encoder. But important is that it is another hyperparam of the architecture.
![[Pasted image 20250324183738.png]]

## Benefits of transformers 
- Parallelism: in RNNs to compute each new state we need to know the results of previous 2. In multi-head attention we can compute heads in parallel as they are independent.
- No vanishing gradients problem: in RNNs the gradient flows to the starting states through many other states and vanishes. In multi-head attention it goes directly to each head and updates only 3 weights: keys, values and queries.
![[Pasted image 20250324184059.png]]




In the machine translation case
![[Pasted image 20250325155913.png]]![[Pasted image 20250325155928.png]]