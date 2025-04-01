L1 distance (Lasso): sum(abs(x1-x2))
L2 (Ridge): sqrt(sum((x1-x2)^2))

L2 prefers many medium disagreements to a big one (outlier)

We add sum of weights in the matrix (or squared for L2) and add it to loss function to prevent overfitting. This sum is multiplied by coef that is hyperparam.
![Pasted image 20250228204207.png](attachments/Pasted%20image%2020250228204207.png)
