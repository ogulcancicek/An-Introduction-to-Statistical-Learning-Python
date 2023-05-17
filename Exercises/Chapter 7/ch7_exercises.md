# Chapter 7 - Exercises

## Question 1
1. It was mentioned in the chapter that a cubic regression spline with one knot at ξ can be obtained using a basis of the form $x, x^2, x^3$, $(x−ξ)_+^3$,where $(x−ξ)_+^3 =(x−ξ)^3$ if $x>ξ $ and equals 0 otherwise. We will now show that a function of the form

$$ f(x) = \beta_0 + \beta_1 x + \beta_2 x^2 + \beta_3 x^3 + \beta_4 (x−ξ)_+^3$$

is indeed a cubic regression spline, regardless of the values of $\beta_0,\beta_1,\beta_2,\beta_3,\beta_4$.

(a) Find a cubic polynomial

$$ f_1(x) = a_1 + b_1 x + c_1 x^2 + d_1 x^3 $$

such that $f(x) = f_1(x)$ for all $x \leq ξ$. Express $a_1, b_1, c_1, d_1$ in terms of $\beta_0,\beta_1,\beta_2,\beta_3,\beta_4$.

(b) Find the cubic polynomial

$$ f_2(x) = a_2 + b_2 x + c_2 x^2 + d_2 x^3 $$

such that $f(x) = f_2(x)$ for all $x \gt ξ$. Express $a_2, b_2, c_2, d_2$ in terms of $\beta_0,\beta_1,\beta_2,\beta_3,\beta_4$. We have now established that f(x) is a piecewise polynomial.

(c) Show that f1(ξ) = f2(ξ). That is, f(x) is continuous at ξ.

(d) Show that f1′(ξ) = f2′(ξ). That is, f′(x) is continuous at ξ.

(e) Show that f′′(ξ) = f′′(ξ). That is, f′′(x) is continuous at ξ.

Therefore, f(x) is indeed a cubic spline.

### Answer
(a)

$$ x \leq ξ \implies (x−ξ)_+^3 = 0$$

$$ \implies f(x) = \beta_0 + \beta_1 x + \beta_2 x^2 + \beta_3 x^3 $$

$$ f(x) = f_1(x) \implies \begin{cases} a_1 = \beta_0 \\ b_1 = \beta_1 \\ c_1 = \beta_2 \\ d_1 = \beta_3 \\ \end{cases} $$



(b)

$$ x \gt ξ \implies (x−ξ)_+^3 = (x−ξ)^3$$

$$ \begin{split} f(x) &= \beta_0 + \beta_1 x + \beta_2 x^2 + \beta_3 x^3 + \beta_4  (x−ξ)^3 \\ &=\beta_0 + \beta_1 x + \beta_2 x^2 + \beta_3 x^3 + \beta_4 (x^3 - 3x^2ξ + 3xξ^2 - 3ξ^3) \\ &= \beta_0 - \beta_4 ξ^3 + x \bigg(\beta_1 + 3\beta_4ξ^2 \bigg) + x^2 \bigg(\beta_2 - 3\beta_4ξ \bigg) + x^3 \bigg(\beta_3 + \beta_4 \bigg) \end{split}$$


$$ f(x) = f_1(x) \implies \begin{cases} a_2 = \beta_0 - \beta_4 ξ^3 \\ b_2 = \beta_1 + 3\beta_4ξ^2 \\ c_2 = \beta_2 - 3\beta_4ξ \\ d_2 = \beta_3 + \beta_4 \end{cases} $$


(c)

$$ \begin{split} f(x) =& \begin{cases} f_1(x) & \text{if} & x \leq ξ \\ f_2(x) & \text{if} & x \gt ξ\end{cases} \\ =& \begin{cases} \beta_0 + \beta_1 x + \beta_2 x^2 + \beta_3 x^3 \\ \beta_0 - \beta_4 ξ^3 + x \bigg(\beta_1 + 3\beta_4ξ^2 \bigg) + x^2 \bigg(\beta_2 - 3\beta_4ξ \bigg) + x^3 \bigg(\beta_3 + \beta_4 \bigg)\end{cases}\end{split}$$

$f_1(x) = f_2(x)$ at the point ξ, so if we compute $f_1$ and $f_2$ for $x=ξ$

$$ f_1(x) = \beta_0 + \beta_1 x + \beta_2 x^2 + \beta_3 x^3$$

$$ \begin{split} f_2(x) &= \beta_0 - \beta_4 x^3 + x \bigg(\beta_1 + 3\beta_4x^2 \bigg) + x^2 \bigg(\beta_2 - 3\beta_4x \bigg) + x^3 \bigg(\beta_3 + \beta_4 \bigg) \\ &= \beta_0 - \beta_4 x^3 + x \beta_1 + 3 \beta_4 x^3 + x^2 \beta_2 - 3 \beta_4 x^3 + x^3 \beta_3 + x^3 \beta_4 \\ &= \beta_0 + \beta_1 x + \beta_2 x^2 + \beta_3 x^3 \end{split}$$

Therefore, we have $f_1(x) = f_2(x)$, so f(x) is continuous at the point ξ.

(d)

$$ f_1'(x) = \beta_1 + 2\beta_2 x + 3\beta_3 x^2$$

$$ f_2'(x) = \beta_1 + 3\beta_4ξ^2 + 2x \bigg(\beta_2 - 3\beta_4ξ \bigg) + 3x^2 \bigg(\beta_3 + \beta_4 \bigg) $$

At the point ξ, we get

$$ \begin{split} f_2'(x) &= \beta_1 + 3\beta_4x^2 + 2x \bigg(\beta_2 - 3\beta_4x \bigg) + 3x^2 \bigg(\beta_3 + \beta_4 \bigg) \\ &= \beta_1 + 3\beta_4x^2 + 2x\beta_2 - 6\beta_4x^2 + 3\beta_3x^2 + 3\beta_4x^2 \\ &= \beta_1 + 2\beta_2 x + 3\beta_3 x^2\end{split}$$


Therefore, we have $f_1(x)' = f_2(x)'$, so f'(x) is continuous at the point ξ.

(e)

$$ f_1''(x) = 2\beta_2 + 6\beta_3 x$$

$$ f_2''(x) = 2\bigg(\beta_2 - 3\beta_4ξ \bigg) + 6x\bigg(\beta_3 + \beta_4 \bigg) $$

At the point ξ, we get

$$ \begin{split} f_2''(x) &= 2\bigg(\beta_2 - 3\beta_4x \bigg) + 6x\bigg(\beta_3 + \beta_4 \bigg) \\ &= 2\beta_2 - 6x\beta_4 + 6x\beta_3 + 6x\beta_4 \\ &= 2\beta_2 + 6x\beta_3\end{split}$$

Therefore, we have $f_1(x)'' = f_2(x)''$, so f''(x) is continuous at the point ξ.

## Question 2
Suppose that a curve gˆ is computed to smoothly fit a set of n points using the following formula:

$$ \hat{g} = \arg \min_g \bigg(\sum_{i=1}^n (y_i - g(x_i))^2 + \lambda \int \bigg[ g^{(m)}(x)\bigg]^2 dx \bigg),$$

where $g^{(m)}$ represents the mth derivative of g (and $g^{(0)}$ = g). Provide example sketches of gˆ in each of the following scenarios.

(a) $\lambda=\infty,\ m = 0$

(b) $\lambda=\infty,\ m = 1$

(c) $\lambda=\infty,\ m = 2$

(d) $\lambda=\infty,\ m = 3$

(e) $\lambda=0,\ m = 3$

### Answer

Assume that g(x) is an exponential function, such as 

$$ g(x) =  2 * \exp(0.5*x) + 1$$

![Figure 6](/figures/Figure_6.png)

(a)

When $\lambda=\infty$ the loss term is ignored so we can look only at the penalty term; the function is hence minimized where the penalty term is zero.

In this scenario, the penalty term is zero when $g(x) = 0$.

![Figure 7](/figures/Figure_7.png)

(b)

In this scenario, the penalty term is zero when $g(x) = c$, where $c$ is any constant, because the derivative of a constant is zero. Therefore, to minimize the given function in this case, we can choose the constant value that makes the $g$ function equal to the average value of the true target values. Such as,

$$ g(x) = \frac{1}{n} \sum_{i=1}^n y_i$$

![Figure 8](/figures/Figure_8.png)
 
(c)

In scenario (c), the penatly term is zero when g is a linear function, such as $g(x) = ax +b$, because the second derivative of a linear function is zero.

![Figure 9](/figures/Figure_9.png)

(d)

In this scenario, the g would be a quadratic function, because the third derivative of a quadratic function is zero. Therefore, the penatly term would be zero when g takes a quadratic form in this scenario.

![Figure 10](/figures/Figure_10.png)

(e)

The penatly coefficient $\lambda=0$, this removes the impact of the penalty on the sum of squares method. So, it is completely unconstrained sum of squares method.

![Figure 11](/figures/Figure_11.png)


## Question 3
Suppose we fit a curve with basis functions $b_1(X) = X, b_2(X) = (X-1)^2I(X \geq 1)$. (Note that $I(X \geq 1)$ equals to 1 for $X \geq 1$ and 0 otherwise.) We fit the linear regression model

$$ Y = \beta_0 + \beta_1 b_1(X) + \beta_2 b_2(X) + \epsilon $$

and obtain coefficient estimates $\hat{\beta}_0 = 1, \hat{\beta}_1 = 1, \hat{\beta}_2 = -2$. Sketch the estimated cureve between X = -2 and X = 2. Not the intercepts, slopes, and other relevant information.

### Answer

When we plot the fitted curve, we get

![Figure 12](/figures/Figure_12.png)

As we can guess, since we fit the curve using two different basis functions, we get a curve that has different slopes in two different areas of the plot.

$$ \text{For} \ X \lt 1, \ \text{we get} \ \hat{f}(X) = 1 + X $$

When $X$ is less than 1, the second basis function returns 0, indicating that it does not have an impact on the curve. Thus, we can conclude that the slope of the curve is 1 when the value of $X$ is less than 1, and the curve is linear in this region. The intercept of the curve is 1.

$$ \text{For} \ X \geq 1, \ \text{we get} \ \hat{f}(X) = 1 + X - 2(X-1)^2 $$

Taking derivative of this equation

$$ \hat{f}(X) = -4X + 5 $$

On the other hand, when the value of $X$ is equal to or larger than 1, the second basis function has an impact on the curve. In this region, the curve takes a quadratic form instead of being linear. The slope of the curve is determined by the value of $X$.

## Question 4
Suppose we fit a curve with basis functions $b_1(X) = I(0 \leq X \leq 2) - (X-1)I(1 \leq X \leq 2),\ b_2(X) = (X-3)I(3 \leq X \leq 4) + I(4 \lt X \leq 5)$. (Note that $I(X \geq 1)$ equals to 1 for $X \geq 1$ and 0 otherwise.) We fit the linear regression model

$$ Y = \beta_0 + \beta_1 b_1(X) + \beta_2 b_2(X) + \epsilon$$

and obtain coefficient estimates $\hat{\beta}_0 = 1, \hat{\beta}_1 = 1, \hat{\beta}_2 = 3$. Sketch the estimated cureve between X = -2 and X = 6. Not the intercepts, slopes, and other relevant information.

### Answers

![Figure 13](/figures/Figure_13.png)

$$ \hat{Y} = \begin{cases} 1 & \text{if} & X \in [-2, 0[ \bigcup [2, 3] \bigcup [5, 6] \\ 2& \text{if} & X \in [0,1[ \\ 4 & \text{if} & X \in ]4,5] \\ 3 - X & \text{if} & X \in [1,2] \\ 3X - 8 & \text{if} & X \in [3,4 ]\end{cases} $$

## Question 5
Consider two curves, $\hat{g}_1$ and $\hat{g}_2$, defined by

$$ \hat{g}_1 = \arg \min_g \bigg(\sum_{i=1}^n (y_i - g(x_i))^2 + \lambda \int \bigg[ g^{(3)}(x)\bigg]^2 dx \bigg) $$

$$ \hat{g}_2 = \arg \min_g \bigg(\sum_{i=1}^n (y_i - g(x_i))^2 + \lambda \int \bigg[ g^{(4)}(x)\bigg]^2 dx \bigg) $$

where $g^{(m)}$ represents mth derivative of g.

(a) As $\lambda \rightarrow \infty$, will $\hat{g}_1$ or $\hat{g}_2$ have the smaller training RSS?

(b) As $\lambda \rightarrow \infty$, will $\hat{g}_1$ or $\hat{g}_2$ have the smaller test RSS?

(c) For $\lambda = 0$, will $\hat{g}_1$ or $\hat{g}_2$ have the smaller training RSS?

### Answer

(a) As $\lambda \rightarrow \infty$, our goal is to minimize the given functions. Consequently, the third derivative of $\hat{g}_1$ will approach zero, resulting in a quadratic form. Similarly, the fourth derivative of $\hat{g}_2$ will approach zero, indicating a cubic form. Since $\hat{g}_2$ has a higher degree than $\hat{g}_1$, it possesses greater flexibility. Thus, $\hat{g}_2$ will likely have a lower training RSS compared to $\hat{g}_1$ due to its higher flexibility.

(b) Without any information about the true relationship of the dataset used to fit these two curves, it is difficult to make definitive conclusions. The choice between $\hat{g}_1$ and $\hat{g}_2$ will depend on the specific characteristics of the data and the underlying relationship between the predictors and the response. It is not possible to determine which model will have a lower training RSS without additional information.

(c) When $\lambda = 0$, the penalty term has no impact on the sum of squares method. Therefore, the choice of the degrees of derivatives for $\hat{g}_1$ and $\hat{g}_2$ becomes irrelevant, and both curves will end up fitting the sum of squares method. The penalty term only becomes influential when $\lambda$ is non-zero, introducing regularization and potentially leading to different curve shapes. So both curves will have the same training RSS value.
