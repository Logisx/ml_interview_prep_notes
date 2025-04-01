
![Pasted image 20250306110017.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250306110017.png)3061![Pasted image 20250306110640.png](../../../../Q&A/attachments/Pasted%20image%2020250306110640.png)2503061![Pasted image 20250306111836.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250306111836.png)3061![Pasted image 20250306111853.png](../../../../Q&A/attachments/Pasted%20image%2020250306111853.png)1![Pasted image 20250306111906.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250306111906.png)2503061![Pasted image 20250306112149.png](../../../../Q&A/attachments/Pasted%20image%2020250306112149.png) use this principle to select between two different models. Given two models with the same generalization error, the simpler one should be preferred because simplicity is desirable. Given two models with the same training-set error, the simpler one should be preferred because it is likely to have a lower generalizatio![Pasted image 202503061![Pasted image 20250306112432.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250306112432.png)1![Pasted image 20250306112445.png](../../../../Q&A/attachments/Pasted%20image%2020250306112445.png)2503061![Pasted image 20250306112506.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250306112506.png) availability of Big Data because of raise of the internet and web.
- Improved hardware (GPU, TPU)
- Research found better architectures/algorithms (CNNs, Transformers, ![Pasted image 202503061![Pasted image 20250306113308.png](../../../../Q&A/attachments/Pasted%20image%2020250306113308.png)networks** can learn hierarchical representations. Lower layers capture simple patterns (e.g., edges), while deeper layers combine them into more complex structures (e.g., shapes, objects). This enables more efficient representation learning.
In a deep network, neurons in early layers can be reused multiple times by later layers, enabling parameter sharing and more efficient function approximation.
**Multiple layers are much better at generalizing because they learn all the intermediate features** between the raw data and the high-level classifica![Pasted image 202503061![Pasted image 20250306141547.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250306141547.png)ersal Approximation Theorem states that a neural network with a single hidden layer can approximate any continuous function for inputs within a specific range. While the theorem guarantees that the network can approximate any function, it does not provide specific guidance on the number of neurons or the complexity required to achieve a certain level of accuracy. A low error can be achieved by an exponentially large number of neurons but such a wide model is prone to overfitting and difficult to train.

Resources for deep understanding:
http://neuralnetworksanddeeplearning.com/chap4.html
https://medium.com/towards-data-science/can-neural-networks-really-learn-any-function-65e106![Pasted image 20250306142159.png](ml_interview_prep_notes/attachments/Pasted%20image%2020250306142159.png)6142159.png)
A **saddle point** is a point in the loss landscape where the gradient is **zero**, but it is neither a local minimum nor a local maximum. Instead, it has at least one direction where the loss decreases and another where it increases.
Local minima are points in the function where it reaches the **minimum** value in its neighbourhood. **It may or may not be the minimum** for the whole function.

Saddle points cause more problems as they slow down optimization (cause gradient is near zero) and there are plenty of them in high-dimensional landscapes. Moreover, gradient descent can escape local min easily.
**Momentum-based optimization (e.g., Adam, RMSprop)** helps escape saddle points by accumulating gradients over time.

Empirically, it has been shown that **saddle points** can cause more problems than **local minimum** for training models. For a point to truly be a local minimum of the loss function, it has to be a local minimum in all directions, where each direction is specified by one of the parameters of the network.Given that we usually train million-  
(or even billion-) parameter models, it is much more likely that at least one direction displays different behavior than the others, as opposed to all of them displaying the same behavior. Therefore, we can  
conclude that local minima are not as common.

In practice, networks trained by Stochastic Gradient Descent almost always escapes from the local minima. Since we are calculating the loss wrt. the current batch (and not the entire dataset), we are not truly traversing the original loss landscape, but a proxy of it. And if we eventually get stuck in a local minima / saddle point in the loss landscape (or even its current proxy), in the next iteration we are optimizing over a different batch, which is a different proxy of the loss, and therefore will slightly nudge us in a different direction. This regularization effect is a huge reason why we are able to train neural networks that show remarkable capabili![Pasted image 202503061![Pasted image 20250306143844.png](../../../../Q&A/attachments/Pasted%20image%2020250306143844.png) are quantities that are optimized by the model during the training process (e.g. weights of a neural network). Hyperparameters are quantities related to the learning procedure, which are not optimized during training, but are set by the user before the training starts (e.g. learning rate of the optimizer).

Hyperparameter tuning consists of finding a set of optimal hyperparameter values for a learning algorithm while applying this optimized algorithm to any data set. That combination of hyperparameters maximizes the model’s performance, minimizing a predefined loss function to produce better results with fewer errors. Note that the learning algorithm optimizes the loss based on the input data and tries to find an optimal solution within the given setting. However, hyperparameters describe this setting exactly.

Eg. of Hyperparameters for a NN:

a) Number of hidden layers.

b) Number of nodes/neurons per layer

c) Learning Rate

d) Momentum

Most important ones as recommended by Andrew NG are: learning rate, adam's beta parameter, hidden units.

Two fairly naive, but commonly used algorithms for tuning hyperparameters are:
• Grid Search – given a set of values for each hyperparameter, the algorithm looks over each possible combination.

• Random Search – given an interval of possible hyperparameter values, the algorithm trains the model by sampling randomly from the provided ranges.

One major drawback of these two approaches is that they are uninformative – the choice of the next set of parameters is independent of the performance of the previous choice. This serves as a motivating factor as to why someone might consider using Bayesian Optimiza![Pasted image 202503061![Pasted image 20250306144928.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250306144928.png)cation, the output is a discrete category label, but in regression, it is a continuous value.
Ans. It is technically possible to convert a regression problem into classification by defining a threshold. For example, if I have a dataset of images with labels of their cloudiness level from 0 to 5 I could define a threshold, i.e. 2.5 and use it to turn the continuous values into discrete one, and use those discrete values as classes (cloudiness level < 2.5 equal image without clouds) but the opposite is definitely not possible.

But converting from classification to regression is not possible as we can't define an order. (Cat < Dog doesn't make sense)

However, there are multiple reasons to avoid it, like:

- Loss of information by binning.
    
- Continuous targets have an order but classification classes don't.
    
- Continuous targets usually have some kind of smoothness: Proximity in feature space (for continuous features) means proximity in target space.
    
- All this loss of information is accompanied by possibly more parameters in the model, e.g. logistic regression has number of coefficients proportional to number of classes.
    
- The binning obfuscates whether one is trying to predict the expectation/mean or a quantile.
    
- One can end up with a badly (conditionally) calibrated regression model, ie biased. (This can also happen for stdandard regression techniq![Pasted image 202503061![Pasted image 20250306183706.png](../../../../Q&A/attachments/Pasted%20image%2020250306183706.png)model is a method with a fixed size of parameters while a non-parametric model can have potentially infinite size of parameters. In non-parametric methods, the complexity of the model grows with the number of training data samples. For example, linear regression, logistic regression and linear Support-vector machines are parametric models having a fixed size of parameters (weight coefficient). But the KNN, decision trees, or SVM with RBF kernel SVMS are non-parametric as the number of parameters increases with the training data size.

- Use **parametric methods** when you have **limited data** and a **known underlying structure** (e.g., predicting house prices with linear regression).
- Use **non-parametric methods** when you have **large data** and **no clear assumptions** about the distribution (e.g., image classification with k-NN or SVM).
- Since parametric models use a fixed parametrization, they are more applicable in cases when we need consistent inference time guarantees. In contrast, the prediction time of non-parametric methods might depend on the dataset size (e.g. finding k-nearest neighbors, iterating over all support vectors, \l![Pasted image 202503071![Pasted image 20250307132906.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250307132906.png)dels make **different types of errors**. Even if it happens that all models have highly correlated errors it will mean that the result with ensembling won't be worse than without. But more commonly errors are uncorrelated, so combining multiple models cancel![Pasted image 202503071![Pasted image 20250307133234.png](../../../../Q&A/attachments/Pasted%20image%2020250307133234.png)2503071![Pasted image 20250307133307.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250307133307.png)ty proportional to the absolute value. The absolute value function encourages some weights to become exactly **zero**. So it selectively removes less important features, making the model **sparse**. While L2 reduces weight magnitudes but keeps all features, preventing overfitting without enforcing sparsity.

Let w = 0.001. Then, L1(w) = |0.001| = 0.001, but L2(w) = (0.001)2 = 0.000001. We see that for the same value of w, the L2 term is much lower than the L1 term. As a consequence, in order to minimize the L1 regularization loss, the optimizer is forced to push w even closer to 0.

This is why L1 regularization is useful for **feature selection**, while L2 regularization helps **prevent overfitting without discarding featur![Pasted image 202503071![Pasted image 20250307135153.png](../../../../Q&A/attachments/Pasted%20image%2020250307135153.png)1![Pasted image 20250307135140.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250307135140.png)![Pasted image 20250307135219.png](../../../../Q&A/attachments/Pasted%20image%2020250307135219.png)2503071![Pasted image 20250307135235.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250307135235.png)1![Pasted image 20250307142830.png](../../../../Q&A/attachments/Pasted%20image%2020250307142830.png)![Pasted image 202503071![Pasted image 20250307143355.png](ml_interview_prep_notes/Interview_prep/ML/Q&A/attachments/Pasted%20image%2020250307143355.png)