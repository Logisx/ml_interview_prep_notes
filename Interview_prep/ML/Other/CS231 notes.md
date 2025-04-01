
Nearest neighbour classifier: 
example of classifying images (10 classes)
Basic concept - find the image with the most similar pixels and use its class
idea is to take L1/L2 difference of all the features (for L1 example you take your inference input features and substract them from all the train samples' features you have. The one with the smallest difference is the one which label you take. Like if all pixels almost match probably it's the same class)

No time to train - just save the values and compare to them while predicting. But more time to predict.
```python
import numpy as np

class NearestNeighbor(object):
  def __init__(self):
    pass

  def train(self, X, y):
    """ X is N x D where each row is an example. Y is 1-dimension of size N """
    # the nearest neighbor classifier simply remembers all the training data
    self.Xtr = X
    self.ytr = y

  def predict(self, X):
    """ X is N x D where each row is an example we wish to predict label for """
    num_test = X.shape[0]
    # lets make sure that the output type matches the input type
    Ypred = np.zeros(num_test, dtype = self.ytr.dtype)

    # loop over all test rows
    for i in range(num_test):
      # find the nearest training image to the i'th test image
      # using the L1 distance (sum of absolute value differences)
      distances = np.sum(np.abs(self.Xtr - X[i,:]), axis = 1)
      min_index = np.argmin(distances) # get the index with smallest distance
      Ypred[i] = self.ytr[min_index] # predict the label of the nearest example

    return Ypred
```

L1 distance: sum(abs(x1-x2))
L2: sqrt(sum((x1-x2)^2))

L2 prefers many medium disagreements to a big one (outlier)



# K-Nearest Neighbor Classifier
Basic concept: we find top k closest images and have them vote on the label of the test image.
k =1 -> simple Nearest Neighbor classifier
As k grows, the classifier is more resistant to outliers.
![Pasted image 20250228154750 1.png](Pasted%20image%2020250228154750%201.png)


![Pasted image 20250228161155.png](Pasted%20image%2020250228161155%201.png)



# Data splitting

### Train Val Test
Train - train models
val -tune yperparameters
test - final evaluation

If a lot of hyperparams -> bigger val
### Cross-validation
If the amount of data is small, cross-val is used for hyperparameter tuning.
You do train test sets. Then divide train in folds (e.g. 5 folds) and each time use 4 folds for training and 1 for validation. Then iterate over which fold is the validation fold, evaluate the performance, and finally average the performance across the different folds.
Typical number of folds is 3/5/10

In practice, cross-validation is not often used as it is computationally expensive.



# Linear Classifier
y = Wx+b means that for classification we draw kinda lines and rotates them with W and move them around with b to separate the categories.
![Pasted image 20250228203831.png](Pasted%20image%2020250228203831%201.png)

![Pasted image 20250228165100.png](Pasted%20image%2020250228165100%201.png)


We can transform y=Wx+b to y=Wx if do this:
![Pasted image 20250228165215 1.png](Pasted%20image%2020250228165215%201.png)


# Loss function
We measure how unhappy we are with how the current prediction turned out.
Loss has no kinda unit, different losses are not comparable. Like softmax loss of 2 and svm loss of 1.06 doesnt' mean svm is better.
# SVM - hinge loss (also called max-margin loss)






???????????????????????????????????? Read more on SVMs





![Pasted image 20250228170355.png](Pasted%20image%2020250228170355%201.png)

**hinge loss** - max(0,−)


# Regularization
We add sum of weights in the matrix (or squared for L2) and add it to loss function to prevent overfitting. This sum is multiplied by coef that is hyperparam.
![Pasted image 20250228204207.png](Pasted%20image%2020250228204207%201.png)



# Softmax - cross-entropy loss

Classification function that returns a vector of probabilities for each class to be the right one.

![Pasted image 20250228205153.png](Pasted%20image%2020250228205153.png)Softmax to SVM comparison

# Optimizing Loss
Optimization loss analogy is a blindfolded hiker. You want to reach the bottom of the hills. You can either try random directions around you and if it goes down - you step, if not - you stay. Or, more optimally you feel the slope with your feet (with gradient) and step where you feel the slope goes down. The learning rate represents the distance of your step, so you don't overstep the bottomest point.

# Data Preprocessing
Mean substraction - centers around (0,0)
Normalization - scales to -1, 1 by dividing by standard dev
![Pasted image 20250303182337.png](Pasted%20image%2020250303182337%201.png)

### PCA and whitening
![Pasted image 20250303182517.png](Pasted%20image%2020250303182517%201.png)