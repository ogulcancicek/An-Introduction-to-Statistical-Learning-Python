# Chapter 4 - Exercises

## Question 1
Using a little bit of algebra, prove that (4.2) is equivalent to (4.3). In other words, the logistic function representation and logit represen- tation for the logistic regression model are equivalent.

### Answer
Recall that 
$$ p(x) = \frac{e^{\beta_0 + \beta_1X}}{1 + e^{\beta_0 + \beta_1X}} \tag{4.2}$$
$$ \frac{p(x)}{1-p(x)} = e^{\beta_0 + \beta_1X} \tag{4.3} $$

$$ p(x) = \frac{e^{\beta_0 + \beta_1X}}{1 + e^{\beta_0 + \beta_1X}} => \frac{1}{p(x)} = \frac{1 + e^{\beta_0 + \beta_1X}}{e^{\beta_0 + \beta_1X}} = 1 + \frac{1}{e^{\beta_0 + \beta_1X}} $$
$$ => \frac{1-p(x)}{p(x)} = e^{\beta_0 + \beta_1X}$$

## Question 2
It was stated in the text that classifying an observation to the class for which (4.17) is largest is equivalent to classifying an observation to the class for which (4.18) is largest. Prove that this is the case. In other words, under the assumption that the observations in the kth class are drawn from a $N(\mu_k,\sigma^2)$ distribution, the Bayes classifier assigns an observation to the class for which the discriminant function is maximized.

### Answer
Recall that

$$ p_k(x) = \frac{\pi_k \frac{1}{\sqrt{2\pi}\sigma} \exp(-\frac{1}{2\sigma^2}(x - \mu_k)^2)}{\sum_{l=1}^K \pi_l \frac{1}{\sqrt{2\pi}\sigma} \exp(-\frac{1}{2\sigma^2}(x - \mu_k)^2)} \tag{4.17} $$

$$ \delta_k(x) = x.\frac{\mu_k}{\sigma^2} - \frac{\mu_k^2}{2\sigma^2} + \log(\mu_k) \tag{4.18} $$

We're looking for the class with the largest probability, which means that we're looking for the largest value of $p_k(x)$. To simplify this calculation, we can take the logarithm of equation (4.17):

$$ \log(\frac{\pi_k \frac{1}{\sqrt{2\pi}\sigma} \exp(-\frac{1}{2\sigma}(x - \mu_k)^2)}{\sum_{l=1}^K \pi_l \frac{1}{\sqrt{2\pi}\sigma} \exp(-\frac{1}{2\sigma}(x - \mu_k)^2)}) = \frac{\pi_k e^{a_j}}{\sum_{l=1}^K \pi_l e^{a_l}} \  (\text{where} \ a_j = -\frac{1}{2\sigma^2}(x - \mu_k)^2)$$

$$ \log(\frac{\pi_k e^{a_j}}{\sum_{l=1}^K \pi_l e^{a_l}}) = \log{(\pi_k e^{a_j})} - \log{(\sum_{l=1}^K \pi_l e^{a_l})} $$

$$ = \log(\pi_k) + a_k - \underbrace{\log{(\sum_{l=1}^K \pi_l e^{a_l})}}_{\text{will take a value across every value of k}} $$

Under these circumstances, choosing a value for k to maximize $\log(\pi_k) + a_k - \log{(\sum_{l=1}^K \pi_l e^{a_l})}$ is equivalent to choosing a value k to maximize $\log(\pi_k) + a_k$.

$$ \log(\pi_k) + a_k = \log(\pi_k) -\frac{1}{2\sigma^2}(x - \mu_k)^2$$
$$ \log(\pi_k) -\frac{x^2 - 2x\mu_k + \mu_k^2}{2\sigma^2} $$
$$ \log(\pi_k) - \frac{\mu_k^2}{2\sigma^2} + \frac{x\mu_k}{\sigma^2} - \frac{x^2}{2\sigma^2} $$ 


We can note that $\frac{x^2}{2\sigma^2}$ is constant for all values of k, as we did in the previous step. So choosing a value of k to maximize $ \log(\pi_k) - \frac{\mu_k^2}{2\sigma^2} + \frac{x\mu_k}{\sigma^2} - \frac{x^2}{2\sigma^2} $ is equivalent to choosing a value of k to maximize $\delta_k(x) = x.\frac{\mu_k}{\sigma^2} - \frac{\mu_k^2}{2\sigma^2} + \log(\mu_k)$

## Question 3
This problem relates to the QDA model, in which the observations within each class are drawn from a normal distribution with a class-specific mean vector and a class specific covariance matrix. We consider the simple case where p = 1; i.e. there is only one feature.
Suppose that we have K classes, and that if an observation belongs to the kth class then X comes from a one-dimensional normal distribution, $X ∼ N(\mu_k,\sigma_k^2)$. Recall that the density function for the one-dimensional normal distribution is given in (4.16). Prove that in this case, the Bayes classifier is not linear. Argue that it is in fact quadratic.

### Answer
Recall that
$$ f_k(x) = \frac{1}{\sqrt{2\pi}\sigma_k} \exp(-\frac{1}{2\sigma_k}(x - \mu_k)^2) \tag{4.16} $$
$$ p_k(x) = \frac{\pi_k f_k(x)}{\sum_{l=1}^K \pi_l f_l(x)} $$

If we substitute equation (4.6) into the formula for $p_k(x)$, we obtain:
$$ p_k(x) = \frac{\pi_k \frac{1}{\sqrt{2\pi}\sigma} \exp(-\frac{1}{2\sigma^2}(x - \mu_k)^2)}{\sum_{l=1}^K \pi_l \frac{1}{\sqrt{2\pi}\sigma} \exp(-\frac{1}{2\sigma^2}(x - \mu_k)^2)} $$
and if we simplify this equation to make it easier to took its logarithm:
$$ p_k(x) = \frac{\frac{\pi_k}{\sigma_k} e^{a_j}}{\sum_{l=1}^K \frac{\pi_l}{\sigma_l} e^{a_l}} \  (\text{where} \ a_j = -\frac{1}{2\sigma_j^2}(x - \mu_j)^2) $$

$$ \log(\frac{\frac{\pi_k}{\sigma_k} e^{a_j}}{\sum_{l=1}^K \frac{\pi_l}{\sigma_l} e^{a_l}}) = \log(\frac{\pi_k}{\sigma_k}) + \log{(e^{a_j})} - \log{(\sum_{l=1}^K \frac{\pi_l}{\sigma_l} e^{a_l})} $$

We apply the same operations as we did in the previous question, then we obtain:

$$ = \log(\pi_k) - \log(\sigma_k) -\frac{1}{2\sigma_j^2}(x - \mu_j)^2 $$
$$ = \log(\pi_k) - \log(\sigma_k) -\frac{x^2 - 2x\mu_k + \mu_k^2}{2\sigma^2} = \log(\pi_k) - \log(\sigma_k) +  \frac{\mu_k^2}{2\sigma^2} + \frac{x\mu_k}{\sigma^2} - \frac{x^2}{2\sigma^2}$$
Finally, we obtain a non-linear equation:
$$ \delta_k(x) = (\log(\pi_k) - \log(\sigma_k) + \frac{\mu_k^2}{2\sigma^2}) + x \frac{\mu_k}{\sigma^2} - x^2\frac{1}{2\sigma^2}$$

## Question 4 (???)
When the number of features p is large, there tends to be a deterioration in the performance of KNN and other local approaches that perform prediction using only observations that are near the test observation for which a prediction must be made. This phenomenon is known as the curse of dimensionality, and it ties into the fact that non-parametric approaches often perform poorly when p is large. We will now investigate this curse.

(a) Suppose that we have a set of observations, each with measurements on p = 1 feature, X. We assume that X is uniformly (evenly) distributed on [0, 1]. Associated with each observation is a response value. Suppose that we wish to predict a test observation’s response using only observations that are within 10 % of the range of X closest to that test observation. For instance, in order to predict the response for a test observation with X = 0.6, we will use observations in the range [0.55,0.65]. On average, what fraction of the available observations will we use to make the prediction?

(b) Now suppose that we have a set of observations, each with measurements on p = 2 features, X1 and X2. We assume that (X1, X2) are uniformly distributed on [0, 1] × [0, 1]. We wish to predict a test observation’s response using only observations that are within 10 % of the range of X1 and within 10 % of the range of X2 closest to that test observation. For instance, in order to predict the response for a test observation with X1 = 0.6 and X2 = 0.35, we will use observations in the range [0.55, 0.65] for X1 and in the range [0.3,0.4] for X2. On average, what fraction of the available observations will we use to make the prediction?

(c) Now suppose that we have a set of observations on p = 100 fea- tures. Again the observations are uniformly distributed on each feature, and again each feature ranges in value from 0 to 1. We wish to predict a test observation’s response using observations within the 10 % of each feature’s range that is closest to that test observation. What fraction of the available observations will we use to make the prediction?

(d) Using your answers to parts (a)–(c), argue that a drawback of KNN when p is large is that there are very few training observations “near” any given test observation.

(e) Now suppose that we wish to make a prediction for a test observation by creating a p-dimensional hypercube centered around the test observation that contains, on average, 10 % of the train- ing observations. For p = 1,2, and 100, what is the length of each side of the hypercube? Comment on your answer.

### Answer
???

## Question 5
We now examine the differences between LDA and QDA.

(a) If the Bayes decision boundary is linear, do we expect LDA or QDA to perform better on the training set? On the test set?

(b) If the Bayes decision boundary is non-linear, do we expect LDA or QDA to perform better on the training set? On the test set?

(c) In general, as the sample size n increases, do we expect the test prediction accuracy of QDA relative to LDA to improve, decline, or be unchanged? Why?

(d) True or False: Even if the Bayes decision boundary for a given problem is linear, we will probably achieve a superior test er- ror rate using QDA rather than LDA because QDA is flexible enough to model a linear decision boundary. Justify your answer.

### Answer

(a) Linear Discriminant Analysis (LDA) provides linear solutions to linear classification problems. In contrast, Quadratic Discriminant Analysis (QDA) provides a non-linear solution. We know that increasing the flexibility of a model leads to a decrease in training error, regardless of the true nature of the data.So, QDA will perform better on training set. However, the same may not hold for test error. If the decision boundary is linear, it is clear that LDA will perform better on the test set.

(b) Now, we have a non-linear dataset. In this case, we would obtain the same training set performance as in the previous scenario. However, in this case, QDA would perform better on the test set due to the non-linear nature of the data. This is because QDA is able to capture non-linear relationships between the predictors and response, whereas LDA is limited to linear relationships only.

(c) In general case, we expect the test prediction accuracy of QDA to improve relative to LDA. This is because, when the increase of the size of training set leads to reduce of the variance of the model. Which means a single data point cannot affect the model easily, if we increase the size of training set.

(d) FALSE. While increasing the flexibility of a model can reduce the training error rate, it doesn't necessarily mean that it will also reduce the test error rate. The test error is more indicative of the true nature of the data. Therefore, using a linear model like LDA, instead of a non-linear model like QDA, will generally lead to more accurate test set predictions and a lower test error rate.

## Question 6
Suppose we collect data for a group of students in a statistics class with variables X1 = hours studied, X2 = undergrad GPA, and Y = receive an A. We fit a logistic regression and produce estimated coefficient, $\hat{\beta}_0 = −6$, $\hat{\beta}_1 = 0.05$, $\hat{\beta}_2 = 1$.

(a) Estimate the probability that a student who studies for 40 h and has an undergrad GPA of 3.5 gets an A in the class.

(b) How many hours would the student in part (a) need to study to have a 50 % chance of getting an A in the class?

### Answer
$$ p(x) = \frac{e^{\beta_0 + \beta_1x_1 + \beta_2x_2}}{1 + e^{\beta_0 + \beta_1x_1 + \beta_2x_2}} = \frac{e^{-6 + 0.05x_1 + x_2}}{1 + e^{-6 + 0.05x_1 + x_2}} $$

(a) 
$$ => \frac{e^{-6 + 0.05 \times 40 + 3.5}}{1 + e^{-6 + 0.05 \times 40 + 3.5}} = 0.378$$

(b)
$$ \frac{1-p(x)}{p(x)} = e^{\beta_0 + \beta_1x_1 + \beta_2x_2} $$
$$ \frac{1-0.5}{0.5} = e^{-6 + 0.05 \times h + 3.5} => -6 + 3.5 + 0.05 \times h = ln(1) = 0 => h = 50 \ \text{hours}$$

## Question 7
Suppose that we wish to predict whether a given stock will issue a dividend this year (“Yes” or “No”) based on X, last year’s percent profit. We examine a large number of companies and discover that the mean value of X for companies that issued a dividend was $\bar{X}= 10$, while the mean for those that didn’t was $\bar{X}= 0$. In addition, the variance of X for these two sets of companies was $\sigma^2 = 36$. Finally, 80 % of companies issued dividends. Assuming that X follows a normal distribution, predict the probability that a company will issue a dividend this year given that its percentage profit was X = 4 last year.

### Answer
Recall that the density function for a normal random variable,
$$ f(x) = \frac{1}{\sqrt{2\pi}\sigma} \exp(-\frac{1}{2\sigma^2}(x - \mu_k)^2)$$
, and Bayes Theorem formula
$$ Pr(Y=k|X=x) = \frac{\pi_k f_k(x)}{\sum_{l=1}^K \pi_l f_l(x)} $$


Prior probabilities of groups are given in the question: '80 % of companies issued dividends'
$$ \pi_{\text{issued}}= 0.8, \pi_{\text{not issued}} = 0.2$$
If we compute the density functions for each group, we find that
$$ f_{\text{issued}}(X=4) = \frac{1}{\sqrt{2\pi}6} \exp(-\frac{1}{2\times36}(4 - 10)^2) = 0.099$$

$$ f_{\text{not issued}}(X=4) = \frac{1}{\sqrt{2\pi}6} \exp(-\frac{1}{2\times36}(4 - 0)^2) = 0.130$$

Then, we compute the probability that a company will issue a dividend this year
$$ Pr(Y=\text{issued}|X=4) = \frac{\pi_k f_k(x)}{\sum_{l=1}^K \pi_l f_l(x)} = \frac{0.8 \times 0.099}{0.8 \times 0.099 + 0.2 \times 0.130} = 0.752$$

## Question 8
Suppose that we take a data set, divide it into equally-sized training and test sets, and then try out two different classification procedures. First we use logistic regression and get an error rate of 20% on the training data and 30% on the test data. Next we use 1-nearest neighbors (i.e. K = 1) and get an average error rate (averaged over both test and training data sets) of 18%. Based on these results, which method should we prefer to use for classification of new observations? Why?

### Answer
Certainly, in this particular case, when performing KNN with K=1, it assigns a training example by looking at the single closest observation available in the training set (the point itself). Therefore, the training error will always be zero. However, this also means that the KNN classifier has a high variance value, which may lead to overfitting.

If we assume the error rate of KNN with K=1 as zero, then:
$$\frac{\text{training error} +  \text{test error}}{2} = 0.18 => \text{test error} = 0.36 $$
Based on these results, we can say that logistic regression has a lower test error rate than KNN with K=1 on this example. Therefore, we should prefer the logistic regression model.

## Qusetion 9
This problem has to do with odds.

(a) On average, what fraction of people with an odds of 0.37 of defaulting on their credit card payment will in fact default?

(b) Suppose that an individual has a 16% chance of defaulting on her credit card payment. What are the odds that she will default?

### Answer

In statistics and probability theory, the odds represent the likelihood of an event occurring. Specifically, the odds are the ratio of the probability of the event occurring to the probability of the event not occurring.

Odds = probability / (1 - probability)

(a)
$$ \frac{p(x)}{1 - p(x)} = 0.37 => p(x) = \frac{0.37}{1.37} = 0.27 $$


(b)
$$ \frac{p(x)}{1 - p(x)} = \frac{0.16}{1 - 0.16} = 0.19$$

## Question 10
Equation 4.32 derived an expression for $\log (\frac{Pr(Y =k|X=x)}{Pr(Y =K|X=x)})$ in the setting where $p > 1$, so that the mean for the kth class, $\mu_k$, is a p- dimensional vector, and the shared covariance $Σ$ is a $p × p$ matrix. However, in the setting with p = 1, (4.32) takes a simpler form, since the means $\mu_1,..., \mu_K$ and the variance $\sigma^2$ are scalars. In this simpler setting, repeat the calculation in (4.32), and provide expressions for $a_k$ and $b_{kj}$ in terms of $\pi_k, \pi_K, \mu_k, \mu_K, \text{and} \  \sigma^2$.

### Answer

$$ \frac{Pr(Y =k|X=x)}{Pr(Y =K|X=x)} = \frac{\pi_k f_k(x)}{\pi_K f_K(x)} = \frac{\pi_k \frac{1}{\sqrt{2\pi}\sigma} \exp(-\frac{1}{2\sigma^2}(x - \mu_k)^2)}{\pi_K \frac{1}{\sqrt{2\pi}\sigma} \exp(-\frac{1}{2\sigma^2}(x - \mu_K)^2)}$$

$$ \log(\frac{\pi_k f_k(x)}{\pi_K f_K(x)}) = \log(\frac{\pi_k f_k(x)}{\pi_K f_K(x)} = \log(\frac{\pi_k \frac{1}{\sqrt{2\pi}\sigma} \exp(-\frac{1}{2\sigma^2}(x - \mu_k)^2)}{\pi_K \frac{1}{\sqrt{2\pi}\sigma} \exp(-\frac{1}{2\sigma^2}(x - \mu_K)^2)}) $$

$$ = \log(\frac{\pi_k}{\pi_K}) - \frac{1}{2\sigma^2}(x - \mu_k)^2 + \frac{1}{2\sigma^2}(x - \mu_K)^2 $$

$$ = \log(\frac{\pi_k}{\pi_K}) - \frac{1}{2\sigma^2}(-2x(\mu_k-\mu_K) + (\mu_k^2 + \mu_K^2)) $$

$$ = \log(\frac{\pi_k}{\pi_K})-\frac{(\mu_k^2 + \mu_K^2)}{2\sigma^2} + \frac{x(\mu_k-\mu_K)}{\sigma^2} $$

$$ = a_k + \sum_{j=1}^p b_{k}x $$

where $a_k = \log(\frac{\pi_k}{\pi_K})-\frac{(\mu_k + \mu_K)}{2\sigma^2}$ and $b_{k} = \frac{(\mu_k-\mu_K)}{\sigma^2}$ 

## Question 11 (???)
Work out the detailed forms of $a_k$, $b_{kj}$, and $b_{kjl}$ in (4.33). Your answer should involve $\pi_k, \pi_K, \mu_k, \mu_K, \sum_k,$ and $\sum_K$.

### Answer

## Question 12
Suppose that you wish to classify an observation $X \isin \R$ into apples and oranges. You fit a logistic regression model and find that
$$ \hat{\text{Pr}}(Y=\text{orange}|X=x) =  \frac{\exp({\hat{\beta}_0 + \hat{\beta}_1X})}{1 + \exp({\hat{\beta}_0 + \hat{\beta}_1X})}$$
Your friend fits a logistic regression model to the same data using the softmax formulation in (4.13), and finds that
$$ \hat{\text{Pr}}(Y=\text{orange}|X=x) =  \frac{\exp({\hat{\alpha}_{\text{orange0}}+ \hat{\alpha}_{\text{orange1}}x})}{\exp({\hat{\alpha}_{\text{orange0}}+ \hat{\alpha}_{\text{orange1}}x}) + \exp({\hat{\alpha}_{\text{apple0}}+ \hat{\alpha}_{\text{apple1}}x})}$$

(a) What is the log odds of orange versus apple in your model?

(b) What is the log odds of orange versus apple in your friend’s model?

(c) Suppose that in your model, $\hat{\beta}_0 = 2$ and $\hat{\beta}_1=-1$. What are the coefficient estimates in your friend’s model? Be as specific as possible.

(d) Now suppose that you and your friend fit the same two models on a different data set. This time, your friend gets the coefficient estimates $\hat{\alpha}_{\text{orange0}} = 1.2$, $\hat{\alpha}_{\text{orange1}} = −2$, $\hat{\alpha}_{\text{apple0}} = 3$, $\hat{\alpha}_{\text{apple1}} = 0.6$. What are the coefficient estimates in your model?

(e) Finally, suppose you apply both models from (d) to a data set with 2,000 test observations. What fraction of the time do you expect the predicted class labels from your model to agree with those from your friend’s model? Explain your answer.

### Answer

(a) $$ \log(\text{odds}(\frac{\exp({\hat{\beta}_0 + \hat{\beta}_1X})}{1 + \exp({\hat{\beta}_0 + \hat{\beta}_1X})})) = \hat{\beta}_0 + \hat{\beta}_1X$$

(b) $$ \text{odds}(\frac{\hat{\text{Pr}}(Y=\text{orange}|X=x)}{\hat{\text{Pr}}(Y=\text{apple}|X=x)}) = \frac{\exp({\hat{\alpha}_{\text{orange0}}+ \hat{\alpha}_{\text{orange1}}x})}{\exp({\hat{\alpha}_{\text{apple0}}+ \hat{\alpha}_{\text{apple1}}x})}$$

$$ \log(\frac{\exp({\hat{\alpha}_{\text{orange0}}+ \hat{\alpha}_{\text{orange1}}x})}{\exp({\hat{\alpha}_{\text{apple0}}+ \hat{\alpha}_{\text{apple1}}x})}) = \hat{\alpha}_{\text{orange0}}+ \hat{\alpha}_{\text{orange1}}x - (\hat{\alpha}_{\text{apple0}}+ \hat{\alpha}_{\text{apple1}}x)$$

(c)
$$ \hat{\beta}_0 \approx \hat{\alpha}_{\text{orange0}} - \hat{\alpha}_{\text{apple0}}$$
$$ \hat{\beta}_0 \approx \hat{\alpha}_{\text{orange1}} - \hat{\alpha}_{\text{apple1}}$$

(d)
If we fit the same two models on a different data set, then
$$ \hat{\beta}_0 \approx \hat{\alpha}_{\text{orange0}} - \hat{\alpha}_{\text{apple0}} => \hat{\beta}_0 \approx 1.2 - 3 = -1.8$$
$$ \hat{\beta}_0 \approx \hat{\alpha}_{\text{orange1}} - \hat{\alpha}_{\text{apple1}} => \hat{\beta}_1 \approx -2 - 0.6 = -2.6$$

(e) ???