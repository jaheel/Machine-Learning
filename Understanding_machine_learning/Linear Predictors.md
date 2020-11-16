# Linear Predictors

First, we define the class of affine functions as 
$$
L_d = \{ h_{w,b}: w \in \mathbb{R}^d, b \in \mathbb{R} \}
$$
where
$$
h_{w,b}(X) = \lang {W,X} \rang +b = \bigg( \sum_{i=1}^d {w_i x_i} \bigg)+b
$$
It will be convenient also to use the notation
$$
L_d=\{ X \mapsto \lang W,X \rang +b : W \in \mathbb{R}^d, b \in \mathbb{R} \}
$$


let $W' = (b,w_1, w_2,...,w_d) \in \mathbb{R}^{d+1}$ and let $X'=(1,x_1,x_2,...,x_d) \in \mathbb{R}^{d+1}$. Therefore,
$$
h_{w,b}(X) = \lang W,X \rang +b = \lang W',X' \rang
$$


By doing this , we can omit the bias term and refer to $L_d$ as the class of homogenous linear functions of the form $h_W(X) = \lang W,X \rang$



Define $\gamma = \min_i (y_i \lang w^{*}, x_i \rang)$ and let $\bar{w} = \frac{w^{*}}{\gamma}$. Therefore, for all $i$ we have
$$
y_i \lang \bar{w},x_i \rang = \frac{1}{\gamma}y_i \lang w^*,x_i \rang \ge 1
$$
We have thus shown that there exists a vector that satisfies
$$
y_i \lang w,x_i \rang \ge 1, \space \space \forall i=1,...,m
$$


## Halfspaces

The VC dimension of the class of homogenous halfspaces in $\mathbb{R}^d$ is $d$.



## Perceptron algorithm

An iterative algorithm that constructs a sequence of vectors $w^{(1)},w^{(2)},...$ , $w^{(1)}$ is set to be the all-zeros vector.



Batch Perceptron

> input : A training set $(x_1,y_1),...,(x_m,y_m)$
>
> initialize: $w^{(1)}=(0,...,0)$
>
> ​	for t = 1,2,...
>
> ​		if $(\exist i \space s.t. \space y_i \lang w^{(t)},x_i \rang \le 0) $ then
>
> ​				$w^{(t+1)} = w^{(t)}+y_i x_i$
>
> ​		else
>
> ​				output $w^{(t)}$



## Linear Regression

A common statistical tool for modeling the relationship between some "explanatory" variables and some real valued outcome.
$$
H_{reg} = L_d=\{ x \mapsto \lang w,x \rang+b:w \in \mathbb{R}^d, b \in \mathbb{R} \}
$$


One common way is to use the squared-loss function:
$$
\ell(h,(X,y)) = (h(X)-y)^2
$$
For this loss function, the empirical risk function is called the Mean Squared Error:
$$
L_S(h) = \frac{1}{m} \sum_{i=1}^m (h(x_i)-y_i)^2
$$

### Least Squares

$$
\arg \min_w L_S(h_w) = \arg \min_m \frac{1}{m} \sum_{i=1}^m ( \lang w,x_i \rang - y_i )^2
$$

To solve the problem we calculate the gradient of the objective function and compare it to zero. That is, we need to solve
$$
\frac{2}{m} \sum_{i=1}^m ( \lang w,x_i \rang - y_i )x_i = 0
$$
We can rewrite the problem as the problem $Aw=b$ where
$$
A= \bigg( \sum_{i=1}^m x_ix_i^\top \bigg) \\
b= \sum_{i=1}^m y_ix_i
$$
If $A$ is invertible then the solution to the ERM problem is 
$$
w=A^{-1} b
$$
The case in which $A$ is not invertible requires a few standard tools from linear algebra.



### Linear Regression for Polynomial Regression Tasks

Some learning tasks call for nonlinear predictors, such as polynomial predictors.

For instance, a one dimensional polynomial function of degree $n$, that is,
$$
p(x)=a_0+a_1x+a_2x^2+...+a_nx^n
$$
where $(a_0,...,a_n)$ is a vector of coefficients of size $n+1$.



the class of one dimensional, n-degree, polynomial regression predictors, namely,
$$
H_{poly}^n = \{ x \mapsto p(x) \}
$$


To translate a polynomial regression problem to a linear regression problem, we define the mapping $\psi: \mathbb{R} \rightarrow \mathbb{R}^{n+1}$ such that $\psi(x) = (1,x,x^2,...,x^n)$. Then we have that:
$$
p(\psi(x)) = a_0+a_1x+ a_2 x^2 +...+a_n x^n = \lang \bold{a}, \psi(x) \rang
$$

## Logistic Regression

Used for classification tasks: We can interpret $h(X)$ as the probability that the label of x is 1.

the sigmoid function:
$$
\phi_{sig}(z) = \frac{1}{1+\exp(-z)}
$$


The hypothesis class is therefore:
$$
H_{sig}= \phi_{sig} \circ L_d = \{ \bold{x} \mapsto \phi_{sig}( \lang \bold{w}, \bold{x} \rang ): \bold{w} \in \mathbb{R}^d  \}
$$


use log to compute faster:
$$
\ell(h_w,(\bold{x},y)) = \log(1+\exp(-y \lang \bold{w}. \bold{x} \rang))
$$
Therefore, the ERM problem associated with logistic regression is:
$$
\arg \min_{\bold{w} \in \mathbb{R}^d} \frac{1}{m} \sum_{i=1}^m \log(1+ \exp(-y_i \lang \bold{w},\bold{x}_i \rang))
$$


The advantage of the logistic loss function is that it is a convex function with respect to $\bold{w}$; hence the ERM problem can be solved efficiently using standard methods.