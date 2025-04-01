##### Tree-based methods

**Decision tree** is a tree-based method that goes from observations about an object (represented in the branches) to conclusions about its target value (represented in the leaves). At its core, decision trees are nest if-else conditions.

In **classification trees**, the target value is discrete and each leaf represents a class. In **regression trees**, the target value is continuous and each leaf represents the mean of the target values of all objects that end up with that leaf.

Decision trees are easy to interpret and can be used to visualize decisions. However, they are overfit to the data they are trained on -- small changes to the training set can result in significantly different tree structures, which lead to significantly different outputs.

##### 8.1.1.5 Bagging and boosting

Bagging and boosting are two popular ensembling methods commonly used with tree-based algorithms that can also be used for other algorithms.

###### 8.1.1.5.1 Bagging

Bagging, shortened for **b**ootstrap **agg**regat**ing**, is designed to improve the stability and accuracy of ML algorithms. It reduces variance and helps to avoid overfitting.

Given a dataset, instead of training one classifier on the entire dataset, you sample **with** replacement to create different datasets, called bootstraps, and train a classification or regression model on each of these bootstraps. Sampling with replacement ensures each bootstrap is independent of its peers.

If the problem is classification, the final prediction is decided by the majority vote of all models. For example, if 10 classifiers vote SPAM and 6 models vote NOT SPAM, the final prediction is SPAM.

If the problem is regression, the final prediction is the average of all models’ predictions.

Bagging generally improves unstable methods, such as neural networks, classification and regression trees, and subset selection in linear regression. However, it can mildly degrade the performance of stable methods such as k-nearest neighbors[2](https://huyenchip.com/ml-interviews-book/contents/8.1.1-overview:-basic-algorithm.html#fn_2).

![Bagging](https://huyenchip.com/ml-interviews-book/contents/images/image26.png "image_tooltip")  
Illustration by [Sirakorn](https://en.wikipedia.org/wiki/Bootstrap_aggregating#/media/File:Ensemble_Bagging.svg)

A **random forest** is an example of bagging. A random forest is a collection of decision trees constructed by both **bagging** and **feature randomness**, each tree can pick only from a random subset of features to use.

Due to its ensembling nature, random forests correct for decision trees’ overfitting to their training set.

**Applications**: Random forests are among the most widely used machine learning algorithms in the real world. They are used in banking for fraud detection, medicine for disease prediction, stock market analysis, etc.

For more information on random forests, see [Understanding Random Forest](https://towardsdatascience.com/understanding-random-forest-58381e0602d2) by Tony Yiu.

###### 8.1.1.5.2 Boosting

Boosting is a family of iterative ensemble algorithms that convert weak learners to strong ones. Each learner in this ensemble is trained on the same set of samples but the samples are weighted differently among iterations. Thus, future weak learners focus more on the examples that previous weak learners misclassified.

1. You start by training the first weak classifier on the original dataset.
2. Samples are reweighted based on how well the first classifier classifies them, e.g. misclassified samples are given higher weight.
3. Train the second classifier on this reweighted dataset. Your ensemble now consists of the first and the second classifiers.
4. Samples are weighted based on how well the ensemble classifies them.
5. Train the third classifier on this reweighted dataset. Add the third classifier to the ensemble.
6. Repeat for as many iterations as needed.
7. Form the final strong classifier as a weighted combination of the existing classifiers -- classifiers with smaller training errors have higher weights.

![Boosting](https://huyenchip.com/ml-interviews-book/contents/images/image27.png "image_tooltip")  
Illustration by [Sirakorn](https://en.wikipedia.org/wiki/Boosting_\(machine_learning\)#/media/File:Ensemble_Boosting.svg)

An example of a boosting algorithm is Gradient Boosting Machine which produces a prediction model typically from weak decision trees. It builds the model in a stage-wise fashion as other boosting methods do, and it generalizes them by allowing optimization of an arbitrary differentiable loss function.

XGBoost, a variant of GBM, used to be [the algorithm of choice for many winning teams of machine learning competitions](https://github.com/dmlc/xgboost/tree/master/demo#machine-learning-challenge-winning-solutions). It’s been used in a wide range of tasks from classification, ranking, to the discovery of the Higgs Boson[3](https://huyenchip.com/ml-interviews-book/contents/8.1.1-overview:-basic-algorithm.html#fn_3). However, many teams have been opting for [LightGBM](https://github.com/microsoft/LightGBM), a distributed gradient boosting framework that allows parallel learning which generally allows faster training on large datasets.