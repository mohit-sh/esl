# Mathematical Background
## Tricks to identify equivalent matrix expressions

1. **Quadratic Form** : 
$$
\bm{y}^{\mathsf{T}}\bm{A}\bm{y} = \sum_{i}^n\sum_{j=1}^nA_{ij}y_iy_j
$$

2. **Trace of Product of Matrices** ($\bm{A} \in \mathbb{R}^{n \times p}, \bm{B} \in \mathbb{R}^{p \times n}$)
$$
    \operatorname{\text{tr}}\big(\bm{AB}\big) = \sum_{i=1}^n\sum_{j=1}^pA_{ij}B_{ji}
$$

## Properties of $\operatorname{\text{tr}}\big(. \big)$ operator.
1. $\operatorname{\text{tr}}\big( \bm{AB}\big) = \operatorname{\text{tr}}\big(\bm{BA}\big)$
$$
    \begin{aligned}
        \operatorname{\text{tr}}\big(\bm{AB}\big) 
            &= \sum_{i=1}^n \sum_{j=1}^n A_{ij}B_{ij} \\
            &= \sum_{j=1}^n \sum_{i=1}^n B_{ji}A_{ij} \\
            &= \operatorname{\text{tr}}\big(\bm{BA}\big)
    \end{aligned}
$$
## Definition/Notation for Gradient, Jacobians, and Hessians (and their relationship)

**Gradient** For a function $f: \mathbb{R}^{n} \to \mathbb{R}$, gradient of $f$ with respect to $\bm{x}$, denoted as $\operatorname{\nabla_{\bm{x}}} f(\bm{x})$, is a column vector of partial derivatives $\dfrac{\partial f}{\partial x_i}$
$$
\operatorname{\nabla_{\bm{x}}} f(\bm{x}) = 
    \begin{bmatrix}
        \dfrac{\partial f}{\partial x_1} \\
        \vdots \\
        \dfrac{\partial f}{\partial x_n}
    \end{bmatrix}
$$

**Jacobian** For a function $f : \mathbb{R}^n \to \mathbb{R}^m$, Jacobian of $f$ with respect to $\bm{x}$, denotes as $\operatorname{\mathbb{J}}\big(f(\bm{x})\big)$ is a collection of partial derivaties of components of $f$, with respect to components of $x$, arranged in a matrix.

$$
\operatorname{\mathbb{J}}\big(f(\bm{x})\big) =
    \begin{bmatrix}
        \operatorname{\nabla_{\bm{x}}} f_1^{\mathsf{T}} \\
        \vdots \\
        \operatorname{\nabla_{\bm{x}}} f_m^{\mathsf{T}} \\
    \end{bmatrix} = 
    \begin{bmatrix}
        \dfrac{\partial f_1}{\partial x_1} & \cdots & \dfrac{\partial f_1}{\partial x_n} \\
        \vdots & \ddots & \vdots \\
        \dfrac{\partial f_m}{\partial x_1} & \cdots & \dfrac{\partial f_m}{\partial x_n} \\
    \end{bmatrix}
$$

**Hessian** For a function $f : \mathbb{R}^n \to \mathbb{R}$, Hessian of $f$ with respect to $x$, denoted as $\operatorname{\nabla_{\bm{x}}^2}f(\bm{x})$, is a collection of second-order partial derivatives of $f$ with respect to components of $\bm{x}$, arranged in a matrix.

$$
\operatorname{\nabla_{\bm{x}}^2}f(\bm{x}) = \operatorname{\mathbb{J}}\big(\operatorname{\nabla_{\bm{x}}}f(\bm{x})\big)^{\mathsf{T}}
$$

$$
% still need some algebraic rules to quickly compute Gradients/Hessians of functions that frequently show up in Statistics/Machine Learning.
$$

## Quadratic Forms (Completing the squares)
**Proposition 1** For any vector $\bm{x}, \bm{b} \in \mathbb{R}^d$ and a symmetric invertible matrix $\bm{M} \in \mathbb{R}^{d\times d}$, we have

$$
\bm{x}^{\mathsf{T}}\bm{M}\bm{x} - 2\bm{b}^{\mathsf{T}}\bm{x} = (\bm{x} - \bm{M}^{-1}\bm{b})^{\mathsf{T}}\bm{M}(\bm{x} - \bm{M}^{-1}\bm{b}) - \bm{b}^{\mathsf{T}}\bm{M}^{-1}\bm{b}
$$

**Proof** On expanding the RHS, we get

$$
\begin{aligned}
(\bm{x} - \bm{M}^{-1}\bm{b})^{\mathsf{T}}M(\bm{x} - \bm{M}^{-1}\bm{b}) - \bm{b}^{\mathsf{T}}\bm{M}^{-1}\bm{b} &= (\bm{x}^{T} - \bm{b}^{\mathsf{T}}\bm{M}^{-1})\bm{M}(\bm{x} - \bm{M}^{-1}\bm{b}) - \bm{b}^{\mathsf{T}}\bm{M}^{-1}\bm{b} \\
&= \bm{x}^{\mathsf{T}}\bm{M}\bm{x} - 2 \bm{b}^{\mathsf{T}}\bm{x} + \bm{b}^{\mathsf{T}} \bm{M}^{-1}\bm{b} - \bm{b}^{\mathsf{T}} \bm{M}^{-1}\bm{b} \\
&= \bm{x}^{\mathsf{T}}\bm{M}\bm{x} - 2 \bm{b}^{\mathsf{T}}\bm{x}
\end{aligned}
$$
More interesting is to come up with the expression on RHS. Here's how you can do that:

Consider this generic form for the RHS (Pause and think why this makes sense!)

$$
 \bm{x}^{\mathsf{T}}\bm{M}\bm{x} - 2\bm{b}^{\mathsf{T}}\bm{x} = (\bm{x} - \bm{u})^{\mathsf{T}}\bm{M}(\bm{x} - \bm{u}) + \bm{v}
$$

Expanding the RHS

$$
\begin{aligned}
\bm{x}^{\mathsf{T}}\bm{M}\bm{x} - 2\bm{b}^{\mathsf{T}}\bm{x} 
    &= (\bm{x} - \bm{u})^{\mathsf{T}}\bm{M}(\bm{x} - \bm{u}) + \bm{v} \\
    &= \bm{x}^{\mathsf{T}}\bm{M}\bm{x} -2 \bm{u}^{\mathsf{T}}\bm{x} + \bm{u}^{\mathsf{T}}\bm{M}\bm{u} + \bm{v}
\end{aligned}
$$

Comparing terms of similar degrees on LHS and RHS, we can see

$$
\begin{aligned}
\bm{u} &= \bm{b} \\
\bm{v} &= - \bm{u}^{\mathsf{T}}\bm{M}\bm{u} = - \bm{b}^{\mathsf{T}}\bm{M}\bm{b}
\end{aligned}
$$ 

**Proposition 2** Sum of two quadratic forms $f(\bm{x})$ 

$$
f(\bm{x}) = (\bm{x} - \bm{\mu})^{\mathsf{T}}\bm{\Sigma}^{-1}(\bm{x} - \bm{\mu}) + (\bm{x} - \bm{\theta})^{\mathsf{T}}\bm{V}^{-1}(\bm{x} - \bm{\theta})
$$
can be expressed in standard form as follows

$$
f({\bm{x}}) = (\bm{x} - \bm{M}^{-1}\bm{b})^{\mathsf{T}}\bm{M}(\bm{x} - \bm{M}^{-1}\bm{b}) + m 
$$
where

$$
    \begin{aligned}
        \bm{M}  &= \bm{\Sigma}^{-1} + \bm{V}^{-1} \\
        \bm{b}  &= \bm{\Sigma}^{-1}\bm{\mu} + \bm{V}^{-1}\bm{\theta} \\
        m   &=  \bm{\mu}^{\mathsf{T}}\bm{\Sigma}^{-1}\bm{\mu} + \bm{\theta}^{\mathsf{T}}\bm{V}^{-1}\mathsf{\theta} - \bm{b}^{\mathsf{T}}\bm{M}^{-1}\bm{b} \\
    \end{aligned}
$$
Note that we are assuming the invertibility of $\bm{M}$.

**Proof** Upon expansion, we can write $f(\bm{x})$ as follows

$$
\begin{aligned}
    f({\bm{x}})   &= (\bm{x} - \bm{\mu})^{\mathsf{T}}\bm{\Sigma}^{-1}(\bm{x} - \bm{\mu}) + (\bm{x} - \bm{\theta})^{\mathsf{T}}\bm{V}^{-1}(\bm{x} - \bm{\theta}) \\
                &= \bm{x}^{\mathsf{T}}\bm{\Sigma}^{-1}\bm{x} + \bm{x}^{\mathsf{T}}\bm{V}^{-1}\bm{x} -2 \bm{\mu}^{\mathsf{T}}\bm{\Sigma}^{-1}\bm{x} - 2\bm{\theta}^{\mathsf{T}}\bm{V}^{-1}\bm{x} + \bm{\mu}^{\mathsf{T}}\bm{\Sigma}^{-1}\bm{\mu} + \bm{\theta}^{\mathsf{T}}\bm{V}^{-1}\mathsf{\theta} \\
                &= \bm{x}^{\mathsf{T}}(\bm{\Sigma}^{-1} + \bm{V}^{-1})\bm{x} - 2 (\bm{\Sigma}^{-1}\bm{\mu} + \bm{V}^{-1}\bm{\theta})^{\mathsf{T}}\bm{x} + \bm{\mu}^{\mathsf{T}}\bm{\Sigma}^{-1}\bm{\mu} + \bm{\theta}^{\mathsf{T}}\bm{V}^{-1}\mathsf{\theta} \\
                &= \bm{x}^{\mathsf{T}}\bm{M}\bm{x} - 2 \bm{b}^{\mathsf{T}}\bm{x} + \bm{\mu}^{\mathsf{T}}\bm{\Sigma}^{-1}\bm{\mu} + \bm{\theta}^{\mathsf{T}}\bm{V}^{-1}\mathsf{\theta} \\
                &= (\bm{x} - \bm{M}^{-1}\bm{b})^{\mathsf{T}}\bm{M}(\bm{x} - \bm{M}^{-1}\bm{b}) + m
\end{aligned}
$$
We used Proposition 1 in the last step.

## Derivatives in Higher Dimensions
### Element-wise calculations
In all these examples, we assume $\bm{x} \in \mathbb{R}^n, \bm{A} \in \mathbb{R}^{n \times n}$.

$$
    % Nabla should be an operator! Proper spacing for the argument wouldn't hurt. 
    % FIX: \operatorname*{\nabla} 
$$

1. $\operatorname{\nabla_{\bm{x}}}\bm{x}^{\mathsf{T}}\bm{b}$ 
    $$
        \begin{aligned}
            \operatorname{\nabla_{\bm{x}}}\bm{x}^{\mathsf{T}}\bm{b} 
                    &= \operatorname{\nabla_{\bm{x}}} \big(\sum_{i=1}^n x_i b_i\big) \\
                    &= \begin{bmatrix}
                            \dfrac{\partial}{\operatorname{\partial}{x_1}} x_1 b_1 \\
                            \vdots \\
                            \dfrac{\partial}{\operatorname{\partial}{x_n}} x_n b_n \\
                       \end{bmatrix} \\
                       &= \bm{b}
        \end{aligned}
    $$

2. $\operatorname*{\nabla_{\bm{x}}} \bm{x}^{\mathsf{T}}\bm{A}\bm{x}$
    $$
    \begin{aligned} 
        \operatorname*{\nabla_{\bm{x}}} \bm{x}^{\mathsf{T}}\bm{A}\bm{x} 
            &= \nabla_{x} \Big( \sum_{i=1}^{n} \sum_{j=1}^{n} x_i x_j A_{ij}\Big) \\
            &=  \begin{bmatrix}
                    \dfrac{\operatorname{\partial}}{ \operatorname{\partial} x_1} \Big( \sum_{i=1}^{n} \sum_{j=1}^{n} x_i x_j A_{ij}\Big) \\ 
                    \vdots\\
                    \dfrac{\operatorname{\partial}}{ \operatorname{\partial} x_n} \Big( \sum_{i=1}^{n} \sum_{j=1}^{n} x_i x_j A_{ij}\Big) \\ 
                \end{bmatrix} \\
    \end{aligned}
    $$

    The $k^{th}$ element of the gradient can be computed as follows:
    $$
    \begin{aligned}
        \dfrac{\operatorname{\partial}}{ \operatorname{\partial} x_k} \Big( \sum_{i=1}^{n} \sum_{j=1}^{n} x_i x_j A_{ij}\Big) 
            &= \dfrac{\operatorname{\partial}}{ \operatorname{\partial} x_k} \Big( \sum_{i=1; i \neq k}^{n} \sum_{j=1; j \neq k}^n x_i x_j A_{ij} + x_k^2 A_{kk}  + \sum_{j=1; j \neq k}^n x_k x_j A_{kj} + \sum_{i=1; i \neq k}^n x_i x_k A_{ik}\Big) \\
            &= 2 x_k A_{kk} + \sum_{j=1; j \neq k}^n x_j A_{kj} + \sum_{i=1; i \neq k}^n x_i A_{ik} \\
            &= \sum_{j=1}^n x_j A_{kj} + \sum_{i=1}^n x_i A_{ik}
    \end{aligned}
    $$

    Now the gradient $\operatorname*{\nabla_{\bm{x}}} \bm{x}^{\mathsf{T}}\bm{A}\bm{x}$ can be simplified.

    $$
    \begin{aligned}
    \operatorname*{\nabla_{\bm{x}}} \bm{x}^{\mathsf{T}}\bm{A}\bm{x} 
            &=  \begin{bmatrix}
                    \sum_{j=1}^n x_j A_{1j} + \sum_{i=1}^n x_i A_{i1}\\ 
                    \vdots\\
                    \sum_{j=1}^n x_j A_{nj} + \sum_{i=1}^n x_i A_{in} \\ 
                \end{bmatrix} \\
            &= \begin{bmatrix}
                    \sum_{j=1}^n x_j A_{1j}\\ 
                    \vdots\\
                    \sum_{j=1}^n x_j A_{nj}\\ 
                \end{bmatrix} + 
                \begin{bmatrix}
                    \sum_{i=1}^n x_i A_{i1}\\ 
                    \vdots\\
                    \sum_{i=1}^n x_i A_{in} \\ 
                \end{bmatrix} \\
            &= \bm{A}\bm{x} + \bm{A}^{\mathsf{T}} \bm{x} \\
            &= \big( \bm{A} + \bm{A}^{\mathsf{T}}\big) \bm{x}

    \end{aligned}
    $$

2. $\operatorname{\nabla_{\bm{x}}^2} \bm{x}^{\mathsf{T}}\bm{A}\bm{x}$
    $$
    % Write down the derivation in terms of element-wise derivatives.
    % TODO: Figure out a way to get Gradients and Hessians without doing element-wise operations.
    % Understand the Jacobians of common functions and then you can compose the gradient and jacobian operators to get hessian operators.
    \operatorname{\nabla_{\bm{x}}^2} \bm{x}^{\mathsf{T}}\bm{A}\bm{x} = (\bm{A} + \bm{A}^{\mathsf{T}})
    $$
### Faster Gradient & Hessian computations

## Mean and Variance of Linear Functions of Random Variables
(This section mostly follows the section 3.6 of *LMS, Rencher*, including the notation)

$\bm{y} \in \mathbb{R}^p$ is a random vector.

Covariance matrix is defined as follows:
$$
\begin{aligned}
\operatorname{\text{Cov}}\big(\bm{y}\big) 
        &= \operatorname{\mathbb{E}} \left[\big(\bm{y} - \operatorname{\mathbb{E}} \left[\bm{y}\right]\big)\big( \bm{y} - \operatorname{\mathbb{E}} \left[\bm{y}\right]\big)^{\mathsf{T}}\right] \\
        &= \operatorname{\mathbb{E}} \left[\bm{y}\bm{y}^{\mathsf{T}} - \operatorname{\mathbb{E}} \left[\bm{y}\right]\operatorname{\mathbb{E}} \left[\bm{y}\right]^{\mathsf{T}}\right]
\end{aligned}
$$

**Theorem 3.6a** If $\bm{a}$ is a $p \times 1$ vector of constants and $\bm{y}$ is a $p \times 1$ random vector with mean $\bm{\mu}$, then

$$
    \operatorname{\mathbb{E}\left[\bm{a}^{\mathsf{T}}\bm{y}\right]} = \bm{a}^{\mathsf{T}} \bm{\mu}
$$

**Proof**

Consider a matrix $\bm{A} \in \mathbb{R}^{k \times p}$ of constants with $k \leq p$ such that it's full row-rank (all rows of $\bm{A}$ are linearly independent.  

**Theorem 3.6b** Suppose $\bm{y}$ is a random vector and $\bm{X}$  is a random matrix, $\bm{a}, \bm{b}$ are vectors of constants, and $\bm{A}, \bm{B}$ are matrices of constants. Then assuming vectors and matrices in each product are conformal, we have the following expected values:  
1. $\operatorname{\mathbb{E}} \left[ \bm{A}\bm{y} \right] = \bm{A} \operatorname{\mathbb{E}} \left[\bm{y}\right]$ 
2. $\operatorname{\mathbb{E}}\left[ \bm{a}^{\mathsf{T}} \bm{X} \bm{b}\right] = \bm{a}^{\mathsf{T}} \operatorname{\mathbb{E}} \left[\bm{X}\right]\bm{b}$
3. $\operatorname{\mathbb{E}} \left[\bm{A}\bm{X}\bm{B}\right] = \bm{A}\operatorname{\mathbb{E}}\left[\bm{X}\right] \bm{B}$

**Proof**

**Theorem 3.6c** If $\bm{a}$ is a $p \times 1$ vector of constants,  and $\bm{y}$ is a $p \times 1$ random variable with $\bm{\Sigma}$ as the covariance matrix, then the variance of $z = \bm{a}^{\mathsf{T}}\bm{y}$ is given by
$$
    \sigma^2_z = \operatorname{\text{Var}}\big(\bm{a}^{\mathsf{T}}\bm{y}\big) = \bm{a}^{\mathsf{T}}\bm{\Sigma} \bm{a}
$$

**Proof** 
To make our life easier (from algebraic manipulations, we use the following observation:
$$
\sigma^2_z = \operatorname{\text{Var}}\big(z\big) = \operatorname{\text{Var}}\big(\bm{a}^{\mathsf{T}} (\bm{y} - \operatorname{\mathbb{E}} \left[\bm{y}\right])\big) =  \operatorname{\text{Var}}\big(\bm{a}^{\mathsf{T}}\bm{y'}\big)
$$
where $\bm{y'} = \bm{y} - \operatorname{\mathbb{E}} \left[\bm{y}\right]$.
Also, 
$$
    \operatorname{\text{Cov}}\big(\bm{y'}\big) = \operatorname{\text{Cov}}\big(\bm{y}\big) = \Sigma
$$
Now, 
$$
\begin{aligned}
    \sigma^2_z = \operatorname{\text{Var}}\big(\bm{a}^{\mathsf{T}}\bm{y'}\big) 
        &= \operatorname{\mathbb{E}} \left[\big(\bm{a}^{\mathsf{T}}\bm{y'}\big)^2\right] \\
        &= \operatorname{\mathbb{E}} \left[ \bm{a}^{\mathsf{T}}\bm{y'}\bm{y'}^{\mathsf{T}} \bm{a}\right] \\
        &= \bm{a}^{\mathsf{T}}\operatorname{\mathbb{E}} \left[\bm{y'}\bm{y'}^{\mathsf{T}}\right]\bm{a} \\
        &= \bm{a}^{\mathsf{T}}\bm{\Sigma}\bm{a}
\end{aligned}
$$


**Theorem 3.6d** Let $\bm{z} = \bm{A}\bm{y}$ and $\bm{w} = \bm{B}\bm{y}$ where $\bm{A}$ is a $k \times p$ matrix of constants and $\bm{B}$ is a $m \times p$ matrix of constants, and $\bm{y}$ is a $p \times 1$ random vector with covariance matrix $\Sigma$. Then
1. $\operatorname{\text{Cov}}\big(\bm{z}\big) = \bm{A}\bm{\Sigma}\bm{A}^{\mathsf{T}}$
2. $\operatorname{\text{Cov}}\big(\bm{z}, \bm{w}\big) = \bm{A}\bm{\Sigma}\bm{B}^{\mathsf{T}}$

**Proof**

1. Let's define $\bm{z'} = \bm{A}\bm{y'}$ where $\bm{y'} = \big(\bm{y} - \operatorname{\mathbb{E}} \left[\bm{y}\right]\big)$ and note that $\operatorname{\text{Cov}}\big(\bm{z'}\big) = \operatorname{\text{Cov}}\big(\bm{z}\big)$

$$
    \begin{aligned}
        \operatorname{\text{Cov}}\big(\bm{z'}\big) 
            &= \operatorname{\mathbb{E}} \left[\big(\bm{Ay'}\big) \big(\bm{Ay'}\big)^{\mathsf{T}}\right] \\
            &= \operatorname{\mathbb{E}} \left[\bm{Ay'y'^{\mathsf{T}}\bm{A}^{\mathsf{T}}}\right] \\
            &= \bm{A}\operatorname{\mathbb{E}} \left[\bm{y'y'}^{\mathsf{T}}\right] \bm{A}^{\mathsf{T}} \\
            &= \bm{A\Sigma A^{\mathsf{T}}}
    \end{aligned}
$$

2. Let's define $\bm{z'} = \bm{Ay'}$ and $\bm{w'} = \bm{By'}$ where $\bm{y'} = \big(\bm{y} - \operatorname{\mathbb{E}} \left[\bm{y}\right]\big)$. With that, we can note that 
    $$
    \begin{aligned}
        \operatorname{\text{Cov}}\big(\bm{z'}, \bm{w'}\big) 
            &= \operatorname{\mathbb{E}} \left[\big( \bm{z} - \bm{A}\operatorname{\mathbb{E}} \left[\bm{y}\right]\big)\big( \bm{w} - \bm{B}\operatorname{\mathbb{E}} \left[y\right]\big)^{\mathsf{T}}\right] \\
            &= \operatorname{\mathbb{E}} \left[ \big( \bm{z}\bm{w}^{\mathsf{T}} - \bm{z}\operatorname{\mathbb{E}} \left[\bm{y}\right]^{\mathsf{T}}\bm{B}^{\mathsf{T}} - \bm{A} \operatorname{\mathbb{E}} \left[\bm{y}\right]\bm{w}^{\mathsf{T}} + \bm{A} \operatorname{\mathbb{E}} \left[\bm{y}\right] \operatorname{\mathbb{E}} \left[\bm{y}\right] ^{\mathsf{T}} \bm{B}^{\mathsf{T}}\big) \right] \\
            &= \operatorname{\mathbb{E}} \left[ \bm{z}\bm{w}^{\mathsf{T}} - \bm{A} \operatorname{\mathbb{E}} \left[\bm{y}\right] \operatorname{\mathbb{E}} \left[\bm{y}\right] ^{\mathsf{T}} \bm{B}^{\mathsf{T}}\right] \\
            &= \operatorname{\mathbb{E}} \left[ \bm{zw}^{\mathsf{T}} - \operatorname{\mathbb{E}} \left[\bm{z}\right] \operatorname{\mathbb{E}} \left[ \bm{w}\right]\right] \\ 
            &= \operatorname{\text{Cov}}\big(\bm{z}, \bm{w}\big)
    \end{aligned}
    $$
    Let's now compute $\operatorname{\text{Cov}}\big( \bm{z'}, \bm{w'}\big)$
    $$
    \begin{aligned}
        \operatorname{\text{Cov}}\big(\bm{z'}, \bm{w'}\big) 
            &= \operatorname{\mathbb{E}} \left[ \big(\bm{A} \bm{y'}\big) \big(\bm{By'}\big)^{\mathsf{T}}\right] \\
            &= \operatorname{\mathbb{E}} \left[ \bm{Ay'y'}^{\mathsf{T}}\bm{B}^{\mathsf{T}}\right] \\
            &= \bm{A\Sigma B}^{\mathsf{T}} 

    \end{aligned}
    $$

## Mean and Variance of Quadratic Forms
In this subsection, we'll work with the quadratic form $\bm{y}^{\mathsf{T}}\bm{Ay}$, where $\bm{y} \in \mathbb{R}^p$.

**Theorem 5.2a (Mean of a quadratic form)** If $\bm{y}$ is a random vector with mean $\bm{\mu}$ and covariance matrix $\bm{\Sigma}$, and $\bm{A}$ is a symmetric matrix of constants, then

$$
\operatorname{\mathbb{E}} \left[ \bm{y}^{\mathsf{T}}\bm{Ay}\right] = \bm{\mu}^{\mathsf{T}} \bm{A\mu} + \operatorname{\text{tr}}\big(\bm{A\Sigma}\big)
$$

**Proof 1 (my proof)**

$$
\begin{aligned}
    \operatorname{\mathbb{E}} \left[\bm{y}^{\mathsf{T}}\bm{Ay}\right] 
        &= \operatorname{\mathbb{E}} \left[\sum_{i=1}^{p}\sum_{j=1}^p A_{ij}y_iy_j\right] \\
        &= \sum_{i=1}^p\sum_{j=1}^p A_{ij} \operatorname{\mathbb{E}} \left[y_iy_j\right] \\
\end{aligned}
$$
Now, $\operatorname{\mathbb{E}} \left[y_iy_j\right] = \Sigma_{ij} + \mu_i\mu_j$. Put this back in the equation above.

$$
\begin{aligned}
    \operatorname{\mathbb{E}} \left[\bm{y}^{\mathsf{T}}\bm{Ay}\right] 
        &= \sum_{i=1}^p\sum_{j=1}^p A_{ij} \big(\Sigma_{ij} + \mu_i\mu_j\big)  \\
        &= \sum_{i=1}^p\sum_{j=1}^p A_{ij} \Sigma_{ij} + \sum_{i=1}^p\sum_{j=1}^p A_{ij} \mu_i\mu_j \\
        &= \sum_{i=1}^p\sum_{j=1}^p A_{ij} \Sigma_{ji} + \bm{\mu}^{\mathsf{T}}\bm{A}\bm{\mu} \\
        &= \operatorname{\text{tr}}\big(\bm{A\Sigma}\big) + \bm{\mu}^{\mathsf{T}}\bm{A}\bm{\mu} \\
\end{aligned}
$$

**Proof 2 (from Rencher)**
$$
\begin{aligned}
    \operatorname{\mathbb{E}} \left[\bm{y}^{\mathsf{T}}\bm{Ay}\right] 
        &= \operatorname{\mathbb{E}} \left[\operatorname{\text{tr}}\big( \bm{y}^{\mathsf{T}}\bm{Ay}\big)\right] \\
        &=  \operatorname{\mathbb{E}} \left[\operatorname{\text{tr}}\big(\bm{Ayy}^{\mathsf{T}}\big)\right]\\
        &= \operatorname{\text{tr}}\big(\operatorname{\mathbb{E}} \left[\bm{Ayy}^{\mathsf{T}}\right]\big) \\
        &= \operatorname{\text{tr}}\big(\bm{A}\operatorname{\mathbb{E}} \left[\bm{yy}^{\mathsf{T}}\right]\big)
\end{aligned}
$$
Now, 
$$
\begin{aligned}
    \operatorname{\text{Cov}}\big(\bm{y}\big) 
        &= \operatorname{\mathbb{E}} \left[\big(\bm{y} - \bm{\mu}\big)\big(\bm{y} - \bm{\mu}\big)^{\mathsf{T}}\right] \\
        &= \operatorname{\mathbb{E}} \left[\bm{yy}^{\mathsf{T}}\right] - \bm{\mu\mu}^{\mathsf{T}} \\
        \Rightarrow \operatorname{\mathbb{E}} \left[\bm{yy}^{\mathsf{T}}\right] &= \bm{\Sigma} + \bm{\mu\mu}^{\mathsf{T}}
\end{aligned}
$$
This gives us following:

$$
\begin{aligned}
    \operatorname{\mathbb{E}} \left[\bm{y}^{\mathsf{T}}\bm{Ay}\right]
        &= \operatorname{\text{tr}}\big(\bm{A\Sigma}\big) + \operatorname{\text{tr}}\big(\bm{A\mu\mu}^{\mathsf{T}}\big) \\
        &= \operatorname{\text{tr}}\big(\bm{A\Sigma}\big) + \operatorname{\text{tr}}\big(\bm{\mu}^{\mathsf{T}}\bm{A\mu}\big) \\
        &= \operatorname{\text{tr}}\big(\bm{A\Sigma}\big) + \bm{\mu}^{\mathsf{T}}\bm{A\mu}
\end{aligned}
$$
