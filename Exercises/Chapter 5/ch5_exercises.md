# Chapter 5 - Exercises

## Question 1
Using basic statistical properties of the variance, as well as single-variable calculus, derive (5.6). In other words, prove that α given by (5.6) does indeed minimize Var(αX + (1 − α)Y).

### Answer
Recal that

$$ \text{Var}(aX+bY) = a^2 \text{Var}(X) + b^2 \text{Var}(Y) + 2ab\text{Cov}(X,Y) $$

If we use this property on $ \text{Var}(αX + (1 − α)Y) $, we get:

$$ \text{Var}(αX + (1 − α)Y) = \alpha^2\text{Var}(X) + (1 - \alpha)^2\text{Var}(Y) + 2\alpha(1-\alpha)\text{Cov}(X,Y) $$

$$ = \alpha^2\text{Var}(X) + (1 - 2\alpha + \alpha^2)\text{Var}(Y) + (2\alpha-2\alpha^2)\text{Cov}(X,Y) $$

, we set 

$$ f(\alpha) = \alpha^2\text{Var}(X) + (1 - 2\alpha + \alpha^2)\text{Var}(Y) + (2\alpha-2\alpha^2)\text{Cov}(X,Y) $$

, and if we solve 

$$ f(\alpha)' =  \frac{d}{d\alpha}(\alpha^2\text{Var}(X) + (1 - 2\alpha + \alpha^2)\text{Var}(Y) + (2\alpha-2\alpha^2)\text{Cov}(X,Y)) = 0 $$

$$ \implies 2\alpha \text{Var}(X) + 2\alpha \text{Var}(Y) - 2\text{Var}(Y) + 2\text{Cov}(X,Y) - 4\alpha\text{Cov}(X,Y) =0 $$

$$ \implies \alpha(\text{Var}(X) + \text{Var}(Y) -2\text{Cov}(X,Y)) = \text{Var}(Y) - \text{Cov}(X,Y) $$

$$ \implies \alpha = \frac{\text{Var}(Y) - \text{Cov}(X,Y)}{\text{Var}(X) + \text{Var}(Y) -2\text{Cov}(X,Y)} \tag{5.6}$$

## Question 2
We will now derive the probability that a given observation is part of a bootstrap sample. Suppose that we obtain a bootstrap sample from a set of n observations.

(a) What is the probability that the first bootstrap observation is not the jth observation from the original sample? Justify your answer.

(b) What is the probability that the second bootstrap observation is not the jth observation from the original sample?

(c) Argue that the probability that the jth observation is not in the bootstrap sample is $(1 − 1/n)^n$.

(d) When n = 5, what is the probability that the jth observation is in the bootstrap sample?

(e) When n = 100, what is the probability that the jth observation is in the bootstrap sample?

(f) When n = 10,000, what is the probability that the jth observation is in the bootstrap sample?

(g) Create a plot that displays, for each integer value of n from 1 to 100,000, the probability that the jth observation is in the bootstrap sample. Comment on what you observe.

(h) We will now investigate numerically the probability that a bootstrap sample of size n = 100 contains the jth observation. Here j = 4. We repeatedly create bootstrap samples, and each time we record whether or not the fourth observation is contained in the bootstrap sample.

```r
> store <- rep(NA, 10000) 
> for(i in 1:10000){
    store[i] <- sum(sample(1:100, rep=TRUE) == 4) > 0 
}
> mean(store)
```

Comment on the results obtained.

### Answer
(a) 

$$ p(Y=y|X_1 \neq X_j) = \frac{n-1}{n} $$

There are a total of n observations in the original sample, and each observation has an equal probability of being selected. The probability of selecting the jth observation as the first bootstrap observation is $1/n$. To find the probability that the first bootstrap observation is not the jth observation from the original sample, we simply subtract 1/n from the probability of selecting any other observation, which is $(n-1)/n$.

(b)
Since we do sampling with replacement, and we find the probability that the second bootstrap observation is not the jth observation from the original sample, which is 

$$ p(\text{all observations from original sample}) \times p(Y=y|X_2 \neq X_j) = \frac{n-1}{n}$$

(c) 
We sample with replacement, so on each step, the probability of not selecting the jth observation as the bootstrap observation is equal to

$$ \frac{n-1}{n} $$

If we assume that there are n bootstrap observations, since the probabilities are indipendent, we can multiply these probabilities. Then the probability that the jth observation is not in the bootstrap sample is given by

$$ \underbrace{\frac{n-1}{n}\times...\times\frac{n-1}{n}}_{\text{n times}} = ((n-1)/n)^n $$

(d)
When $n=5$, the probability that the jth observation is in the bootstrap sample is

$$ 1 - ((5-1)/5)^5 = 1 - 0.8^5 = 0.672$$

(e)
When $n=100$, the probability that the jth observation is in the bootstrap sample is

$$ 1 - ((100-1)/100)^{100} = 1 - 0.99^{100} = 0.634$$

(f)
When $n=10000$, the probability that the jth observation is in the bootstrap sample is

$$ 1 - ((10000-1)/10000)^{10000} = 1 - 0.9999^{10000} = 0.632$$

(g)
```python
import matplotlib.pyplot as plt
import numpy as np

def prob(n):
    return 1-np.power((n-1)/n, n)

n_list = range(1, 100000)
prob_list = prob(np.array(n_list))

plt.plot(n_list, prob_list)
plt.show()
```
$$ \lim_{n \rightarrow \infin} 1 - (1 - (\frac{1}{n})^n) = 1 - \frac{1}{e} \approx 0.632 $$

![Figure 1](/figures/Figure_1.png)

(h)

## Question 3
We now review k-fold cross-validation.

(a) Explain how k-fold cross-validation is implemented.

(b) What are the advantages and disadvantages of k-fold cross-validation relative to:
-  The validation set approach?
-  LOOCV?
### Answer
(a)
k-Fold cross-validation approach is implemented by randomly dividing the set of observations into k groups, or folds, of approximately equal size and then the first fold is treated as a validation set, while the other (k-1) folds are used to fit the model. The mean squared error, $\text{MSE}_1$, is computed on the observations in the validation set. 
The procedure is repeated k times; each time, a different group of observations is treated as a validation set. This process results in k estimated of the test error, $\text{MSE}_1, \text{MSE}_2, ..., \text{MSE}_k$.
The k-fold cross-validation estimate is computed b the averaging these values,

$$ CV_{(k)} = \frac{1}{k}\sum_{i=1}^k \text{MSE}_i $$

(b)

Advantages

- k-Fold CV uses all available data for training and testing, which can lead to more accurate model performance estimates
- k-Fold CV reduces the variability of the model performance estimate, as it averages the results over multiple partitions.
- k-Fold CV allows for the detection of overfitting, as it measures the model's ability to generalize to new data.

Disadvantages

- k-Fold CV can be computationally expensive, especially for large datasets or complex models.
- It may not be suitable for all types of data, such as time-series data or data with spatial autocorrelation, where partitioning the data may result in biased estimates.
---
- The k-Fold cross-validation has a computational advantage on LOOCV. LOOCV requires fitting the statitical learning method n times, this has potential to be computationally expensive. Especially, if n is extremely large. But, while $k \lt n$, the k-Fold cross validation requires less fitting process than the LOOCV.
- LOOCV will perform approximately unbiased estimates of the test error, since each training set contains $n-1$ observations, which is almost as many as the number of observations in the full data.  And performing k-fold CV for, say, k = 5 or k = 10 will lead to an intermediate level of bias, since each training set contains approximately $(k − 1)n/k$ observations - fewer than in the LOOCV approach, but substantially more than in the validation set approach. 

## Question 4
Suppose that we use some statistical learning method to make a prediction for the response Y for a particular value of the predictor X. Carefully describe how we might estimate the standard deviation of our prediction.

### Answer
The bootstrap is a method that can be used to quantify the uncertainty associated with a given estimator or statistical learning method. By using bootstrap for out learning method, we can estimate the standard error of our prediction. 

The bootstrap method involves repeatedly sampling with replacement from the original data set to create multiple training sets. For each training set, we fit the statistical learning method and use it to predict the respons variable for the original value of X. We repeat this process many times, producing multiple predictions for the response variable for each value of X. We can then calculate the standard deviation of these predictions as an estimate of the standard deviation of our original prediction.
