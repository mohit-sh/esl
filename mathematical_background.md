# Mathematical Background

## Quadratic Forms (Completing the squares)

**Proposition 1** For any vector $$\bm{x}, \bm{b} \in \mathbb{R}^d$$ and a symmetric invertible matrix $$\bm{M} \in \mathbb{R}^{d\times d}$$, we have

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

Consider this generic form for the RHS (Paise and think why this makes sense!)

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

**Proposition 2** Sum of two quadratic forms $$f(\bm{x})$$ 

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
Note that we are assuming the invertibility of $$\bm{M}$$.

**Proof** Upon expansion, we can write $$f(\bm{x})$$ as follows

$$
\begin{aligned}
    f({\bm{x}})   &= (\bm{x} - \bm{\mu})^{\mathsf{T}}\bm{\Sigma}^{-1}(\bm{x} - \bm{\mu}) + (\bm{x} - \bm{\theta})^{\mathsf{T}}\bm{V}^{-1}(\bm{x} - \bm{\theta}) \\
                &= \bm{x}^{\mathsf{T}}\bm{\Sigma}^{-1}\bm{x} + \bm{x}^{\mathsf{T}}\bm{V}^{-1}\bm{x} -2 \bm{\mu}^{\mathsf{T}}\bm{\Sigma}^{-1}\bm{x} - 2\bm{\theta}^{\mathsf{T}}\bm{V}^{-1}\bm{x} + \bm{\mu}^{\mathsf{T}}\bm{\Sigma}^{-1}\bm{\mu} + \bm{\theta}^{\mathsf{T}}\bm{V}^{-1}\mathsf{\theta} \\
                &= \bm{x}^{\mathsf{T}}(\bm{\Sigma}^{-1} + \bm{V}^{-1})\bm{x} - 2 (\bm{\Sigma}^{-1}\bm{\mu} + \bm{V}^{-1}\bm{\theta})^{\mathsf{T}}\bm{x} + \bm{\mu}^{\mathsf{T}}\bm{\Sigma}^{-1}\bm{\mu} + \bm{\theta}^{\mathsf{T}}\bm{V}^{-1}\mathsf{\theta} \\
                &= \bm{x}^{\mathsf{T}}\bm{M}\bm{x} - 2 \bm{b}^{\mathsf{T}}\bm{x} + \bm{\mu}^{\mathsf{T}}\bm{\Sigma}^{-1}\bm{\mu} + \bm{\theta}^{\mathsf{T}}\bm{V}^{-1}\mathsf{\theta} \\
                &= (\bm{x} - \bm{M}^{-1}\bm{b})^{\mathsf{T}}\bm{M}(\bm{x} - \bm{M}^{-1}\bm{b}) + m
\end{aligned}
$$
We used **Proposition 1** in the last step.