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

![Pasted image 20250331130339.png](../../../attachments/9ad6ef15ee03c9d91f26ebdeebdd92fe.png)![Pasted image 20250331130356.png](../../../attachments/99741c6e5b1ba5d92347e394cc1839fa.png)![Pasted image 20250331130429.png](../../../attachments/6f28931a9745cfc8edb42db8cafef057.png)![Pasted image 20250331130436.png](../../../attachments/4932592e52ac3ef82beb0dcf6984072d.png)![Pasted image 20250331130456.png](../../../attachments/a1aa480b65b331339e92efe60aa00113.png)

Language modelling training task is used instead of dataset of Q&A as for LangMod the whole internet of texts can be used providing much more data.

![Pasted image 20250331130630.png](../../../attachments/7b0eba98b5259fcec7049d14f8b6f991.png)![Pasted image 20250331130647.png](../../../attachments/411421fc0b4fb0fc18933bddeaa79de9.png)![Pasted image 20250331130656.png](../../../attachments/03dff0243e3968a4d2982c59f1a20072.png)![Pasted image 20250331130704.png](../../../attachments/d3aefe9b18744f315c5473fbc37fbf57.png)![Pasted image 20250331130733.png](../../../attachments/5c4bb0d8fabcbd9390cea0cbaaa9849e.png)![Pasted image 20250331130740.png](../../../attachments/ebf9aaf19de7de0da32b809b5adb0a46.png)



![Pasted image 20250331130812.png](../../../attachments/348f411e613ba5c0741221ca03ed0628.png)
![Pasted image 20250331130830.png](../../../attachments/fb4a937607b8ccbcf1a435f99587f463.png)![Pasted image 20250331130856.png](../../../attachments/ec5c0fd63c8c9a8cb3b70c4fbe8b7e8d.png)![Pasted image 20250331130902.png](../../../attachments/076de8be582b8193590a952ad1dc8e76.png)![Pasted image 20250331130922.png](../../../attachments/aa64cfa2441cef34f6ef9d2a4280cc0f.png)![Pasted image 20250331130947.png](../../../attachments/e346b6a5acbf7d16d26999bcb8944322.png)![Pasted image 20250331131001.png](../../../attachments/d46fd646e575cbca2a1a807f8ef0cd34.png)![Pasted image 20250331131007.png](../../../attachments/e517a94a2fc22a2718ec5eb2afb68000.png)![Pasted image 20250331131021.png](../../../attachments/7e36b1e917209008d9748e7fc42310e7.png)![Pasted image 20250331131050.png](../../../attachments/2adf4923de9c79047a1831ba27bdab10.png)
