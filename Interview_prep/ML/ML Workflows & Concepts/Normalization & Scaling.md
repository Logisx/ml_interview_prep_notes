**Always fit the normalization parameters** (like mean, standard deviation, min, max) on **only the training set** and then apply the same transformation to the test set.

- **Standardization**: Preferred when the data is normally distributed, when dealing with outliers or when using models that are sensitive to variance (e.g., SVM, PCA).
- **Min-Max Scaling**: Best when you need to scale the data to a specific range (e.g., [0, 1]), and when outliers are not a concern.