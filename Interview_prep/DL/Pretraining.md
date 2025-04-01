https://web.stanford.edu/class/cs224n/slides_w25/cs224n-2025-lecture09-pretraining.pdf

Tokens instead of words allowed to still process the words that were spelled incorrectly or unknown words by separating them in parts.

Previously the pretraining were the word embeddings that were generated in advance. Now we pretrain the whole network. We get a set of params that provide good representation of language. Language modelling task is used (predict the next word) as there are a lot of data for this (basically the internet).

We can get a model that is good in understanding language and then finetune it to specific task on a small labeled dataset.

There are 3 types of architectures:
- Encoder (has bidirectional context)
- Decoder (language modelling)
- Encoder-Decoder (combines good sides for specific tasks)

Encoders:
Get bidirectional context, but can't do language modelling. So we train by masking several words in a sentence with a gap and asking to predict what was there.
BERT: Bidirectional Encoder Representations from Transformers is an example with huge success.
Results are great but not suitable for sequences generation.

Encoder-Decoder:
For encoder-decoders, we could do something like language modeling, but where a prefix of every input is provided to the encoder and is not predicted. The encoder portion benefits from bidirectional context; the decoder portion is used to train the whole model through language modeling. More on slides.

Decoders:
Decoders can be easily finetuned to be a classifier by adding a linear layer classifier on the last word's hidden state as it has a context of the whole sequence. Decoders are good generators.

In-context learning:
Was found that very large LMs can adapt to task if you provide examples of what to do in the prompt. The more examples - the better.

Scaling up models was giving better and better perplexity. The cost of training scales as parameters * training-tokens. A model with 2 times less params but 5 times more data outperformed.

![Pasted image 20250331130339.png](../../attachments/Pasted%20image%2020250331130339.png)![Pasted image 20250331130356.png](../../attachments/Pasted%20image%2020250331130356.png)![Pasted image 20250331130429.png](../../attachments/Pasted%20image%2020250331130429.png)![Pasted image 20250331130436.png](../../attachments/Pasted%20image%2020250331130436.png)![Pasted image 20250331130456.png](../../attachments/Pasted%20image%2020250331130456.png)

Language modelling training task is used instead of dataset of Q&A as for LangMod the whole internet of texts can be used providing much more data.

![Pasted image 20250331130630.png](../../attachments/Pasted%20image%2020250331130630.png)![Pasted image 20250331130647.png](../../attachments/Pasted%20image%2020250331130647.png)![Pasted image 20250331130656.png](../../attachments/Pasted%20image%2020250331130656.png)![Pasted image 20250331130704.png](../../attachments/Pasted%20image%2020250331130704.png)![Pasted image 20250331130733.png](../../attachments/Pasted%20image%2020250331130733.png)![Pasted image 20250331130740.png](../../attachments/Pasted%20image%2020250331130740.png)



![Pasted image 20250331130812.png](../../attachments/Pasted%20image%2020250331130812.png)
![Pasted image 20250331130830.png](../../attachments/Pasted%20image%2020250331130830.png)![Pasted image 20250331130856.png](../../attachments/Pasted%20image%2020250331130856.png)![Pasted image 20250331130902.png](../../attachments/Pasted%20image%2020250331130902.png)![Pasted image 20250331130922.png](../../attachments/Pasted%20image%2020250331130922.png)![Pasted image 20250331130947.png](../../attachments/Pasted%20image%2020250331130947.png)![Pasted image 20250331131001.png](../../attachments/Pasted%20image%2020250331131001.png)![Pasted image 20250331131007.png](../../attachments/Pasted%20image%2020250331131007.png)![Pasted image 20250331131021.png](../../attachments/Pasted%20image%2020250331131021.png)![Pasted image 20250331131050.png](../../attachments/Pasted%20image%2020250331131050.png)
