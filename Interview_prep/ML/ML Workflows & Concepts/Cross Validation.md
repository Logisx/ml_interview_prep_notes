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



## Are you done after using your test set once?
https://www.reddit.com/r/MachineLearning/comments/qzsrdw/d_test_set_just_a_glorified_validation_set/
Once you touch the test you are done. You need to go and collect more data now because as you say, if you are going back to the test set many times it's just a glorified validation set.

BUT!
What people here say about the fact that you should never ever ever ever touch the test set until you finish the project - well, that might be correct for research and algorithm benchmarking, but in industry... well, this is unrealistic. you will be testing your model on the test set =)

below is what I think is a useful set of differences between validation and test in production (might not be relevant in all cases)

1. source. we always try to create test sets which origin is completely different from the source of the training set. I work in medical imaging, so for us that would be using data from the different population (country, medical organization, type of scanners)
    
2. type of decisions. validation sets are used to tune hyperparameters, compare experiments, assess new tweaks. test sets are used to make decisions about releases and to track dynamics of the system quality
    
3. update policy. you'll probably have a different set of rules for how and when you add data to your validation and test sets
    
4. data quality. if your data is noisy, you should probably invest more time and money (at least initially) into creating a good test set
    

so yeah, there are a lot of good thoughts in this thread, but I don't see how many of them transfer into production. I imagine the look on the face of our PO if we asked for a completely new test set after each release =)

A test set is a **verification set**. It is a verification that all of the work you have done (selecting algorithms, designing architectures, performing cross-validation, tuning hyperparameters, etc.) generalizes beyond your training data (i.e. that you have not overfit to your training data).
NOTE THE FOLLOWING: The validation data _must_ be representative of the _training data_, **NOT** the testing data.