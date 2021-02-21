# Orthogonal Basis

## Orthogonal Set
A set of vectors is called an orthogonal set if every pair of distinct vectors in the set is orthogonal

:::warning
Orthogonal Set is may not be independent
:::

## Independent
Any orthogonal set of **nonzero** vectors is linearly independent

***Proof***

Let $S = \{v_1, v_2, \dots, v_k\}$ be an orthogonal set $v_i \neq 0$ for $i = 1, 2, \dots, k$

Assume $c_1, c_2, \dots, c_k$ make $c_1v_1 + c_2v_2 + \dots + c_kv_k = 0$

$$(c_1v_1 + c_2v_2 + \dots + c_iv_i + \dots + c_kv_k) \cdot v_i \\
= c_i(v_i \cdot v_i) = c_i||v_i||^2 , ||v_i||^2 \neq 0\\
\Rightarrow c_i = 0 \Rightarrow c_1 = c_2 = \dots = c_k = 0
$$

## Orthonomal Set
A set of vectors is called an orthonormal set if it is an orthogonal set, and the norm of all the vectors is $1$

![](https://i.imgur.com/d8PPiFc.png)

:::success
Orthonormal set is independent
:::

:::info
A vector that has norm equal to 1 is called a unit vector
:::

## Orthogonal Basis
A basis that is an orthogonal(orthonormal) set is called an orthogonal(orthonormal) basis

For Example

$$\begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} \quad \begin{cases} \texttt{Orthogonal basis of } \mathscr{R}^3 \\ \texttt{Orthonormal basis of } \mathscr{R}^3 \end{cases}
$$ 

## Orthogonal Decomposition Theory
### Orthogonal Basis
Let $S = \{v_1, v_2, \dots, v_k\}$ be an orthogonal basis for a subspace $W$, and let $u$ be a vector in $W$

$[u]_S = \begin{bmatrix} c_1 \\ c_2 \\ \vdots \\ C_k \end{bmatrix}$

$$u = c_1v_1 + c_2v_2 + \dots + c_kv_k\\
c_1 = \frac{u \cdot v_1}{||v_1||^2} \quad c_2 = \frac{u \cdot v_2}{||v_2||^2} \quad c_k = \frac{u \cdot v_k}{||v_k||^2}
$$

:::info
This is estiblished when is orthogonal
:::

***Proof***

To find $c_i$
$$u \cdot v_i = (c_1v_1 + c_2v_2 + \dots + c_iv_i + \dots + c_kv_k) \cdot v_i\\
= c_1v_1 \cdot v_i + c_2v_2 \cdot v_i + \dots + c_iv_i \cdot v_i + \dots + c_kv_k \cdot v_i \\
= c_i(v_i \cdot v_i) = c_i ||v_i||^2 \Rightarrow c_i = \frac{u \cdot v_i}{||v_i||^2}
$$

> How about orthonormal basis?

$||v_i||^2 = 1 \Rightarrow c_i = u \cdot v_i$

***Example***

$S = \{v_1, v_2, v_3\}$ is an orthogonal basis for $\mathscr{R}^3$

$v_1 = \begin{bmatrix} 1 \\ 2 \\ 3 \end{bmatrix} \quad v_2 = \begin{bmatrix} 1 \\ 1 \\ -1 \end{bmatrix} \quad v_3 = \begin{bmatrix} 5 \\ -4 \\ 1 \end{bmatrix}$

Let $u = \begin{bmatrix} 3 \\ 2 \\ 1 \end{bmatrix}$ and $u = c_1v_1 + c_2v_2 + c_3v_3$

$c_1 = \frac{u \cdot v_1}{||v_1||^2} = \frac{10}{14} \quad c_2 = \frac{u \cdot v_2}{||v_2||^2} = \frac{4}{3} \quad c_3 = \frac{u \cdot v_3}{||v_3||^2} = \frac{8}{42}$

### Orthogonal Projection
Let $u$ be any vector, and $w$ is the orthogonal projection of $u$ on $W$

$w = c_1v_1 + c_2v_2 + \dots + c_kv_k$

$c_1 = \frac{u \cdot v_1}{||v_1||^2} \quad c_2 = \frac{u \cdot v_2}{||v_2||^2} \quad c_3 = \frac{u \cdot v_3}{||v_3||^2}$

***Proof***

The formula of Orthogonal Projection is $P_W = C(C^TC)^{-1}C^T$

$C^T = \begin{bmatrix} v_1^T \\ v_2^T \\ \vdots \\ v_k^T \end{bmatrix} \quad C = \begin{bmatrix} v_1 & \dots & v_k \end{bmatrix}$

$C^TC$ is a diagonal matrix, which only have values on diagonal, and others are zero, denoted $D$

$$D = \begin{bmatrix} ||v_1||^2 & 0 & \dots & \dots \\ 0 & ||v_2||^2 & \dots & \dots \\ 0 & \dots & \ddots & \dots \\ 0 & \dots & \dots & ||v_k||^2 \end{bmatrix}
$$

$$D^{-1} = \begin{bmatrix} \frac{1}{||v_1||^2} & 0 & \dots & \dots \\ 0 & \frac{1}{||v_2||^2} & \dots & \dots \\ 0 & \dots & \ddots & \dots \\ 0 & \dots & \dots & \frac{1}{||v_k||^2} \end{bmatrix}
$$

$P_W = CD^{-1}C^T$

Projected: $w = CD^{-1}C^Tu$
$$C^Tu = \begin{bmatrix} v_1^Tu & v_2^Tu & \dots & v_k^Tu\end{bmatrix}\\
\Rightarrow D^{-1}C^Tu = \begin{bmatrix} \frac{v_1^Tu}{||v_1||^2} & \frac{v_2^Tu}{||v_2||^2} & \dots & \frac{v_k^Tu}{||v_k||^2}\end{bmatrix}\\
w = \frac{u \cdot v_1}{||v_1||^2}v_1 + \frac{u \cdot v_2}{||v_2||^2}v_2 + \dots + \frac{u \cdot v_k}{||v_k||^2}v_k
$$

:::success
If we have orthogonal basis, we can calculate orthogonal projection more easily
$$w = \frac{u \cdot v_1}{||v_1||^2}v_1 + \frac{u \cdot v_2}{||v_2||^2}v_2 + \dots + \frac{u \cdot v_k}{||v_k||^2}v_k
$$
:::

## How to find Orthonormal Basis
***Gram-Schmidt Process***

Let $\{u_1, u_2, \dots, u_k\}$ be a basis of a subspace $V$. How to transform it into an orthogonal basis $\{v_1, v_2, \dots, v_k\}$?

$$v_1 = u_1\\
v_2 = u_2 - \frac{u_2 \cdot v_1}{||v_1||^2}v_1\\
v_3 = u_3 - \frac{u_3 \cdot v_1}{||v_1||^2}v_1 - \frac{u_3 \cdot v_2}{||v_2||^2}v_2\\
\vdots\\
v_k = u_k - \frac{u_k \cdot v_1}{||v_1||^2}v_1 - \frac{u_k \cdot v_2}{||v_2||^2}v_2 - \dots - \frac{u_k \cdot v_{k-1}}{||v_{k-1}||^2}v_{k-1}
$$

Then, $\{v_1, v_2, \dots, v_k\}$ is an orthogonal basis for $W$

***Span $\{v_1, v_2, \dots, v_i\}$ = Span $\{u_1, u_2, \dots, u_i\}$*** ($i$ can not equal to $k$)

![](https://i.imgur.com/RWg3ZjB.png)

![](https://i.imgur.com/Rh7H2Ay.gif)


***proof***

***Span $\{v_1, v_2, \dots, v_i\}$ = Span $\{u_1, u_2, \dots, u_i\}$*** ($i$ can not equal to $k$)

Ther throrem holds for $k = 1$

Assume the theorem holds for $k = n$, and consider the case for $k = n+1$

> proof $v_{n+1} \cdot v_i = 0\ (i<n+1)$

$$v_{n+1} \cdot v_i = u_{n+1} \cdot v_i - \frac{u_{n+1} \cdot v_i}{||v_i||^2} v_i \cdot v_i\\
= u_{n+1} \cdot v_i - u_{n+1} \cdot v_i = 0
$$

By Math Induction, $Span\ \{v_1, v_2, \dots, v_i\} = Span\ \{u_1, u_2, \dots, u_i\}$

Let $V$ the subspace of $Span\ \{u_1, u_2, \dot, u_k\}$

Is $Span\ \{v_1, v_2, \dots, v_k\}$ in $V$? (O)

1. $dim\ Span\ \{u_1, u_2, \dot, u_k\} = dim\ Span\ \{v_1, v_2, \dots, v_k\}$
2. $v$ is the linear combination of $u$
3. $v$ is non-zero and orthogonal, $v$ is independent

***Example***

$S = \{u_1, u_2, u_3\}$ is a basis for subspace $W$

$u_1 = \begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix} \quad u_2 = \begin{bmatrix} 2 \\ 1 \\ 0 \\ 1 \end{bmatrix} \quad u_3 = \begin{bmatrix} 1 \\ 1 \\ 2 \\ 1 \end{bmatrix}$ (Linear Independent vectors)

$$v_1 = u_1 = \begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix}\\
v_2 = u_2 - \frac{u_2 \cdot v_1}{||v_1||^2} v_1 = \begin{bmatrix} 2 \\ 1 \\ 0 \\ 1 \end{bmatrix} - \frac{4}{4}\begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix} = \begin{bmatrix} 1 \\ 0 \\ -1 \\ 0 \end{bmatrix}\\
v_3 = u_3 - \frac{u_3 \cdot v_1}{||v_1||^2}v_1 - \frac{u_3 \cdot v_2}{||v_2||^2}v_2 = \begin{bmatrix} 1 \\ 1 \\ 2 \\ 1 \end{bmatrix} - \frac{5}{4}\begin{bmatrix} 1 \\ 1 \\ 1 \\ 1 \end{bmatrix} - \frac{(-1)}{2}\begin{bmatrix} 1 \\ 0 \\ -1 \\ 0 \end{bmatrix} = \frac{1}{4}\begin{bmatrix} 1 \\ -1 \\ 1 \\ -1 \end{bmatrix}
$$

Then $S' = \{v_1, v_2, v_3\}$ is an orthogonal basis for $W$

$S'' = \{av_1, bv_2, cv_3\}$, $a, b, c$ are scalars is also an orthogonal basis

###### tags: `線性代數筆記`