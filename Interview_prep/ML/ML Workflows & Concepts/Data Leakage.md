### Target leakage example (Feature leakage)

For example, imagine a model created to predict credit card fraud. This issue is concerning in forecasting applications where models must make reliable future predictions based on incomplete data. The raw dataset will contain information about the customer, the transaction amount, the location, whether fraud was detected and if a chargeback was received.

In training the model, the fraud detection and chargeback columns will have true or false values entered. In the real world, a chargeback is typically initiated after fraud has been detected, so this information would not be available at the time of detection.

Training a model with this information teaches it that transactions with a chargeback are almost always fraudulent. During validation, the model will show high accuracy because, in training, the relationship between fraud and chargebacks is strong. However, the chargeback information will not be available when deployed and the model will perform poorly in practice**.**

### Train-test contamination example  

Imagine a data scientist building a model to predict house prices based on features such as house size, number of bedrooms and neighborhood. Standardizing the numerical features (such as house size and age) so they all have the same scale is a common preprocessing step, which is helpful for many [machine learning algorithms](https://www.ibm.com/topics/machine-learning-algorithms).

However, suppose that the data scientist applies standardization to the entire dataset before splitting it into training and test datasets. In that case, the model will indirectly "see" information from the test set during training. As a result, the model's performance on the test data might appear artificially inflated because the test set's information was used in the preprocessing step. This makes it easier for the model to perform well on the test set but potentially reduces its ability to generalize to new, unseen data.

Preprocessing steps such as scaling, imputation or feature selection should be fitted only on the training data and then applied to the validation set, rather than fitting them on the entire dataset before splitting. Misapplying transformers such as scaling or normalization can lead to train-test contamination, especially in neural network models. When these improperly executed preprocessing steps are performed over the whole dataset, it leads to biased predictions and an unrealistic sense of the model's performance.