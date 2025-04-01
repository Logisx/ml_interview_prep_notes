k-NN is a non-parametric method used for classification and regression. Given an object, the algorithm’s output is computed from its k closest training examples in the feature space.

- In k-NN classification, each object is classified into the class most common among its k nearest neighbors.
- In k-NN regression, each object’s value is calculated as the average of the values of its k nearest neighbors.

**Applications**: anomaly detection, search, recommender system

1 Nearest neighbour classifier: 
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

# K-Nearest Neighbor Classifier
Basic concept: we find top k closest images and have them vote on the label of the test image.
k =1 -> simple Nearest Neighbor classifier
As k grows, the classifier is more resistant to outliers.
![Pasted image 20250228154750.png](ml_interview_prep_notes/Interview_prep/ML/Models&Algorithms/attachments/Pasted%20image%2020250228154750.png)281![Pasted image 20250228161155.png](../../../../Models&Algorithms/attachments/Pasted%20image%2020250228161155.png)