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
![](../../../attachments/Pasted%20image%2020250402132426.png)
https://youtu.be/M05L1DhFqcw?si=Yc85Bp2IqQDIG4WL
”the closer a machine translation is to a professional human translation, the better it is” – this is the central idea behind BLEU
The advantages of BLEU are: • Fast and simple to compute. • Widely used in both industry and academia. In contrast, its disadvantages are: • Doesn’t consider meaning. • Doesn’t incorporate sentence structure. • Struggles with non-English languages. • Hard to compare scores with different tokenizers.

---

![](../../../attachments/Pasted%20image%2020250402132940.png)
### **Understanding Entropy in Language Models**

Entropy measures the uncertainty of a model’s predictions. Lower entropy indicates a more confident and likely better model.

- **Character-Level Entropy (2)**: Measures uncertainty at the character level. A lower value suggests the model is confident in predicting the next character.
    
- **Word-Level Entropy (6)**: Measures uncertainty at the word level. A higher value suggests more uncertainty in predicting the next word.
### **Comparing the Models**

Since entropy is not directly comparable across different granularities (character vs. word), we should convert one to the other for a fair comparison. The approximate relationship is:

Hword≈Hchar×avg word lengthH_{\text{word}} \approx H_{\text{char}} \times \text{avg word length}Hword​≈Hchar​×avg word length

Assuming an **average word length of 4 characters**, the expected word-level entropy for Model A would be:

Hword for Model A≈2×4=8H_{\text{word for Model A}} \approx 2 \times 4 = 8Hword for Model A​≈2×4=8

Since **Model A's estimated word-level entropy (8) is higher than Model B's actual word-level entropy (6)**, Model B is likely the better model.

### **Deployment Decision**

I would choose **Model B (word-level entropy = 6)** for deployment because it exhibits lower overall uncertainty in predicting words, making it more reliable for practical use.

https://www.reddit.com/r/MLQuestions/comments/s5yexj/on_the_same_test_set_lm_model_a_has_a/
if this were model A with a word-level entropy that's lower than model B's word-level entropy, you could say model B has a higher degree of randomness. This isn't a good or bad thing on itself. Less randomness can mean less errors, but it can also mean something like mode collapse, where the model only produces a few "well-known" outputs, and ignores other possibilities for exploration/higher recall.

Based just on an entropy score, without knowing the task at hand or any other performance metrics, you can't really answer this question IMO.

---

![](../../../attachments/Pasted%20image%2020250402133532.png)
I would make **Corpus A case-sensitive** for Named Entity Recognition (NER) training.

### **Reasons for Case Sensitivity in NER**

1. **Proper Nouns Are Often Capitalized** – Many named entities (e.g., **"Apple"** the company vs. **"apple"** the fruit) rely on capitalization to convey meaning. Removing case information would make it harder for the model to differentiate them.
    
2. **Contextual Importance** – In many languages, capitalization provides cues about entity types (e.g., "Paris" as a location vs. "paris" if it were a lowercase common noun).
    
3. **Standard NER Models Use Case Information** – Pretrained NER models like spaCy, BERT-based NER, and CRF-based models leverage case distinctions to improve accuracy.
    
4. **Retaining More Information Is Better** – A case-sensitive corpus retains flexibility; you can always lowercase the text later if needed, but you **cannot recover lost case information** if you start with a case-insensitive dataset.
    

### **When Might Case-Insensitivity Be Useful?**

- If working with **informal text (e.g., social media, chat logs, or noisy OCR)** where capitalization is inconsistent.
    
- If dealing with **languages/scripts that don’t use case distinctions** (e.g., Chinese, Arabic).
### **Conclusion**

For most NER tasks, **a case-sensitive corpus is the better choice**, as it preserves valuable information that helps disambiguate named entities.


---

![](../../../attachments/Pasted%20image%2020250402133700.png)Removing stop words can hurt sentiment analysis because some stop words carry important sentiment cues (e.g., _"not"_ in _"not good"_). They also help preserve context and word relationships, which models—especially deep learning ones—use to understand sentiment. Removing them can distort meaning, weaken sentiment intensity, and disrupt models like BERT that rely on full sentence structures. However, for simpler models like Naïve Bayes, removing stop words might help by reducing noise.

### **When It Might Help:**

- For **simple models (Naïve Bayes, SVMs)** that rely only on word counts, removing stop words can reduce noise.
    
- In **domain-specific tasks**, where stop words don’t add sentiment (e.g., financial reports).

---

![](../../../attachments/Pasted%20image%2020250402142920.png)
Many models use relative position embeddings because they allow for better generalization to longer sequences and are independent of the fixed sequence length. Unlike absolute embeddings, which are limited to a predefined token range, relative embeddings focus on token distances, making them more flexible and capable of handling variable-length inputs.
Absolute embedding may be useful when word position **strictly matters**, like in certain positional encodings for structured data (e.g., DNA sequences, music processing).

---

![](../../../attachments/Pasted%20image%2020250402143253.png)
https://www.reddit.com/r/MachineLearning/comments/1d2iurw/d_should_the_embedding_matrix_and_final/
https://www.reddit.com/r/MachineLearning/comments/1eqm0lr/r_why_and_when_tying_embedding_a_story/
This was popular when models were at such a size that the embeddings were a significant portion (sometimes the majority) of the parameters. Tieing reduced the overall parameter count significantly. With larger models isn't necessary anymore.