# Chapter 3 - Exercises

## Question 1
Describe the null hypotheses to which the p-values given in Table 3.4 correspond. Explain what conclusions you can draw based on these p-values. Your explanation should be phrased in terms of sales, TV, radio, and newspaper, rather than in terms of the coefficients of the linear model.

---
In Table 3.4, the null hypothesis for "TV" is that in presence of predictors "Radio" and "Newspaper", TV predictor has no effect on Sales response ($H_0: \beta_{\text{TV}} = 0$). The null hypothesis for "Radio" is that in the presence of predictors "TV" and "Newspaper", Radio predictors has no effect on Sales response ($H_0: \beta_{\text{Radio}} = 0$). And we can say same for "Newspaper" too.

Based on the p-values given in table 3.4, we can say:
- The p-values of TV and Radio ads are too low, so we can reject the null hypothesis for TV and Radio. We can say that TV and Radio ads have effect on Sales in presence of other predictors.
- But, the contrary for Newspaper ads. Newspaper ads have high p-value, so we cannot reject the null hypothesis. We can say that Newspaper ads have no significant effect in presence of other predictors.

## Question 2
Carefully explain the differences between the KNN classifier and KNN regression methods.

---
KNN classifier and KNN regression use similar formulas, but differ in their output type.

KNN classifier predicts the class label of a query point by computing probability that it belongs to a certain class based on the class labels of its K nearest neighbors. The output type is qualitative.
$Pr(Y=j|X=x_0) = \frac{1}{K} \sum_{i \in N_0} I(y_i = j)$

KNN regression predicts the output values of a query point by computing the average output value of its K nearest neighbors. The ouput type is quantitative.
$\hat{f}(x_0) = \frac{1}{K} \sum_{i \in N_0} y_i$

## Question 3 
Suppose we have a data set with five predictors, X1 = GPA, X2 = IQ, X3 = Level (1 for College and 0 for High School), X4 = Interaction between GPA and IQ, and X5 = Interaction between GPA and Level. The response is starting salary after graduation (in thousands of dollars). Suppose we use least squares to fit the model, and get $β_0$ = 50, $β_1$ = 20, $β_2$ = 0.07, $β_3$ = 35, $β_4$ = 0.01, $β_5$ = −10.

---
Based on the info gived in the question, the equation of our prediction model is: $\hat{y} = \beta_0 + \beta_1 \times \text{GPA} + \beta_2 \times \text{IQ} + \beta_3 \times \text{Level} + \beta_4 \times (\text{GPA}:\text{IQ}) + \beta_5 \times (\text{Level}:\text{GPA})$

(a)    
i. The coefficient for the Level variable is positive, indicating that on average, a college graduate earns more than a high school graduate. However, there is also an interaction term between GPA and Level, with a negative coefficient.

For a fixed value of GPA and IQ, the predicted earnings for a college graduate are 20GPA + 0.007IQ + 35 + 0.01(GPA:IQ) - 10*(GPA) units, while the predicted earnings for a high school graduate are 20GPA + 0.007IQ + 0.01(GPA:IQ) units.

Without knowing the specific value of GPA, we cannot definitively say whether this suggestion is true.

ii. As we saw above, we cannot definitively say whether this suggestion is true, without knowing the specific valeu of GPA.

iii. For a fixed value of IQ and GPA, high school graduates earn more, on average, than college graduates provided that the GPA is high enough. Because, 20GPA + 0.007IQ + 35 + 0.01(GPA:IQ) - 10*(GPA) eqaution will be lower than 20GPA + 0.007IQ + 0.01(GPA:IQ).

This suggestion is true.

iv. This suggestion contradicts the third suggestion, indicating that it is not true.

(b)

Prediction for a college graduate with IQ 110 and a GPA 4.0:

$\hat{y} = 50 + 20 \times 4.0 + 0.07 \times 110 + 35 \times 1 + 0.01 \times (4.0 \times 110) + -10 \times 4.0 = 137.1K$ 

(c)
It is false to determine the impact of an interaction term by looking solely at the coefficient value. Instead, it is necessary to consider the p-value of the interaction term in the presence of other predictors.

## Question 4
I collect a set of data (n = 100 observations) containing a single predictor and a quantitative response. I then fit a linear regression model to the data, as well as a separate cubic regression, i.e. $Y = \beta_0 + \beta_1 X + \beta_2 X^2 + \beta_3 X^3 + \epsilon$.

---
(a) When the flexibility of a regression model increases, such as when moving from a linear to a cubic model, the training RSS will generally decrease. Therefore, even if the true relationship between the variables is linear, a cubic model will likely have a lower training RSS value due to its increased flexibility.

(b) On the contrary (a), the final model we get with cubic model for this data will overfit the data, means that it'll have higher test RSS value than linear model.

(c) The cubic regression model will have RSS lower than the linear regression model due to higher flexibility.

(d) There is not enough information to answer this one. Because if we have a quadratic relationship, the linear regression model could get lower test RSS than the cubic model. But if the degree of relation is far from linear, then the cubic model will have lower test RSS. So, we cannot definitely say which one will have lower RSS without definite information about the true relation.

## Question 5
Consider the fitted values that result from performing linear regression without an intercept. In this setting, the ith fitted value takes the form $\hat{y}_i = x_i\hat{\beta}$, where $\hat{\beta} = (\sum_{i=1}^n x_iy_i)/(\sum_{i'=1}^n x_{i'}^2)$ 

Show that we can write $\hat{y}_i = \sum_{i'=1}^n a_{i'}y_{i'}$

What is $a_{i'}$?

---

???

## Question 6
Using (3.4), argue that in the case of simple linear regression, the least squares line always passes through the point ($\bar{x}$, $\bar{y}$).

---
Equation (3.4) is 
$$ \hat{\beta}_1 = \frac{\sum_{i=1}^n (x_i - \text{\={x}})(y_i - \text{\={y}})}{\sum_{i=1}^n (x_i - \text{\={x}})^2}$$

$$\hat{\beta}_0 = \bar{y} - \hat{\beta}_1 \bar{x}$$

$\hat{\beta}_0 = \bar{y} - \hat{\beta}_1 \bar{x}$ =>  $\bar{y} = \hat{\beta}_0 + \hat{\beta}_1 \bar{x}$, which is the formula of simple linear regression.

## Question 7
It is claimed in the text that in the case of simple linear regression of Y onto X, the $R^2$ statistic (3.17) is equal to the square of the correlation between X and Y (3.18). Prove that this is the case. For simplicity, you may assume that $\bar{x}$ = $\bar{y}$ = 0.

---
???