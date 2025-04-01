https://web.stanford.edu/class/cs224n/slides_w25/cs224n-2025-lecture01-wordvecs1.pdf
https://web.stanford.edu/class/cs224n/slides_w25/cs224n-2025-lecture02-wordvecs2.pdf

Before 2012 one-hot vectors to represent words were popular.
You basically do a vocab of words and in a one hot vector of the word the 1 is in place of this word in the vocab.

**Problems**:

- The vocabulary size can be very large.
- Does not show any association between words as any two one-hot vectors are orthogonal. e.g., in web search, "seattle motel" != "seattle hotel".


## Word2vec basic ideas
- We have a large corpus (“body”) of text
- Every word in a fixed vocabulary is represented by a vector
- Go through each position t in the text, which has **a center word c** and **context (“outside”) words o**
- Use the similarity of the word vectors for c and o to calculate the probability of o given c (or vice versa)
- Keep adjusting the word vectors to maximize this probability
- Learning: Update vectors so they can predict actual surrounding words better

![[Pasted image 20250317183006.png]]
We do gradient descent on a loss function to optimize the parameters of word vectors.
There are 2 vectors for each word:
- vector if the word is the center word
- vector if the word is in the context window

More math:https://github.com/jaaack-wang/Notes-for-Stanford-CS224N-NLP-with-Deep-Learning/blob/main/lecture1-Intro%20and%20Word%20Vectors/%20%5BJack's%20Notes%5D%201-Intro%20and%20Word%20Vectors.ipynb

The size of vectors is defined impirically (100/300 dimensions for ex.)

![[Pasted image 20250317184010.png]]

**Word2Vec** (by Google) is **predictive**: It learns embeddings by training a shallow neural network to predict the context of words. It comes in two variants:

- **CBOW (Continuous Bag of Words):** Predicts a word from its surrounding words.
- **Skip-gram:** Predicts surrounding words given a target word.

## GloVe
**GloVe** (by Stanford) is **count-based**: It constructs a word co-occurrence matrix and factorizes it to learn embeddings based on global word co-occurrence statistics.


## Word2vec vs GloVe
- **Word2Vec** is good at capturing local context, as it relies on moving windows of words in a corpus. Tends to perform better in tasks where predicting context is crucial, like language modeling.
- **GloVe** captures global co-occurrence, making it more robust in understanding overall word relationships. Usually gives better word similarity results because it captures overall co-occurrence patterns better.

### **Which One to Use?**

- Use **Word2Vec** when you need dynamic embeddings that adapt well to specific tasks (e.g., fine-tuning for NLP models).
- Use **GloVe** when you need high-quality pre-trained embeddings that capture broad semantic meanings efficiently.