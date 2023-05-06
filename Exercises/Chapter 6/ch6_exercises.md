# Chapter 6 - Exercises

## Question 1
We perform best subset, forward stepwise, and backward stepwise selection on a single data set. For each approach, we obtain $p + 1$ models, containing $0, 1, 2, . . . , p$ predictors. Explain your answers:


(a) Which of the three models with k predictors has the smallest training RSS?

(b) Which of the three models with k predictors has the smallest test RSS?

(c) True or False:

- i. The predictors in the k-variable model identified by forward stepwise are a subset of the predictors in the (k+1)-variable model identified by forward stepwise selection.

- ii. The predictors in the k-variable model identified by back- ward stepwise are a subset of the predictors in the (k + 1)- variable model identified by backward stepwise selection.

- iii. The predictors in the k-variable model identified by back- ward stepwise are a subset of the predictors in the (k + 1)- variable model identified by forward stepwise selection.

- iv. The predictors in the k-variable model identified by forward stepwise are a subset of the predictors in the (k+1)-variable model identified by backward stepwise selection.

- v. The predictors in the k-variable model identified by best subset are a subset of the predictors in the (k + 1)-variable model identified by best subset selection.

### Answer
(a) Since best subset selection considers all possible combinations of variables to minimize the training RSS, it has a higher chance of giving the best subset solution compared to forward stepwise and backward stepwise selection algorithms. Therefore, it is more likely to obtain the best training RSS with best subset selection.

(b) Subset selection algorithms aim to choose the best subset of variables that minimizes the training RSS. However, selecting the best subset based on this criterion alone does not guarantee the subset with the lowest test RSS. To determine the subset with the lowest test RSS, other metrics such as $C_p$, AIC, BIC, and Adjusted $R^2$ need to be considered.

(c)

- i. True. The forward stepwise selection algorithm starts with a null model (which contains no variables) and then, on each iteration, adds the variable that gives the most improvement to the model until a stopping criterion is met. This process continues until the desired number of variables is reached, resulting in a (k+1)-variable model obtained by adding an additional variable to the k-variable model.

- ii. True. The backward stepwise selection algorithm begins with a full model (which contains all the variables) and then, on each iteration, removes the variable that has the lowest impact on the model until a stopping criterion is met. This results in a k-variable model obtained by removing a variable from the (k+1)-variable model.

- iii. It is possible for a k-variable model identified by backward stepwise to be a subset of the (k+1)-variable model identified by forward stepwise. However, in general, since these two algorithms start with different models, the full model and the null model respectively, it is more likely that the final models obtained from each algorithm will have different subsets of variables.

- iv. Same answer as (iii).

- v. False. The best subset selection algorithm considers all possible combinations of $\binom{p}{k}$ variables for each value of k. Therefore, it is possible to have different subsets of variables for each value of k, and we cannot say that a k-variable model is a subset of the (k+1)-variable model with certainty.


## Question 2
For parts (a) through (c), indicate which of i. through iv. is correct. Justify your answer.

(a) The lasso, relative to least squares, is:

- i. More flexible and hence will give improved prediction accuracy when its increase in bias is less than its decrease in variance.

- ii. More flexible and hence will give improved prediction accuracy when its increase in variance is less than its decrease in bias.

- iii. Less flexible and hence will give improved prediction accuracy when its increase in bias is less than its decrease in variance.

- iv. Less flexible and hence will give improved prediction accuracy when its increase in variance is less than its decrease in bias.

(b) Repeat (a) for ridge regression relative to least squares.

(c) Repeat (a) for non-linear methods relative to least squares.

### Answer
(a) (iii) is correct. When we add a penalization term to the least squares regression formula, we decrease variance at the cost of a slight increase in bias. As a result, the lasso model is less flexible than the least squares model, since the lasso may shrink some of the variables to exactly zero, which results in a less flexible model.

(b) Statement (iii) is also correct for the comparison of ridge regression and least squares. Since ridge regression is also a regularization method similar to lasso, using ridge regression leads to a less flexible model compared to least squares.

(c) (ii) is correct. Nonlinear models are typically more flexible than least squares regression. If we choose an appropriate nonlinear model, we can achieve a decrease in bias that is greater than the increase in variance. However, if we use a more flexible model than what is required, we may overfit the data, resulting in high variance and low bias.

## Question 3
Suppose we estimate the regression coefficients in a linear regression model by minimizing

$$ \sum_{i=1}^n \bigg(y_i - \beta_0 - \sum_{j=1}^p \beta_j x_{ij}\bigg)^2  \ \ \text{subject to} \sum_{j=1}^p |\beta_j| \leq s $$

for a particular value of s. For parts (a) through (e), indicate which of i. through v. is correct. Justify your answer.

(a) As we increase s from 0, the training RSS will:

- i. Increase initially, and then eventually start decreasing in an
inverted U shape.

- ii. Decrease initially, and then eventually start increasing in a U shape.

- iii. Steadily increase. 

- iv. Steadily decrease. 

- v. Remain constant.

(b) Repeat (a) for test RSS. 

(c) Repeat (a) for variance.

(d) Repeat (a) for (squared) bias.

(e) Repeat (a) for the irreducible error.

### Answer
Recall that the given formulation is used for the Lasso.

(a) As we know from the formulation of the Lasso, the term "s" is used to impose a restriction on coefficient estimations. As we increase "s" from 0, the model becomes less restrictive and more flexible. With the increase in flexibility, the training RSS decreases continuously. So the statement (iv) is correct. 

(b) When we set "s" equal to 0, we obtain a null model that only contains the intercept. As we increase "s", the test RSS generally decreases until the true level of flexibility is reached. However, for each increase beyond the required flexibility level, the model will have high variance, which can lead to overfitting and an increase in test RSS. Therefore, statement (ii) is appropriate for the test RSS situation.

(c) When "s" is set equal to 0, we obtain a null model that only contains the intercept. The null model has low variance due to its low flexibility. As we increase the value of "s", the model becomes less restrictive and more flexible, which leads to higher variance. So, the statement (iii) is correct.

(d) When we set "s" equal to 0, we obtain a null model that only contains the intercept. Due to its simplicity, the null model will have high bias and low variance. As we increase the term "s" from 0, the model becomes less restrictive and more flexible, which leads to a decrease in bias and an increase in variance. Therefore, statement (iv) is correct.

(e) The statement (v) is correct. The irreducible error represents the error that cannot be reduced by any model or algorithm because it is inherent in the data itself. It is a constant term that is independent of the model complexity or the size of the dataset. Therefore, optimizing the model to the data will not reduce the irreducible error.

## Question 4
Suppose we estimate the regression coefficients in a linear regression model by minimizing

$$ \sum_{i=1}^n \bigg(y_i - \beta_0 - \sum_{j=1}^p \beta_j x_{ij}\bigg)^2  + \lambda \sum_{j=1}^p \beta_j^2 $$

for a particular value of λ. For parts (a) through (e), indicate which of i. through v. is correct. Justify your answer.

(a) As we increase λ from 0, the training RSS will:

- i. Increase initially, and then eventually start decreasing in an inverted U shape.

- ii. Decrease initially, and then eventually start increasing in a U shape.

- iii. Steadily increase.

- iv. Steadily decrease.

- v. Remain constant.

(b) Repeat (a) for test RSS. 

(c) Repeat (a) for variance.

(d) Repeat (a) for (squared) bias.

(e) Repeat (a) for the irreducible error.

## Answer
The regularization parameter $\lambda$ in this formulation adjusts the impact of the penalization term on the coefficient estimations. More we increase the value of $\lambda$, the more we reduce flexibility of the model.

(a) When $\lambda = 0$, the regularization term has no impact on the least squares method. As we increase $\lambda$ from 0, the least squares method becomes less flexible, and the shrinkage of coefficient estimates will increase. Consequently, the training RSS will increase. Therefore, statement (iii) is correct.

(b) As we increase $\lambda$ from 0, we can obtain a decrease in variance with a small increase in bias until a balance point is reached. However, if we continue increasing $\lambda$ beyond this point, the model will become too constrained and start underfitting the data. Consequently, the test RSS will decrease initially, but then start increasing in a U-shape as we increase $\lambda$ further. Therefore, statement (ii) is correct.

(c) As we increase $\lambda$ from 0, the impact of regularization on least squares will increase continuously which leads to steadly decrease in variance. Therefore, statement (iv) is correct.

(d) As we increase $\lambda$ from 0, the impact of regularization on least squares will increase continuously which leads to steadly increase in bias. Therefore, statement (iii) is correct.

(e) The statement (v) is correct. The irreducible error represents the error that cannot be reduced by any model or algorithm because it is inherent in the data itself. It is a constant term that is independent of the model complexity or the size of the dataset. Therefore, optimizing the model to the data will not reduce the irreducible error.

## Question 5
It is well-known that ridge regression tends to give similar coefficient values to correlated variables, whereas the lasso may give quite different coefficient values to correlated variables. We will now explore this property in a very simple setting.

Suppose that n = 2, p = 2, $x_{11} = x_{12}$, $x_{21} = x_{22}$. Furthermore, suppose that $y_1+y_2 =0$ and $x_{11}+x_{21} =0$ and $x_{12}+x_{22}=0$, so that the estimate for the intercept in a least squares, ridge regression, or lasso model is zero: $\hat{\beta}_0 = 0$.

(a) Write out the ridge regression optimization problem in this setting.

(b) Argue that in this setting, the ridge coefficient estimates satisfy βˆ 1 = βˆ 2 .

(c) Write out the lasso optimization problem in this setting.

(d) Argue that in this setting, the lasso coefficients βˆ1 and βˆ2 are not unique—in other words, there are many possible solutions to the optimization problem in (c). Describe these solutions.

### Answer
(a) As we know, the ridge regression make coefficient estimates to minimize the following equation

$$ \sum_{i=1}^n \bigg(y_i - \hat{\beta}_0 - \sum_{j=1}^p \hat{\beta}_j x_{ij}\bigg)^2  + \lambda \sum_{j=1}^p \hat{\beta}_j^2 $$

since $\hat{\beta}_0$, n=2, and p=2, we can simplify the equation as

$$ \sum_{i=1}^{n=2} \bigg(y_i - \sum_{j=1}^{p=2} \hat{\beta}_j x_{ij}\bigg)^2  + \lambda \sum_{j=1}^{p=2} \hat{\beta}_j^2 $$

$$ \implies (y_1 - \hat{\beta}_1x_{11} - \hat{\beta}_2x_{12})^2 + (y_2 - \hat{\beta}_1x_{21} - \hat{\beta}_2x_{22})^2 + \lambda(\hat{\beta}_1^2 + \hat{\beta}_2^2)$$

(b) If we suppose that 

$$ x_{11} = x_{12}, \ x_{21} = x_{22}, \ y_0 = y_1. \ x_{11}+x_{21} =0, \text{and}  \ x_{12}+x_{22}=0 $$

, and to simplify the equation if we declare 

$$ x_{11} = x_{12} = a \ \text{and} \ x_{21} = x_{22} = b$$
$$ \implies a = -b $$

The ridge regression equation becomes

$$ \implies \bigg(y_1 - a(\hat{\beta}_1 - \hat{\beta}_2)\bigg)^2 + \bigg(-y_1 + a(\hat{\beta}_1 - \hat{\beta}_2)\bigg)^2 + \lambda(\hat{\beta}_1^2 + \hat{\beta}_2^2)$$

$$ \begin{equation} \begin{split} f &=\bigg(y_1 - a(\hat{\beta}_1 - \hat{\beta}_2)\bigg)^2 + (-1)^2 \bigg(y_1 - a(\hat{\beta}_1 - \hat{\beta}_2)\bigg)^2 + \lambda(\hat{\beta}_1^2 + \hat{\beta}_2^2) \\ &=2\bigg(y_1 - a(\hat{\beta}_1 - \hat{\beta}_2)\bigg)^2 + \lambda(\hat{\beta}_1^2 + \hat{\beta}_2^2) \\ &= 2\bigg( y_1^2 -2y_1a(\hat{\beta}_1 - \hat{\beta}_2)+ a^2(\hat{\beta}_1^2 - 2\hat{\beta}_1\hat{\beta}_2 + \hat{\beta}_2^2)\bigg) + \lambda(\hat{\beta}_1^2 + \hat{\beta}_2^2)\end{split} \end{equation}$$

To find the values of $\hat{\beta}_1$ and $\hat{\beta}_2$ that minimize the given equation, we can take partial derivatives with respect to $\hat{\beta}_1$ and $\hat{\beta}_2$.

$$ \frac{\partial}{\partial \hat{\beta}_1} f = -4y_1a + 4a^2\hat{\beta}_1 - 4a^2\hat{\beta}_2 + 2\lambda\hat{\beta}_1 = 0$$

$$ \implies \hat{\beta}_1\bigg( 4a^2 + 2\lambda \bigg) - 4y_1a - 4a^2\hat{\beta}_2 = 0$$

$$ \implies \hat{\beta}_1 = \frac{4y_1a + 4a^2\hat{\beta}_2}{4a^2 + 2\lambda} $$

---

$$ \frac{\partial}{\partial \hat{\beta}_2} f = -4y_1a + 4a^2\hat{\beta}_2 - 4a^2\hat{\beta}_1 + 2\lambda\hat{\beta}_2 = 0$$

$$ \implies \hat{\beta}_2\bigg( 4a^2 + 2\lambda \bigg) - 4y_1a - 4a^2\hat{\beta}_1 = 0$$

$$ \implies \hat{\beta}_2 = \frac{4y_1a + 4a^2\hat{\beta}_1}{4a^2 + 2\lambda} $$

...

(c) The Lasso make coefficient estimates to minimize the following equation

$$ \sum_{i=1}^n \bigg(y_i - \hat{\beta}_0 - \sum_{j=1}^p \hat{\beta}_j x_{ij}\bigg)^2  + \lambda \sum_{j=1}^p |\hat{\beta}_j| $$

since $\hat{\beta}_0$, n=2, and p=2, we can simplify the equation as

$$ \sum_{i=1}^{n=2} \bigg(y_i - \sum_{j=1}^{p=2} \hat{\beta}_j x_{ij}\bigg)^2  + \lambda \sum_{j=1}^{p=2} |\hat{\beta}_j| $$

$$ \implies (y_1 - \hat{\beta}_1x_{11} - \hat{\beta}_2x_{12})^2 + (y_2 - \hat{\beta}_1x_{21} - \hat{\beta}_2x_{22})^2 + \lambda(|\hat{\beta}_1| + |\hat{\beta}_2|)$$

(d) ...


## Question 6
We will now explore (6.12) and (6.13) further.

- (a) Consider (6.12) with p = 1. For some choice of y1 and λ > 0, plot (6.12) as a function of β1. Your plot should confirm that (6.12) is solved by (6.14).

- (b) Consider (6.13) with p = 1. For some choice of y1 and λ > 0, plot (6.13) as a function of β1. Your plot should confirm that (6.13) is solved by (6.15).

### Answer
Recall that

$$ \sum_{i=1}^p \bigg(y_i - \hat{\beta}_j\bigg)^2  + \lambda \sum_{j=1}^p \hat{\beta}_j^2 \tag{6.12} $$

and 

$$ \sum_{i=1}^p \bigg(y_i - \hat{\beta}_j\bigg)^2  + \lambda \sum_{j=1}^p |\hat{\beta}_j| \tag{6.13} $$

(a) If we assume p=1, the equation (6.12) will take the following form

$$ \sum_{i=1}^{p=1} \bigg(y_i - \hat{\beta}_j\bigg)^2  + \lambda \sum_{j=1}^{p=1} \hat{\beta}_j^2 $$

$$ \begin{equation} \begin{split} &= (y_1 - \hat{\beta}_1)^2 + \lambda \hat{\beta}_1^2 \\ &= \hat{\beta}_1^2(\lambda+1) - 2y_1\hat{\beta}_1 + y_1^2 \end{split} \end{equation}$$

For $\lambda = 1$ and $y_1 = 4$, we should find $\hat{\beta}_1 = \frac{4}{1+1} = 2$

![Figure 2](/figures/Figure_2.png)

(b) If we assume p=1, the equation (6.13) will take the following form

$$ \sum_{i=1}^{p=1} \bigg(y_i - \hat{\beta}_j\bigg)^2  + \lambda \sum_{j=1}^{p=1} |\hat{\beta}_j| $$

$$ \begin{equation} \begin{split} &= (y_1 - \hat{\beta}_1)^2 + \lambda |\hat{\beta}_1| \\ &= \hat{\beta}_1^2 -2y_1\hat{\beta}_1 + y_1^2 + \lambda|\hat{\beta}_1|\end{split} \end{equation}$$

Recall that 

$$ \hat{\beta}_{j,\lambda}^L = \begin{cases} y_j - \lambda/2 & \text{if} & y_j \gt \lambda/2 \\ y_j + \lambda/2 & \text{if} & y_j \lt -\lambda/2 \\ 0 & \text{if} & |y_j| \leq \lambda/2 \end{cases} \tag{6.15}$$

- For $\lambda = 2$ and $y_1 = 4$, we should find 

$$  \text{Since} \ y_1=4 \gt 1 = \lambda/2 \implies \hat{\beta}_1 = 4 - 2/2 = 3$$

- For $\lambda = 2$ and $y_1 = -3$, we should find 

$$  \text{Since} \ y_1=-3 \lt -1 = \lambda/2 \implies \hat{\beta}_1 = -3+ 2/2 = -2$$


- For $\lambda = 2$ and $y_1 = -1$, we should find 

$$  \text{Since} \ |y_1|=1 \leq 1 = \lambda/2 \implies \hat{\beta}_1 = 0$$

1|2|3|
|:-:|:-:|:-:|
|![Figure 3](/figures/Figure_3.png)|![Figure 4](/figures/Figure_4.png)| ![Figure 5](/figures/Figure_5.png)|

## Question 7
...