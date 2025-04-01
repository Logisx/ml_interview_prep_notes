![Pasted image 20250311102656.png](Pasted%20image%2020250311102656.png)
Training/optimizing the model any further will not result in an change of our target metrics. 

A machine learning model reaches convergence when it achieves a state during training in which the loss settles to within an error range around the final value. In other words, a model converges when additional training will not improve the model.

---

![Pasted image 20250311102945.png](Pasted%20image%2020250311102945.png)
![Pasted image 20250311102933.png](Pasted%20image%2020250311102933.png)

---

![Pasted image 20250311103426.png](Pasted%20image%2020250311103426.png)
In statistics and machine learning, the bias–variance tradeoff is the property of a model that the variance of the parameter estimated across samples can be reduced by increasing the bias in the estimated parameters. The bias–variance dilemma or bias–variance problem is the conflict in trying to simultaneously minimize these two sources of error that prevent supervised learning algorithms from generalizing beyond their training set

![Pasted image 20250311104923.png](Pasted%20image%2020250311104923.png)
- The bias error is an error from erroneous assumptions in the learning algorithm. High bias can cause an algorithm to miss the relevant relations between features and target outputs (underfitting). 
- The variance is an error from sensitivity to small fluctuations in the training set. High variance may result from an algorithm modeling the random noise in the training data (overfitting).

![Pasted image 20250311105058.png](Pasted%20image%2020250311105058.png)

In high variance, low bias mode the model performs well on the training set but not on the test set. In this case one can: consider getting more training examples, try smaller set of features, reduce number of model parameters, increase regularization parameter λ, use ensembling.

In low variance, high bias mode, the model performs poorly on both train and test data. In this case one can: add more features, increase number of model parameters, decrease regularization parameter λ, train for longer (deep learning epochs).

---

![Pasted image 20250311105410.png](Pasted%20image%2020250311105410.png)
Cross-validation (CV) is a technique used to assess a model’s performance by splitting the data into multiple subsets.
![Pasted image 20250311105400.png](Pasted%20image%2020250311105400.png)
With large deep-learning datasets, it’s very computationally expensive to perform K-fold / Leave-P-Out cross validation. These types of cross validation are most useful when the dataset is on the order of hundreds of examples. Therefore, in practice people usually perform the holdout method by splitting the dataset into train/val/test.

---

![Pasted image 20250311105629.png](Pasted%20image%2020250311105629.png)
If a model is trained and tested on the same data, it will likely perform very well on that data but fail to generalize to new, unseen data. This is because the model may simply memorize patterns from the training data rather than learning generalizable features. This leads to overfitting, where the model has low training error but high error on new data.

A validation set is used to tune hyperparameters and prevent overfitting before evaluating the final model on the test set.
If we used the test set for tuning, it would no longer provide an unbiased estimate of the model’s generalization.

3)
Probably: 
- Validation set has a different distribution than the train and test sets
- Data leakage in test set
- Validation set is too small or noisy

It might be the case that the train set provides good enough coverage for the test distribution, but not for the entirety of the validation distribution. The cause might have been a bug in our splitting procedure, or we might simply have been unlucky with the random draws. A quick fix would be to check the implementation again, and perform a new split with a different random seed.

![Pasted image 20250311113315.png](Pasted%20image%2020250311113315.png)

---

![Pasted image 20250311113323.png](Pasted%20image%2020250311113323.png)
How target is distributed in your data? How have you evaluated performance and done cross-validation?

I'd respond with skepticism and ask for more details. A **99.99% accuracy** in cancer prediction sounds too good to be true, and there's a high chance the model isn’t actually useful.

First, I'd check how the model handles **actual cancer cases**. In medical datasets, cancer is usually rare, so a model could just predict "no cancer" for everyone and still get 99.99% accuracy—while completely failing to detect real cases. That’s why **accuracy alone is misleading**. Instead, I’d want to see metrics like **recall (sensitivity)** to know how well it catches actual cancer cases.

I’d also ask how the model was tested. Did it perform well on real-world, unseen data, or is it just memorizing the training set? Overfitting is a big issue in medical AI. And even if the numbers look good, does it actually help doctors in a clinical setting? Are the predictions interpretable?

Before trusting this claim, I’d need a full evaluation, including false negatives, real-world testing, and clinical validation.

---

![Pasted image 20250311113639.png](Pasted%20image%2020250311113639.png)
F1 is better when dealing with imbalanced datasets. Accuracy can be misleading if one class dominates, while F1 considers both false positives and false negatives, providing a balanced evaluation. But F1 is less imterpretable.
![Pasted image 20250311114039.png](Pasted%20image%2020250311114039.png)

---

![Pasted image 20250311114052.png](Pasted%20image%2020250311114052.png)
![Pasted image 20250311114616.png](Pasted%20image%2020250311114616.png)
The model is very conservative, in the sense that it rarely outputs the positive class (large number of False Negatives). The goal of improving the model’s performance might be achieved by being more aggressive, and predicting the positive class more often. One way to do this is by lowering the threshold for which we predict a positive vs. negative class.

**Optimize Trade-off Between Precision and Recall**

- Tune the decision threshold based on the problem's needs (e.g., higher recall for medical diagnosis).
- Use different metrics like **ROC-AUC** or **PR curve** to find a better balance.

---

![Pasted image 20250311114902.png](Pasted%20image%2020250311114902.png)![Pasted image 20250311115912.png](Pasted%20image%2020250311115912.png)![Pasted image 20250311115921.png](Pasted%20image%2020250311115921.png)

---

TODO🚩🚩🚩🚩🚩🚩🚩🚩
![Pasted image 20250311120042.png](Pasted%20image%2020250311120042.png)

---

![Pasted image 20250311120352.png](Pasted%20image%2020250311120352.png)
In general, (R)MSE is more sensitive to outliers than MAE, and the model will be more skewed towards them. Using one loss over the other typically comes down to how important is it to perform well on outliers. In many circumstances it makes sense to give more weight to points further away from the mean. For example, being off by 10 is more than twice as bad as being off by 5. In such cases RMSE is a more appropriate measure of error. 66 If being off by 10 is just twice as bad as being off by 5, then MAE is more appropriate.

---

TODO🚩🚩🚩🚩🚩🚩🚩🚩
![Pasted image 20250311120422.png](Pasted%20image%2020250311120422.png)

