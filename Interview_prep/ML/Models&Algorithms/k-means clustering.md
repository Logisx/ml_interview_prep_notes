Pick k cluster centroids with random coordinates
Calculate which points are closer to which centroid
Move centroid to the mean coordinate of the points
![500](attachments/Pasted%20image%2020250313113132.png)p![500](attachments/Pasted%20image%2020250313113231.png)![500](attachments/Pasted%20image%2020250313113246.png)p![500](attachments/Pasted%20image%2020250313113302.png)ustering aims to partition observations into k clusters in which each observation belongs to the cluster with the nearest mean. k-means minimizes within-cluster variances (squared Euclidean distances), but not regular Euclidean distances.

The algorithm doesn’t guarantee convergence to the global optimum. The result may depend on the initial clusters. As the algorithm is usually fast, it is common to run it multiple times with different starting conditions.

The problem is computationally difficult (NP-hard); however, efficient heuristic algorithms converge quickly to a local optimum.

The algorithm has a loose relationship to the k-nearest neighbor classifier. After obtaining clusters using k-means clustering, we can classify new data into those clusters by applying the 1-nearest neighbor classifier to the cluster centers.

**Applications**: Vector quantization for signal processing (where k-means clustering was originally developed), cluster analysis, feature learning, topic modeling.