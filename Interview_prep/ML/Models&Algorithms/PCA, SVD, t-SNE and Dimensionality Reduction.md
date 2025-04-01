
# PCA

Basic idea of PCA is to eliminate dimensions and make data easy to explore. 

PCA asks how to arrange data points in a line and preserve as much info as possible.

In the example below the data has 2 correlated dimensions. We can use this pattern to reduce dimensions to 1 (draw a line basically).

![Pasted image 20250304154449.png](attachments/Pasted%20image%2020250304154449.png)ionality reduction

Various techniqu![Pasted image 202503041![Pasted image 20250304154555.png](attachments/Pasted%20image%2020250304154555.png)etosa.io/ev/principal-component-analysis/
https://stats.stackexchange.com/questions/2691/making-sense-of-principal-component-analysis-eigenvectors-eigenvalues/140579#140579

Also, Principial components happen to be excactly eigenvectors of the covariance matrix of the feature matrix. The eigenvectors with the highest eigenvalues are the most important PC.
https://www.youtube.com/watch?v=FD4DeN81ODY&ab_channel=VisuallyExplained

---



# Singular Value Decomposition (SVD)
It's a data reduction tool. (e.g. high quality video that needs to be squeezed)
https://gregorygundersen.com/blog/2018/12/10/svd/

**What is SVD?**  
SVD is a powerful matrix factorization technique used to **decompose** a dataset (matrix) into three simpler matrices. It helps in uncovering patterns, reducing dimensions, and solving mathematical problems efficiently.

**Why do we need SVD?**  
SVD is useful in many areas of machine learning and data science, often overlapping with PCA but also offering additional advantages:

### **1. Dimensionality Reduction (Like PCA but More General)**

- SVD can be used for **feature reduction** in high-dimensional datasets.
- Unlike PCA, SVD can be applied directly to **any** matrix (even non-square ones).

### **2. Recommender Systems (Netflix, Amazon, Spotify)**

- SVD is widely used in recommendation engines to break down user-item interaction matrices and predict missing ratings.
- Example: Netflix uses SVD to suggest movies based on user preferences.

### **3. Image Compression**

- SVD allows us to approximate images using only a few **important components** (reducing file size while keeping quality).
- Used in JPEG compression to store images efficiently.

### **4. Natural Language Processing (LSA in Text Analysis)**

- **Latent Semantic Analysis (LSA)** uses SVD to discover hidden relationships between words and documents.
- Helps in topic modeling, search engines, and understanding synonyms.

### **5. Solving Ill-Conditioned Systems**

- In machine learning, sometimes we need to solve systems of equations where direct methods fail.
- SVD provides a **stable way** to invert matrices and handle noisy data.

### **How is SVD Different from PCA?**

- PCA is a special case of SVD where we apply it to the **covariance matrix**.
- SVD, on the other hand, works **directly** on the dataset and can be used in broader applications (e.g., recommender systems).

### **How Does SVD Work at a High Level?**

SVD **breaks down** a large, complex matrix into **three** simpler matrices that capture the core structure of the data. Think of it as breaking a complex process into smaller, easier-to-understand parts.

---

### **Step-by-Step High-Level Intuition**

1. **Start with a Matrix (Data Table)**
    
    - Imagine you have a big dataset (like a user-movie ratings matrix in Netflix).
    - This matrix is often **too large, noisy, or redundant** to work with directly.
2. **Decompose the Matrix into Three Components**
    
    - SVD splits the matrix into three new matrices:
        - **Core patterns (important concepts)**
        - **How data relates to these patterns**
        - **How important each pattern is**
    
    It’s like breaking a song into different musical elements:  
    🎶 **Melody (core patterns)** + 🎸 **Instrument contributions** + 🔊 **Loudness (importance)**
    
3. **Keep Only the Most Important Patterns (Dimensionality Reduction)**
    
    - Just like PCA, SVD ranks components by importance (higher values = more important).
    - We **remove** the less important parts (noise) and keep the strongest patterns.
    - This makes the dataset **smaller but still meaningful**.
4. **Use the Simplified Data for ML Tasks**
    
    - Now, you can use the reduced data for things like:  
        ✅ **Finding similar movies (recommendation engines)**  
        ✅ **Topic modeling in NLP (Latent Semantic Analysis)**  
        ✅ **Image compression (reducing storage while keeping quality)**

---

### **Analogy: Movie Recommendation System 🎬**

Imagine Netflix has a huge **user-movie rating matrix** with thousands of users and movies.

- The full matrix is **too large** and **sparse** (most users rate only a few movies).
- SVD **extracts key factors** (e.g., "Action-Lover" and "Romantic-Movie-Fan").
- Instead of storing millions of ratings, we now store just a few meaningful preferences.
- Netflix can now **predict missing ratings** efficiently.

---


# t-SNE
t-SNE takes high-dimensional dataset and reduces/plots it as a low-dimensional graph, keeping a lot of i![Pasted image 202503081![Pasted image 20250308153328.png](attachments/Pasted%20image%2020250308153328.png)stributed Stochastic Neighbor Embedding) is a technique used to reduce high-dimensional data to two or three dimensions for visualization. It works by first calculating pairwise similarities between data points in high dimensions and then mapping them to a lower-dimensional space, preserving these similarities. 

We need t-SNE primarily for **data visualization**, helping to reveal patterns or clusters in complex, high-dimensional data, making it easier to understand and interpret. However, it’s mainly used for visualization and may not preserve global structures well.

https://www.reddit.com/r/datascience/comments/jzfhwa/tsne_usefulness/
Despite all the inaccuracies of t-SNE, it can be useful to visualise clusters in data. The same goes for text. If you want to see whether word embeddings actually group terms with similar meaning, t-SNE is your friend.
The problem with t-SNE projection is that it's subjective : it depends on a parameter (perplexity) that the user chooses. So that's the reason you cannot use it as input for other algorithms. Even for visualization it''s problematic because your visualization is also subjective but most people ignore this because t-SNE usually gives nice separation for certain parameter values and hence their clusters then look good but this is deceiving. That's why I don't use it and stick with objective methods like PCA, UMAP, neural embeddings even for visualization.