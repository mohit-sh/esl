# Mathematical Background

## Quadratic Forms

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
