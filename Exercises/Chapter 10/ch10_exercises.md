## Question 1
Consider a neural network with two hidden layers: p = 4 input units, 2 units in the first hidden layer, 3 units in the second hidden layer, and a single output.

(a) Draw a picture of the network, similar to Figures 10.1 or 10.4.

(b) Write out an expression for f(X), assuming ReLU activation functions. Be as explicit as you can!

(c) Now plug in some values for the coefficients and write out the value of f(X).

(d) How many parameters are there?

### Answers

(a)
![Figure 26](/figures/Figure_26.png)

(b)

$$ f(X) = \beta_0 + \sum_{k=1}^K\beta_k \ g(w_{k0} + \sum_{j=1}^p w_{kj} X_j) $$

If we take the activation functions as `relu` and examine the given neural network, we can explain it in two steps which are 'Forward Propagation' and 'Backward Propagation':

Recall the rectifier linear unit activation function:

$$ g(z) = (z)_+ = \begin{cases} 0 & \text{if} \ z \lt 0 \\ z & \text{otherwise} \end{cases} $$

- Step 1 - Forward Propagation

    In this step, we progress from the input layer to the output layer. At each layer, we calculate the activation values for each unit, and depending on the activation function used, we pass the obtained values to the next layers.

    In the first hidden layer, we compute:
        
    $$ A_k^{(1)} = h_k^{(1)}(X) = g \bigg(w_{k0}^{(1)} + \sum_{j=1}^p w_{kj}^{(1)} X_j \bigg) \  \text{for} \ k = 1, 2$$

    where 

    $$ X = (X_1, X_2, X_3, X_4), w^{(1)} = \begin{bmatrix} w_{11}^{(1)} & w_{12}^{(1)} \\ w_{21}^{(1)} & w_{22}^{(1)} \\ w_{31}^{(1)} & w_{32}^{(1)} \\ w_{41}^{(1)} & w_{42}^{(1)} \end{bmatrix}$$

    In the second hidden layer, instead of using input values, we take the activation values from the first hidden layer as input, and we compute:

    $$ A_k^{(2)} = h_k^{(2)}(X) = g \bigg(w_{k0}^{(2)} + \sum_{j=1}^p w_{kj}^{(2)}  A_k^{(1)}\bigg) \  \text{for} \ k = 1, 2, 3$$

    where 

    $$ A^{(1)} = (A_1^{(1)}, A_2^{(1)}), w^{(2)} = \begin{bmatrix} w_{11}^{(2)} & w_{12}^{(2)} & w_{13}^{(2)} \\ w_{21}^{(2)} & w_{22}^{(2)} & w_{23}^{(2)} \end{bmatrix}$$

    Finally, in the output layer, we compute the f function:

    $$ Z = \beta_{0} + \sum_{l=1}^{K_2}\beta_{l} A_l^{(2)} $$

    $$ Z = \beta_{0} + \beta_{1} A_1^{(2)} + \beta_{2} A_2^{(2)} + \beta_{3} A_3^{(2)} $$

    where

    $$ \beta = (\beta_1, \beta_2, \beta_3), \ A_l^{(2)} = g \bigg(w_{l0}^{(1)} + \sum_{k=1}^{K_1} w_{kj}^{(2)} A_k^{(1)} \bigg) $$

- Step 2 - Backward Propagation

    In this step, we calculate the gradients of each parameter and update their values based on these gradients and the learning rate. It is important to know that the equations for updating the parameter values depend on the specific optimization algorithm used, such as gradient descent or stochastic gradient descent. The learning rate determines the step size for each update, influencing the speed and convergence of the training process.

(c)

Suppose we initialize the parameters as follows:

Input value:

$$ X = \begin{bmatrix} 20 \\ 10 \\ -5 \\ 4 \end{bmatrix} $$

First hidden layer:

$$ W_1 = \begin{bmatrix} 2 & 1 \\ 1 & 1 \\ 3 & 4 \\ 0 & -1 \end{bmatrix}, b_1 = \begin{bmatrix} 0 \end{bmatrix} $$

Second hidden layer:

$$ W_2 = \begin{bmatrix} 1 & 0 & 2 \\ 2 & 2 & 1 \end{bmatrix}, b_2 = \begin{bmatrix} 3 \end{bmatrix} $$

Output layer:

$$ \beta = \begin{bmatrix} 2 & 3 & 1 \end{bmatrix}, b_3 = \begin{bmatrix} -5 \end{bmatrix}$$

According to these values, we can compute:

At the first hidden layer, we obtain:

$$ A^{(1)} = g(X . W_1 + b_1) = \begin{bmatrix} 35 & 6 \end{bmatrix} $$

At the second hidden layer, we obtain:

$$ A^{(2)} = g(A^{(1)} . W_2 + b_2) = \begin{bmatrix} 50 & 15 & 79 \end{bmatrix} $$

At the output layer, we have:

$$  f(X) = g(A^{(2)} . \beta + b_3) = \begin{bmatrix} 219 \end{bmatrix} $$

Here, the function $g$ denotes the activation function used at each layer which is `relu`.

(d) There are 23 total parameters

$$ (4+1) \times 2 + (2+1) \times 3 + (3+1) \times 1 = 23 $$

## Question 2
Consider the softmax function in (10.13) (see also (4.13) on page 141) for modeling multinomial probabilities.

(a) In (10.13), show that if we add a constant c to each of the $z_l$, then the probability is unchanged.

(b) In (4.13), show that if we add constants cj, j = 0,1,...,p, to each of the corresponding coefficients for each of the classes, then the predictions at any new point x are unchanged.

This shows that the softmax function is over-parametrized. However, regularization and SGD typically constrain the solutions so that this is not a problem.

### Answer

Recall that

$$ f_m(X) = Pr(Y=m|X) = \frac{e^{Z_m}}{\sum_{l=0}^9e^{Z_l}} \tag{10.13} $$

and 

$$ Pr(Y=k|X=x) = \frac{e^{\beta_{k0} + \beta_{k1}X_1 + ... + \beta_{kp}X_p}}{\sum_{l=1}^{K} e^{\beta_{l0} + \beta_{l1}X_1 + ... + \beta_{lp}X_p}} \tag{4.13} $$

(a) If we add a constant c to each of the $z_l$. we get

$$ Pr(Y=m|X) = \frac{e^{Z_m + c}}{\sum_{l=0}^9e^{Z_l + c}}  = \frac{e^ce^{Z_m}}{e^c\sum_{l=0}^9e^{Z_l}} = \frac{e^{Z_m}}{\sum_{l=0}^9e^{Z_l}} $$

(b) 

$$ Pr(Y=k|X=x) = \frac{e^{(\beta_{k0} + c_0) + (\beta_{k1} + c_1)X_1 + ... + (\beta_{kp} + c_p) X_p}}{\sum_{l=1}^{K} e^{(\beta_{l0} + c_0) + (\beta_{l1} + c_1)X_1 + ... + (\beta_{lp} + c_p) X_p}} $$

$$ \implies \frac{Pr(Y=k|X=x)}{Pr(Y=j|X=x)} = \frac{\frac{e^{(\beta_{k0} + c_0) + (\beta_{k1} + c_1)X_1 + ... + (\beta_{kp} + c_p) X_p}}{\sum_{l=1}^{K} e^{(\beta_{l0} + c_0) + (\beta_{l1} + c_1)X_1 + ... + (\beta_{lp} + c_p) X_p}}}{\frac{e^{(\beta_{j0} + c_0) + (\beta_{j1} + c_1)X_1 + ... + (\beta_{jp} + c_p) X_p}}{\sum_{l=1}^{K} e^{(\beta_{l0} + c_0) + (\beta_{l1} + c_1)X_1 + ... + (\beta_{lp} + c_p) X_p}}} = \frac{e^{(\beta_{k0} + c_0) + (\beta_{k1} + c_1)X_1 + ... + (\beta_{kp} + c_p) X_p}}{e^{(\beta_{j0} + c_0) + (\beta_{j1} + c_1)X_1 + ... + (\beta_{jp} + c_p) X_p}} $$

Simplifying this expression:

$$ \frac{e^{c_0 + c_1X_1 + c_2X_2 + \dots + c_pX_p}e^{e^{\beta_{k0} + \beta_{k1}X_1 + ... + \beta_{kp}X_p}}}{e^{c_0 + c_1X_1 + c_2X_2 + \dots + c_pX_p}e^{e^{\beta_{j0} + \beta_{j1}X_1 + ... + \beta_{jp}X_p}}} $$

Notice that the constants $c_j$ cancel out in the numerator and denominator, resulting in the same ratio as in the original expression. Therefore, adding constants to each of the corresponding coefficients for each of the classes does not change the predictions at any new point x.

## Question 3
Show that the negative multinomial log-likelihood (10.14) is equivalent to the negative log of the likelihood expression (4.5) when there are M = 2 classes.

### Answer
Using equation (10.14):

$$ -\sum_{i=1}^n \sum_{m=0}^M y_{im}\log(f_m(x_i)) \tag{10.14} $$

And equation (4.5):

$$ l(\beta_0, \beta_1) = \prod_{i:y_i=1}p(x_i) \prod_{i':y_{i'}=0} (1-p(x_{i'})) \tag{4.5} $$

For the two-class case, equation (10.14) becomes:

$$ -\sum_{i=1}^n \bigg( y_{i1}\log(f_1(x_i)) + y_{i2}\log(f_2(x_i))\bigg) $$

Taking the negative logarithm of the likelihood expression (4.5):

$$ - \log \bigg(\prod_{i:y_i=1}p(x_i) \prod_{i':y_{i'}=0} (1-p(x_{i'})) \bigg) = - \bigg(\sum_{i:y_i=1}\log(p(x_i)) + \sum_{i':y_{i'}=0} \log(1-p(x_{i'}))\bigg) $$

Expressing the probability values, such as $p(x_i)$, in terms of the prediction result from a logistic regression function:

$$ - \bigg(\sum_{i:y_i=1}\log(f_1(x_i)) + \sum_{i':y_{i'}=0} \log(f_2(x_i))\bigg) $$

By rearranging the terms and considering the target values $y_i$ as conditions in the summation:

$$ - \bigg(\sum_{i=1}y_i\log(f_1(x_i)) + \sum_{i=1} y_{i'}\log(f_2(x_i))\bigg) = - \sum_{i=1}\bigg(y_i\log(f_1(x_i)) +  y_{i'}\log(f_2(x_i))\bigg)$$

Hence,
$$ \implies -\sum_{i=1}^n \bigg( y_{i1}\log(f_1(x_i)) + y_{i2}\log(f_2(x_i))\bigg) = - \sum_{i=1}\bigg(y_i\log(f_1(x_i)) +  y_{i'}\log(f_2(x_i))\bigg)$$

## Question 4
Consider a CNN that takes in $32 \times 32$ grayscale images and has a single convolution layer with three $5 \times 5$ convolution filters (without boundary padding).

(a) Draw a sketch of the input and first hidden layer similar to Figure 10.8.

(b) How many parameters are in this model?

(c) Explain how this model can be thought of as an ordinary feed-forward neural network with the individual pixels as inputs, and with constraints on the weights in the hidden units. What are the constraints?

(d) If there were no constraints, then how many weights would there be in the ordinary feed-forward neural network in (c)?

## Answer

(a)

![Figure 27](/figures/Figure_27.png)

(b)

((`shape of width of the filter` * `shape of height of the filter` * `num of filters in the previous layer + 1`) * number of filter)

$$ (5 \times 5 \times (0+1)) * \times 3 = 78 $$

(c) Each pixel in the grayscale input image represents an individual input feature. To obtain activations in the first hidden layer of a CNN, we apply convolution filters to these pixels, which serve as the input values for the subsequent layers. Therefore, a CNN can be regarded as an ordinary feed-forward neural network.

However, CNNs impose constraints on the weights due to the convolutional filters. These weights remain constant and are shared across different spatial locations in the input. This weight sharing constraint reduces the number of parameters and allows the network to capture local patterns or features in the input. Consequently, CNNs are capable of extracting spatially invariant features from images.

(d) In a feed-forward neural network without constraints, each hidden unit would have its own set of weights for every input feature. This means that each hidden unit would be connected to every individual pixel in the $32 \times 32$ grayscale image, requiring a separate weight for each connection.

The number of weights in the hidden units can be calculated as the product of the number of hidden units and the number of input features:

Number of weights = Number of hidden units * Number of input features

In this case, it would be: 3 * (32 x 32) = 3072 weights.

## Question 5
In Table 10.2 on page 433, we see that the ordering of the three methods with respect to mean absolute error is different from the ordering with respect to test set R2. How can this be?

| Model              | Parameters | Mean Abs. Error | Test Set R2 |
|--------------------|------------|-----------------|-------------|
| Linear Regression  | 20         | 254.7           | 0.56        |
| Lasso              | 12         | 252.3           | 0.51        |
| Neural Network     | 1409       | 257.4           | 0.54        |

We can observe that the linear regression model, with its 20 parameters, provides a statistically reliable way to capture the variance in the test data. However, when we apply the lasso regularization to this model, some of the most important parameters are likely to be removed due to the nature of the lasso formulation. On the other hand, the neural network appears to be over-parametrized for this particular dataset, as it fails to effectively capture most of the variance in the test data.