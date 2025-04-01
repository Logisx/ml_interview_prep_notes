![Pasted image 20250313133610.png](../../../attachments/Pasted%20image%2020250313133610.png)
RNNs were a solution to model and process sequential data. We want to keep context of the previous inputs while predicting. RNNs learn dependencies over time unlike traditional FNN. RNNs allowed to model sequences of any lengths (unlike n-grams) and the model size doesn't increase with sequence length (you just do one more computation for each new input).
But RNNs are slow, in practice the information vanishes after ~7 steps (for words at least). The vanishing/exploding gradient is also an issue.

LSTMs were designed to mitigate the problem of RNN forgetting stuff and the problem of vanishing gradients. LSTMs use gating mechanisms (i/o and forget) to control the flow of information and learn long-term dependencies.

![](../../../attachments/Pasted%20image%2020250401170253.png)

---

![](../../../attachments/Pasted%20image%2020250401170152.png)
### **What is Density Estimation?**

In NLP, **density estimation** means assigning probabilities to sequences of words. A model learns the distribution of words in a language so it can predict how likely a given sentence is.

### **Why is a Language Model a Density Estimator?**

A language model **estimates the probability** of a sequence of words. For example, given a sentence like:  
👉 _"The cat sat on the [MASK]."_  
the model assigns probabilities to possible words like _"mat" (0.7), "floor" (0.2), "roof" (0.05), etc._

Mathematically, it predicts:

P(word∣previous words)P(\text{word} | \text{previous words})P(word∣previous words)

Since it models the probability distribution over language, it acts as a **density estimator** for text.


---

![](../../../attachments/Pasted%20image%2020250401170452.png)
Language models are often called **unsupervised learning** because they don’t require manually labeled data—they learn from raw text by predicting missing words or the next word in a sequence. However, their **training process is very similar to supervised learning**:

- In models like GPT, the task is **next-word prediction**: Given a context, predict the next token. Each training example consists of an input (context) and a target (next word), just like a labeled dataset in supervised learning.
    
- In BERT, **masked language modeling** predicts missing words in a sentence, again using input-target pairs.
    
The key difference is that **labels are derived from the data itself (self-supervision)** rather than being manually annotated. So, while language models are trained like supervised models, they are often categorized as **self-supervised learning** because they generate their own training signals.

---
![](../../../attachments/Pasted%20image%2020250401170711.png)
### **Why do we need word embeddings?**

Word embeddings convert words into dense numerical vectors that capture semantic meaning, unlike one-hot encoding, which is sparse and doesn’t reflect relationships between words. They allow NLP models to generalize better and understand word similarities, improving tasks like search, translation, and sentiment analysis.

---

### **Difference Between Count-Based and Prediction-Based Word Embeddings**

- **Count-Based Embeddings** (e.g., **TF-IDF, LSA, PPMI**): Use word co-occurrence in a corpus to determine word relationships. They rely on **matrix factorization** to extract latent semantic relationships.
    
- **Prediction-Based Embeddings** (e.g., **Word2Vec, GloVe, FastText**): Train neural networks to predict words given a context (or vice versa). These capture deeper semantic relationships and generalize better than count-based methods.
    

---

### **Problems with Context-Based Word Embeddings**

1. **Polysemy (Multiple Meanings)** – Words like _"bank"_ (riverbank vs. financial bank) get a single embedding, which can lead to incorrect interpretations.
    
2. **Context Insensitivity** – Traditional embeddings (e.g., Word2Vec, GloVe) assign fixed vectors to words, ignoring how meaning changes with context. Contextual models (e.g., BERT) address this.
    
3. **Bias in Training Data** – Word embeddings can reflect and amplify biases in their training data, leading to problematic associations.
    
4. **Out-of-Vocabulary (OOV) Words** – Pre-trained embeddings struggle with unseen words or rare words, though subword-based models (like FastText) mitigate this.

---
TODO🚩🚩🚩🚩🚩🚩🚩🚩
![](../../../attachments/Pasted%20image%2020250401171734.png)

---

![](../../../attachments/Pasted%20image%2020250401171901.png)
Definitely could try both. Probably the best approach would be to use a pretrained model and finetune on the dataset. If not possible, n-grams may be better as neural approach need more data usually to generalize well.

---

![](../../../attachments/Pasted%20image%2020250401172144.png)
Increasing n will generally improve performance but will suffer from sparsity. You need exponentially more data to fit increasing n well.

---

![](../../../attachments/Pasted%20image%2020250401172319.png)Softmax for large vocabularies (such as language vocab) is REALLY slow. Cause you need to assign a value to EACH word in your vocab. It needs a lot of memory to store too.

### **How to Fix It**:

1. **Hierarchical Softmax**:  
    One common fix is **hierarchical softmax**, which reduces the complexity of computing softmax. Instead of computing the softmax over the entire vocabulary, it uses a binary tree representation of the vocabulary, reducing the time complexity to O(log⁡V)O(\log V)O(logV) instead of O(V)O(V)O(V). This technique speeds up both training and inference.
    
2. **Negative Sampling**:  
    **Negative sampling** is another popular solution, especially for models like Word2Vec. Instead of updating all words in the vocabulary, the model only updates a small sample of negative (incorrect) words along with the target word. This reduces the number of computations required, speeding up training significantly. Negative sampling doesn't require computing the full softmax but approximates it by only focusing on a few words at each step.
    
3. **Approximate Softmax (e.g., **Recurrent Neural Network with Efficient Softmax**):**  
    Some models use approximate methods to reduce the cost of softmax. For instance, using **subsampling** or **quantization techniques** can approximate the softmax function, improving efficiency without losing too much accuracy.
    
4. **Subword Tokenization**:  
    Using subword-based approaches like **Byte Pair Encoding (BPE)** or **WordPiece** reduces vocabulary size by breaking words into smaller units (subwords or characters). This reduces the number of entries the model needs to process in the softmax layer, lowering the computational burden.

---
![](../../../attachments/Pasted%20image%2020250401172713.png)Levenshtein distance is a measure of the difference between two strings, calculated by counting the minimum number of single-character edits (insertions, deletions, or substitutions) required to transform one string into the other. It’s commonly used in applications like spell-checking, DNA sequence analysis, and natural language processing to quantify how similar or different two strings are.
In this case, the Levenshtein distance between “doctor” and “bottle” is 4: 
1. Change d into b 
2. Change c into t 
3. Change o into l 
4. Change r into e

---
