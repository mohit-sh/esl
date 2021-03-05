# 3.2: Linear Regression Models and Least Squares
The Linear Model for regression, in its simplest form, assumes a linear relationship between regression function $\mathbb{E}\left[Y \mid X \right]$ and model parameters $\beta_0, \ldots, \beta_p$ in the form: 

$$
\begin{aligned}
    \mathbb{E} \left[ Y \mid X \right]  &= f(X) \\ 
                                        &=  \beta_0 + \sum_{j=1}^{p} \beta_j X_j
\end{aligned}
$$

We can collectively represent all the parameters $\beta_0, \ldots, \beta_p$ as a vector $\bm{\beta}$.
## Least Squares Estimator for $\bm{\beta}$

Given training data of observations and their corresponding responses $\{ \left( x_i, y_i \right)\}_{i=1}^{N}$, where each observation $x_i \in \mathbb{R}^p$  we can use the method of *Least Squares* to estimate the parameter vector $\bm{\beta} = \left( \beta_0, \ldots, \beta_p\right)^{\mathsf{T}}$ by minimizing the *Residual Sum of Squares* $(RSS)$
$$
\begin{aligned}
RSS\left(\bm{\beta} \right)  &= \sum_{i=1}^{N} \left(y_i - f(x_i) \right)^2
\end{aligned}
$$

For brevity sake, we introduce some vector notations: $\bm{X} \in \mathbb{R}^{N \times p}$ is the data-matrix, $\bm{y} \in \mathbb{R}^{N}$ is the vector of responses. Unless otherwise mentioned, $\bm{X}$ is assumed to be full-column rank.

With these two entities introduced, we can rewrite the $RSS(\beta)$ as follows:

$$
RSS(\bm{\beta}) = (\bm{y} - \bm{X}\bm{\beta})^{\mathsf{T}}(\bm{y} - \bm{X}\bm{\beta})
$$

$$
% How do we know that RSS(\beta) has a unique solution?
$$

To find $\bm{\beta}$ that minimizes $RSS{\bm{\beta}}$, set $\operatorname{\nabla_{\bm{\beta}}} RSS(\bm{\beta}) = 0$.

$$
\begin{aligned}
    \operatorname{\nabla_{\bm{\beta}}} RSS(\bm{\beta}) &= \operatorname{\nabla_{\bm{\beta}}} \big(\bm{y}^{\mathsf{T}}\bm{y} -2 \bm{\beta}^{\mathsf{T}} \bm{X}^{\mathsf{T}}\bm{y} + \bm{\beta}^{\mathsf{T}}\bm{X}^{\mathsf{T}}\bm{X}\bm{\beta} \big) \\
                                        &= -2 \bm{X}^{\mathsf{T}}\bm{y} + 2 \bm{X}^{\mathsf{T}}\bm{X} \bm{\beta} \\
\end{aligned}
$$
Setting $\operatorname{\nabla_{\bm{\beta}}} RSS(\bm{\beta}) = 0$ gives us following:

$$
\begin{aligned}
                     & -2 \bm{X}^{\mathsf{T}}\bm{y} + 2 \bm{X}^{\mathsf{T}}\bm{X} \bm{\beta} = 0 \\ 
    \Rightarrow \quad &\bm{\hat{\beta}} = (\bm{X}^{\mathsf{T}}\bm{X})^{-1}\bm{X}^{\mathsf{T}}\bm{y}
\end{aligned}
$$
These are usually called *normal equations*. Note that the invertibility of $(\bm{X}^{\mathsf{T}}\bm{X})$ follows from the assumption that $\bm{X}$ is full-column rank. In fact, $\bm{X}$ being full-column rank ensures that $(\bm{X}^{\mathsf{T}}\bm{X})$ is *Positive Definite (PD)*. It's not that hard to see -- for any non-zero $\bm{\alpha} \in \mathbb{R}^p$, $\bm{\alpha}^{\mathsf{T}}(\bm{X}^{\mathsf{T}}\bm{X})\bm{\alpha} = \big(\bm{X}\bm{\alpha}\big)^{\mathsf{T}}\big(\bm{X}\bm{\alpha}\big) \gt 0$ because $\bm{X}$ is full-column rank. 

In order to show that normal-equations indeed gives a minima, we now compute the Hessian $\operatorname{\nabla_{\bm{\beta}}^2} RSS(\bm{\beta})$
$$
    \begin{aligned}
        \operatorname{\nabla_{\bm{\beta}}^2} RSS(\bm{\beta}) &= 2 (\bm{X}^{\mathsf{T}}\bm{X})
    \end{aligned}
$$
which is a positive-definite matrix.
$$
% Add second-order condition for minimization.
$$

## Sampling Properties of Least Squares Estimator Under Minimal Distributional Assumptions

In order to understand the sampling properties of Least-squares estimator $\bm{\hat{\beta}}$, we need to expand the set of assumptions we impose on our linear model. In this section, we assume the following of our linear model:

1. $x_i$ are fixed, and $y_i$ are uncorrelated with constant variance $\sigma^2$.
2. The true model is $\operatorname{\mathbb{E}}\left[Y \mid X\right] = \beta_0 + \sum_{j=1}^n X_j \beta_j$

Under these assumptions, the following hold: 

**Proposition** Under the assumptions stated above, $\operatorname{\text{Var}}\big(\bm{\hat{\beta}}\big) = \sigma^2 \big(\bm{X}^{\mathsf{T}}\bm{X}\big)^{-1}$  
**Proof**
We know that, for a random variable $\bm{x} \in \mathbb{R}^n$ with $\operatorname{\text{Var}}\big(\bm{x}\big) = \bm{\Sigma}$, the variance of a linear transformation $\bm{y} = \bm{A}\bm{x}$ is given by $\operatorname{\text{Var}}\big(\bm{y}\big) = \bm{A\Sigma A}^{\mathsf{T}}$ (TODO: Add link to the section in ../mathematical_background.md)
So, 
$$
    \begin{aligned}
    \operatorname{\text{Var}}\big(\bm{\hat{\beta}}\big) 
        &= \big(\bm{X}^{\mathsf{T}}\bm{X}\big)^{-1}\bm{X}^{\mathsf{T}} \operatorname{\text{Var}}\big(\bm{y}\big) \bm{X}\big( \bm{X}^{\mathsf{T}}\bm{X}\big)^{-1} \\
        &= \big(\bm{X}^{\mathsf{T}}\bm{X}\big)^{-1}\bm{X}^{\mathsf{T}} \sigma^2 \bm{I} \bm{X}\big( \bm{X}^{\mathsf{T}}\bm{X}\big)^{-1} \\
        &= \sigma^2 \big(\bm{X}^{\mathsf{T}}\bm{X}\big)^{-1}\bm{X}^{\mathsf{T}} \bm{X}\big( \bm{X}^{\mathsf{T}}\bm{X}\big)^{-1} \\
        &= \sigma^2 \big(\bm{X}^{\mathsf{T}}\bm{X}\big)^{-1}\\
    \end{aligned}
$$

### Estimator for $\sigma^2$

One estimator for $\sigma^2$ is the following (TODO: Add more context later)
$$
\begin{aligned}
    s^2 &= \dfrac{1}{n - p -1 } \sum_{i=1}^n \big(y_i - \bm{x}_i^{\mathsf{T}}\bm{\hat{\beta}}\big)^2 \\
        &= \dfrac{1}{n - p -1 } \big(\bm{y} - \bm{X\hat{\beta}} \big)^{\mathsf{T}} \big(\bm{y} - \bm{X\hat{\beta}}\big) \\
        &= \dfrac{SSE}{n - p -1 }  \\
        &= \dfrac{1}{n - p -1 } \big(\bm{yy}^{\mathsf{T}} - \bm{y}^{\mathsf{T}}\bm{X\hat{\beta}} \big)
\end{aligned}
$$

Now, we show that $s^2$ defined above is an unbiased estimator for $\sigma^2$
$$
\begin{aligned}
\operatorname{\mathbb{E}} \left[s^2\right] 
    &= \operatorname{\mathbb{E}} \left[\big(\bm{y}^{\mathsf{T}}\bm{y} - \bm{y}^{\mathsf{T}}\bm{X\hat{\beta}} \big)\right] \\
\end{aligned}
$$
We know how to calculate the expected value of a quadratic form: $\operatorname{\mathbb{E}} \left[\bm{y}^{\mathsf{T}}\bm{Ay}\right] = \bm{\mu}^{\mathsf{T}}\bm{A\mu} + \bm{A\Sigma}$, where $\bm{\mu} = \operatorname{\mathbb{E}} \left[\bm{y}\right]$, and $\bm{\Sigma} = \operatorname{\text{Cov}}\big(\bm{y}\big)$. So, we represent $s^2$ as a quadratic form. With that, we have
(TODO: Add link to the proof to the result) 
$$
\begin{aligned}
\operatorname{\mathbb{E}} \left[SSE\right] 
    &= \operatorname{\mathbb{E}} \left[\Big(\bm{y}^{\mathsf{T}}\bm{y} - \bm{y}^{\mathsf{T}}\bm{X\big(\bm{X}^{\mathsf{T}}\bm{X}\big)^{-1}\bm{X}^{\mathsf{T}}\bm{y}} \Big)\right] \\
    &= \operatorname{\mathbb{E}} \left[\bm{y}^{\mathsf{T}}\Big(\bm{I} -\bm{X\big(\bm{X}^{\mathsf{T}}\bm{X}\big)^{-1}\bm{X}^{\mathsf{T}}} \Big)\bm{y}\right] \\
    &= \operatorname{\mathbb{E}} \left[\bm{\beta}^{\mathsf{T}}\bm{X}^{\mathsf{T}}\Big( \bm{I} -\bm{X\big(\bm{X}^{\mathsf{T}}\bm{X}\big)^{-1}\bm{X}^{\mathsf{T}}}\Big)\bm{X\beta} + \operatorname{\text{tr}}\Big(\sigma^2 \big(\bm{I} -\bm{X\big(\bm{X}^{\mathsf{T}}\bm{X}\big)^{-1}\bm{X}^{\mathsf{T}}}\big) \Big)\right] \\
    &= \operatorname{\mathbb{E}} \left[\bm{\beta}^{\mathsf{T}}\bm{X}^{\mathsf{T}}\bm{X\beta}\right] - \operatorname{\mathbb{E}} \left[ \bm{\beta}^{\mathsf{T}}\bm{X}^{\mathsf{T}}\bm{X\big(\bm{X}^{\mathsf{T}}\bm{X}\big)^{-1}\bm{X}^{\mathsf{T}}}\bm{X\beta}\right] + \sigma^2\operatorname{\text{tr}}\big(\bm{I_n}\big) - \sigma^2 \operatorname{\text{tr}}\Big(\bm{X} \big(\bm{X} ^{\mathsf{T}}\bm{X}\big)^{-1}\bm{X}^{\mathsf{T}}\Big) \\
    &= \operatorname{\mathbb{E}} \left[\bm{\beta}^{\mathsf{T}}\bm{X}^{\mathsf{T}}\bm{X\beta}\right] -  \operatorname{\mathbb{E}} \left[\bm{\beta}^{\mathsf{T}}\bm{X}^{\mathsf{T}}\bm{X\beta}\right] + \sigma^2 n - \sigma^2\operatorname{\text{tr}}\Big(\big(\bm{X}^{\mathsf{T}}\bm{X}\big)^{-1}\big(\bm{X}^{\mathsf{T}}\bm{X}\big)\Big) \\
    &= \operatorname{\mathbb{E}} \left[\bm{\beta}^{\mathsf{T}}\bm{X}^{\mathsf{T}}\bm{X\beta}\right] -  \operatorname{\mathbb{E}} \left[\bm{\beta}^{\mathsf{T}}\bm{X}^{\mathsf{T}}\bm{X\beta}\right] + \sigma^2 n - \sigma^2\operatorname{\text{tr}}\big(\bm{I}_{p+1}\big) \\
    &= \operatorname{\mathbb{E}} \left[\bm{\beta}^{\mathsf{T}}\bm{X}^{\mathsf{T}}\bm{X\beta}\right] -  \operatorname{\mathbb{E}} \left[\bm{\beta}^{\mathsf{T}}\bm{X}^{\mathsf{T}}\bm{X\beta}\right] + \sigma^2 n - \sigma^2(p+1) \\
    &= \sigma^2(n - p - 1)
\end{aligned}
$$
Therefor, 
$$
\operatorname{\mathbb{E}} \left[s^2\right] = \sigma^2(n - p -1) / (n-p-1) = \sigma^2
$$
So, $s^2$ is indeed an unbiased estimator for $\sigma^2$. The denominator of $s^2$ is set to $n - p - 1$ to achieve unbiasedness.
