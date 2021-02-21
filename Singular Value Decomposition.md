# Singular Value Decomposition

Diagonalization can only apply on some square matrices, but Singular Value Decomposition (SVD) can apply on any matrix

For any $m \times n$ matrix $A$
![](https://i.imgur.com/VDP2mbS.png)

- $U$ is Orthonormal
- $\sum$ is Diagonal
- $V^T$ is Orthonormal

:::info
$U$ and $V^T$ are both orthonormal and independent
:::

:::info
Diagonal in $\sum$ matrix
$$\begin{bmatrix}
v_1 & 0 & \dots & 0\\
0 & v_2 & \dots & 0\\
0 & 0 & \ddots & \vdots\\
0 & 0 & 0 & v_n\\
\vdots & \vdots & \vdots & \vdots\\
0 & 0 & 0 & 0
\end{bmatrix}
$$

The diagonal entries are non-negative, and increasing numbers
:::

numbers on diagonal can be $0$
![](https://i.imgur.com/ktSUFPk.png)

What is the rank of $A$? ($k$)

$k$ is the numbers of non-zero number on $\sum$'s diagonal

:::success
If $A$ is a $m \times n$ matrix, and $B$ is a $n \times k$ matrix
$$Rank(AB) \leq min(Rank(A), Rank(B))
$$

If $B$ is a matrix of Rank $n$
$$Rank(AB) = Rank(A)
$$

If $A$ is a matrix of Rank $n$
$$Rank(AB) = Rank(B)
$$
:::

We can ignore zeros in $\sum$
Let $\sum '$ be a $k \times k$ matrix
![](https://i.imgur.com/Uwcy6r7.png)

Then, we can ignore numbers that will multiply by the number we ignored in $\sum$

Let $U_1$ ba a $m \times k$ matrix, and $V_1^T$ be a $k \times n$ matrix

The result won't change
![](https://i.imgur.com/BnfpMOL.png)

> How about ignore $\sigma_{k}$?

![](https://i.imgur.com/UdAEdms.png)

$A \neq A'$
![](https://i.imgur.com/8vx2aZL.png)

:::success
$A'$ is the rank $k-1$ matrix minimizing $||A - A'||$

$A'$ is the closet matrix to $A$ in $(k-1) \times (k-1)$ matrix
:::

## Low Rank Approximation using SVD
We can use SVD to compress picture

We can choose $k$ by ourself, the smaller the value of k, the greater the amount of compression

![](https://i.imgur.com/dSP4N6K.gif)

In the gif, we can figure out that we don’t need a large $k$ to have good results

We need to store $m \times n$ matrix, but now we only need $(m + n + 1) \times k$

###### tags: `線性代數筆記`