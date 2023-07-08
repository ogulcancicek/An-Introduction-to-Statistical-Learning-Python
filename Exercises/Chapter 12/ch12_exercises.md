## Question 1
This problem involves the K-means clustering algorithm.

(a) Prove (12.18).

(b) On the basis of this identity, argue that the K-means clustering algorithm (Algorithm 12.2) decreases the objective (12.17) at each iteration.

### Answer

(a) Recall that

$$  \frac{1}{|C_k|} \sum_{i, i' \in C_k} \sum_{j=1}^p (x_{ij} - x_{i'j})^2 = 2 \sum_{i \in C_k} \sum_{j=1}^p (x_{ij} - \bar{x}_{kj})^2 \tag{12.18}$$

where $ \bar{x}_{kj} = \frac{1}{|C_k|} \sum_{i \in C_k} x_{ij} $.

If we expand the left-hand side of equation (12.18):

$$ \frac{1}{|C_k|} \sum_{i, i' \in C_k} \sum_{j=1}^p (x_{ij} - x_{i'j})^2 = \frac{1}{|C_k|} \sum_{i, i' \in C_k} \sum_{j=1}^p x_{ij}^2 + \frac{1}{|C_k|} \sum_{i, i' \in C_k} \sum_{j=1}^p x_{i'j}^2 - \frac{2}{|C_k|} \sum_{i, i' \in C_k} \sum_{j=1}^p x_{ij}x_{i'j} $$

$$ = \frac{2}{|C_k|}|C_k| \sum_{i \in C_k} \sum_{j=1}^p x_{ij}^2 - \frac{2}{|C_k|} \sum_{i, i' \in C_k} \sum_{j=1}^p x_{ij}x_{i'j} = 2 \sum_{i \in C_k} \sum_{j=1}^p x_{ij}^2 - \frac{2}{|C_k|} \sum_{i, i' \in C_k} \sum_{j=1}^p x_{ij}x_{i'j} $$

And now if we expand the right-hand side of the equation:

$$ 2 \sum_{i \in C_k} \sum_{j=1}^p (x_{ij} - \bar{x}_{kj})^2 = 2 \sum_{i \in C_k} \sum_{j=1}^p x_{ij}^2 + 2 \sum_{i \in C_k} \sum_{j=1}^p \bar{x}_{kj}^2 - 4 \sum_{i \in C_k} \sum_{j=1}^p x_{ij}\bar{x}_{kj} $$

$$ = 2 \sum_{i \in C_k} \sum_{j=1}^p x_{ij}^2 + 2 |C_k| \sum_{j=1}^p \bar{x}_{kj}^2 - 4 |C_k| \sum_{j=1}^p \bar{x}_{kj}^2 = 2 \sum_{i \in C_k} \sum_{j=1}^p x_{ij}^2 - 2 |C_k| \sum_{j=1}^p \bar{x}_{kj}^2 $$

$$ = 2 \sum_{i \in C_k} \sum_{j=1}^p x_{ij}^2 - 2 |C_k|\frac{1}{|C_k|^2} \sum_{i, i' \in C_k} \sum_{j=1}^p x_{ij}x_{i'j} $$

Therefore, we can conclude that the left-hand side and the right-hand side are equal.

(b) The objective function (12.17) is defined as:

$$ \min_{C_1, \dots, C_K} \{ \sum_{k=1}^K \frac{1}{|C_k|} \sum_{i, i' \in C_k} \sum_{j=1}^p (x_{ij} - x_{i'j})^2\} $$

By using the equation given in (a), we can rewrite (12.17) as:

$$ \min_{C_1, \dots, C_K} \{ \sum_{k=1}^K 2 \sum_{i \in C_k} \sum_{j=1}^p (x_{ij} - \bar{x}_{kj})^2 \} $$

The K-Means algorithm aims to minimize within-cluster variance. This means that each observation is assigned to the nearest cluster centroid, minimizing the distance between the observations and their assigned cluster centroids. Consequently, the K-Means algorithm decreases the objective (12.17), resulting in reduced within-cluster variance.

## Question 2
Suppose that we have four observations, for which we compute a dissimilarity matrix, given by

$$ \begin{bmatrix} & 0.3 & 0.4 & 0.7 \\ 0.3 &  & 0.5 & 0.8 \\ 0.4 & 0.5 &  & 0.45 \\ 0.7 & 0.8 & 0.45 &  \\ \end{bmatrix} $$

For instance, the dissimilarity between the first and second observations is 0.3, and the dissimilarity between the second and fourth observations is 0.8.

(a) On the basis of this dissimilarity matrix, sketch the dendrogram that results from hierarchically clustering these four observations using complete linkage. Be sure to indicate on the plot the height at which each fusion occurs, as well as the observations corresponding to each leaf in the dendrogram.

(b) Repeat (a), this time using single linkage clustering.

(c) Suppose that we cut the dendrogram obtained in (a) such that two clusters result. Which observations are in each cluster?

(d) Suppose that we cut the dendrogram obtained in (b) such that two clusters result. Which observations are in each cluster?

(e) It is mentioned in the chapter that at each fusion in the dendrogram, the position of the two clusters being fused can be swapped without changing the meaning of the dendrogram. Draw a dendrogram that is equivalent to the dendrogram in (a), for which two or more of the leaves are repositioned, but for which the meaning of the dendrogram is the same.

### Answer

(a) 

![Figure 28](/figures/Figure_28.png)

(b) 

![Figure 29](/figures/Figure_29.png)

(c) If we suppose that we cut the dendrogram obtained in (a) such that two cluster result. The clusters will look like: 

Cluster A = {0, 1}

Cluster B = {2, 3}

(d) If we suppose that we cut the dendrogram obtained in (a) such that two cluster result. The clusters will look like: 

Cluster A = {0, 1, 2}

Cluster B = {3}

(e) 

![Figure 30](/figures/Figure_30.png)

## Question 3
In this problem, you will perform K-means clustering manually, with K = 2, on a small example with n = 6 observations and p = 2 features. The observations are as follows.

| Obs. | X1 | X2 |
|------|----|----|
|   1  |  1 |  4 |
|   2  |  1 |  3 |
|   3  |  0 |  4 |
|   4  |  5 |  1 |
|   5  |  6 |  2 |
|   6  |  4 |  0 |

(a) Plot the observations.

(b) Randomly assign a cluster label to each observation. You can use the sample() command in R to do this. Report the cluster labels for each observation.

(c) Compute the centroid for each cluster.

(d) Assign each observation to the centroid to which it is closest, in terms of Euclidean distance. Report the cluster labels for each observation.

(e) Repeat (c) and (d) until the answers obtained stop changing.

(f) In your plot from (a), color the observations according to the cluster labels obtained.

### Answers

(a) 

![Figure 31](/figures/Figure_31.png)

(b)

![Figure 32](/figures/Figure_32.png)

(c)

![Figure 33](/figures/Figure_33.png)

(d)

![Figure 34](/figures/Figure_34.png)

(e) - (f)

![Figure 35](/figures/Figure_35.png)

## Question 4
Suppose that for a particular data set, we perform hierarchical clustering using single linkage and using complete linkage. We obtain two dendrograms.

(a) At a certain point on the single linkage dendrogram, the clusters {1,2,3} and {4,5} fuse. On the complete linkage dendrogram, the clusters {1, 2, 3} and {4, 5} also fuse at a certain point. Which fusion will occur higher on the tree, or will they fuse at the same height, or is there not enough information to tell?

(b) At a certain point on the single linkage dendrogram, the clusters {5} and {6} fuse. On the complete linkage dendrogram, the clusters {5} and {6} also fuse at a certain point. Which fusion will occur higher on the tree, or will they fuse at the same height, or is there not enough information to tell?

### Answers

(a) When using the single linkage method to model hierarchical clustering, clusters are merged based on the smallest pairwise distances between observations. On the other hand, the complete linkage method merges clusters based on the largest pairwise distances. 

In the dendrogram figure, the point at which the clusters {1,2,3} and {4,5} fuse will occur at a higher level for the complete linkage method compared to the single linkage method. This is because the complete linkage method considers the maximum distance between observations, which tends to result in fewer and more compact clusters compared to the single linkage method.

(b) Since the distance calculation in hierarchical clustering is based on pairwise distances between individual observations, rather than distances between clusters and observations, the fusion points for single linkage and complete linkage methods will occur at the same height on dendrogram figures. This is because the distances between individual observations remain the same regardless of the linkage method used. Thus, the heights at which clusters merge will be consistent regardless of whether single linkage or complete linkage is employed.

## Question 5
In words, describe the results that you would expect if you performed K-means clustering of the eight shoppers in Figure 12.16, on the basis of their sock and computer purchases, with K = 2. Give three answers, one for each of the variable scalings displayed. Explain.

### Answer

![Figure 36](/figures/Figure_36.png)

In the left panel of the figure, which represents the data on purchase counts of socks and computers, when applying the K-Means clustering method without scaling the data to have a standard deviation of one, I expect the algorithm to effectively separate the two customer classes. This is because customers who have a large number of sock purchases would have a significant impact on the algorithm, leading to the formation of distinct clusters based on the amount of sock purchases. Similarly, in the right panel of the figure, which shows the purchasing costs for each item, I anticipate that the K-Means clustering method would successfully cluster the dataset based on customers who spend a significant amount on computers and those who do not.

In the center panel, where the data is scaled to have a standard deviation of one, the algorithm would classify the observations based on the types of purchases, distinguishing between customers who purchase socks and those who purchase computers. However, the relative proximity of the observations may make it more challenging to accurately separate these two customer classes compared to the scenarios without data scaling.

## Question 6
We saw in Section 12.2.2 that the principal component loading and score vectors provide an approximation to a matrix, in the sense of (12.5). Specifically, the principal component score and loading vectors solve the optimization problem given in (12.6). Now, suppose that the M principal component score vectors $z_{im}$, $m = 1,...,M$, are known. Using (12.6), explain that the first M principal component loading vectors $\phi_{jm}$, $m = 1,...,M$, can be obtaining by performing M separate least squares linear regressions. In each regression, the principal component score vectors are the predictors, and one of the features of the data matrix is the response.

### Answer
Recall that:

$$ x_{ij} \approx \sum_{m=1}^M z_{im}\phi_{jm} \tag{12.5}$$

And:

$$ \min_{A\in\R^{n\times M}, B\in\R^{n\times M}} \{ \sum_{j=1}^p\sum_{i=1}^n ( x_{ij} - \sum_{m=1}^M a_{im}b_{jm})^2 \} \tag{12.6} $$

If we assume that we have a dataset with the principal component scores as features and the real feature values from the original data as the response, we can view the problem of predicting the real feature values using principal component scores as a regression problem.

The linear regression equation is:

$$ \hat{Y} = \beta_0 + \beta_1 X_1 + \dots + \beta_p X_p $$

We can modify this equation as follows:

$$ \hat{x_{ij}} = \beta_{j1}z_{i1} + \beta_{j2}z_{i2} + \dots + \beta_{jM}z_{iM} $$

By performing M separate linear regressions, one for each principal component loading vector, we can estimate the regression coefficients $(\beta_{0j}, \beta_{1j}, \ldots, \beta_{Mj})$ that correspond to the loading vector $\phi_{jm}$ for feature $j$.

In each regression, the principal component score vectors $z_{im}$ act as predictors, and we treat the feature values $x_{ij}$ as the response variables. By solving each regression problem separately, we can obtain the M principal component loading vectors $\phi_{jm}$ that represent the coefficients of the linear regression models for each feature.

This formulation allows us to estimate the loadings by fitting a linear regression model between the principal component scores and the original feature values.
