## Question 1
1. This problem involves hyperplanes in two dimensions.

(a) Sketch the hyperplane 1 + 3X1 − X2 = 0. Indicate the set of points for which 1+3X1 −X2 > 0, as well as the set of points for which 1 + 3X1 − X2 < 0.

(b) On the same plot, sketch the hyperplane −2 + X1 + 2X2 = 0. Indicate the set of points for which −2 + X1 + 2X2 > 0, as well asthesetofpointsforwhich−2+X1+2X2 <0.

### Answers

(a)

![Figure 18](/figures/Figure_18.png)

(b)

![Figure 19](/figures/Figure_19.png)

## Question 2

We have seen that in $p = 2$ dimensions, a linear decision boundary takes the form $\beta_0 +\beta_1X_1 +\beta_2X_2 = 0$. We now investigate a non-linear decision boundary.

(a) Sketch the curve

$$ (1 + X_1)^2 + (2 - X_2)^2 = 4 $$

(b) On your sketch, indicate the set of points for which

$$ (1 + X_1)^2 + (2 - X_2)^2 \gt 4 $$

as well as the set of points for which

$$ (1 + X_1)^2 + (2 - X_2)^2 \leq 4 $$

(c) Suppose that a classifier assigns an observation to the blue class if

$$ (1 + X_1)^2 + (2 - X_2)^2 \gt 4 $$

and to the red class otherwise. To what class is the observation (0, 0) classified? (−1, 1)? (2, 2)? (3, 8)?

(d) Argue that while the decision boundary in (c) is not linear in terms of $X_1$ and $X_2$, it is linear in terms of $X_1, X_1^2, X_2, \ \text{and} \ X_2^2$.

### Answers

(a) & (b)

![Figure 20](/figures/Figure_20.png)

(c)
The observation (0, 0) is classified as `Blue`.

(−1, 1) -> `Red`

(2, 2) -> `Blue`

(3, 8) -> `Blue`

(d) When expressing the decision boundary in terms of X1 and X2, a quadratic form is required. However, if we express it in terms of X1^2 and X2^2, we can treat it as a linear equation similar to polynomial features in linear regression. Although the terms may appear nonlinear, the overall formulation can be represented using linear terms.

Let 

$$ X_1^2 = a \ \text{and} \ X_2^2 = b $$

$$ \implies (1 + X_1)^2 + (2 - X_2)^2 = X_1^2 + 2 X_1 + X_2^2 - 4 X_2 + 5 $$

$$ = a + 2 X_1 + b - 4 X_2 + 5 $$


## Question 3

(a) We are given n = 7 observations in p = 2 dimensions. For each observation, there is an associated class label.

| Obs. | X1 | X2 | Y   |
|------|----|----|-----|
| 1    | 3  | 4  | Red |
| 2    | 2  | 2  | Red |
| 3    | 4  | 4  | Red |
| 4    | 1  | 4  | Red |
| 5    | 2  | 1  | Blue|
| 6    | 4  | 3  | Blue|
| 7    | 4  | 1  | Blue|

Sketch the observations.

(b) Sketch the optimal separating hyperplane, and provide the equation for this hyperplane (of the form (9.1)).

(c) Describe the classification rule for the maximal margin classifier. It should be something along the lines of “Classify to Red if $\beta_0 +\beta_1X_1 +\beta_2X_2 \gt 0$, and classify to Blue otherwise.” Provide the values for β0, β1, and β2.

(d) On your sketch, indicate the margin for the maximal margin hyperplane.

(e) Indicate the support vectors for the maximal margin classifier.

(f) Argue that a slight movement of the seventh observation would not affect the maximal margin hyperplane.

(g) Sketch a hyperplane that is not the optimal separating hyperplane, and provide the equation for this hyperplane.

(h) Draw an additional observation on the plot so that the two classes are no longer separable by a hyperplane.

### Answers

(a)

![Figure 21](/figures/Figure_21.png)

(b)

![Figure 22](/figures/Figure_22.png)

The equation of the decision boundary

$$ X_1 - X_2 - \frac{1}{2} = 0 $$

(c)
The new observations are assigned as `Blue` if the inequality 

$$ X_1 - X_2 - \frac{1}{2} > 0 $$

holds, and they are assigned as `Red` if the inequality 

$$ X_1 - X_2 - \frac{1}{2} < 0 $$

holds.

(d) We can compute the margin of the maximal margin classifiers as the distance between the support vectors and the decision boundary. This distance represents the perpendicular distance from a support vector to the decision boundary.

$$ \text{point} = x = (x_1, y_1) \ \text{and} \ \text{line} = ax + by + c $$

$$ \text{Distance} = \frac{|a*x1 + b * y1 + c|}{\sqrt{a^2 + b^2}}$$

$$ \implies \frac{|1*2 + (-1) * 1 + (-0.5)|}{\sqrt{1^2 + (-1)^2}} = 0.3536 $$

(e)

![Figure 23](/figures/Figure_23.png)

(f) Since the seventh point (4, 1) is not a support vector, it does not have any influence on the decision boundary. If we were to slightly modify or replace this point without including it in the margin, it would not have any effect on the position or shape of the decision boundary.

Recall the hinge loss function:

$$ L(X, y, \beta) = \sum_{i=1}^n \max \bigg[ 0, 1 - y_i(\beta_0 + \beta_1x_{i1} + + \beta_2x_{i2} + ... + \beta_px_{ip}) \bigg] $$

If an observation is on the correct side of the margin, we have:

$$ y_i(\beta_0 + \beta_1x_{i1} + + \beta_2x_{i2} + ... + \beta_px_{ip}) \geq 1 $$

In this case, the hinge loss function is exactly equal to zero. Therefore, if a point is on the correct side of the margin, it does not have any influence on the decision boundary.

(g) The orange line represents a non optimal seperating hyperplane for this data

$$ X_1 - X_2 - \frac{3}{4} = 0 $$

![Figure 24](/figures/Figure_24.png)

(h)

![Figure 25](/figures/Figure_25.png)