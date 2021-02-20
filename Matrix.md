# Matrix

[![hackmd-github-sync-badge](https://hackmd.io/FuQgfmpPRmiFHeiSLsrAQA/badge)](https://hackmd.io/FuQgfmpPRmiFHeiSLsrAQA)


## Definition
If the matrix has $m$ rows and $n$ columns, we say the size of the matrix is $m$ by $n$, written $m \times n$

We use $\mathscr{M}_{m \times n}$ to denote the set that contains all matrices whose size is $m \times n$
> ![](https://i.imgur.com/sNyRNAd.png)

:::success
In matrix, **row** first then **column**
:::

### Component
> the scalar in the $i$-th row and $j$-th column is called $(i,j)$-entry of the matrix

$$A = \begin{bmatrix} a_{11} & a_{12} & \dots & a_{1n} \\
a_{21} & a_{22} & \dots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \dots & a_{mn}\end{bmatrix}
$$

We can regard every column as a vector
$$A = \begin{bmatrix}a_1 & a_2 & \dots & a_n \end{bmatrix}
$$

:::success
Again, in matrix, **row** first then **column**
:::

## Properties
- Two matrices with the same size can add or substract.
	$$A=\begin{bmatrix} 1 & 4 \\ 2 & 5 \\ 3 & 6\end{bmatrix} \quad B = \begin{bmatrix} 6 & 9 \\ 8 & 0 \\ 9 & 2\end{bmatrix} \\ \\ A+B = \begin{bmatrix} 7 & 13 \\ 10 & 5 \\ 12 & 8\end{bmatrix} \quad A-B = \begin{bmatrix} -5 & -5 \\ -6 & 5 \\ -6 & -4\end{bmatrix}
	$$

- Matrix can multiply by a scalar
	$$9B = \begin{bmatrix} 54 & 81 \\ 72 & 0 \\ 81 & 18\end{bmatrix}
	$$

- A, B, C are $m \times n$ matrices, and s and t are scalars
	- $A + B = B + A$
	- $(A + B) + C = A + (B + C)$
	- $(st)A = s(tA)$
	- $s(A + B) = sA + sB$
	- $(s+t)A = sA + tA$

## Special Matrices
### Square matrix
A matrix $A_{m \times n}$ which $m=n$, we called $A$ a Square matrix

![](https://i.imgur.com/CJ0W0mQ.png)

Only Square matrix have a **diagonal**
![](https://i.imgur.com/fuQLBuN.png)

### Upper Triangular Matrix
A Square matrix whose component are all $0$ below the diagonal

![](https://i.imgur.com/7iAHM4B.png)

### Lower Triangular Matrix
A Square matrix whose component are all $0$ above the diagonal

![](https://i.imgur.com/O7PQZAo.png)


### Diagonal Matrix
A Square matrix whose non-diagonal component are all $0$

![](https://i.imgur.com/4zRSwQF.png)

### Identity Matrix
A Square matrix whose diagonal component are all $1$, and non-diagonal component are all $0$

![](https://i.imgur.com/goTMVTj.png)

We use $I_n$ to denote that the matrix is a $n$ by $n$ identity matrix

### Zero Matrix
A Matrix whose component are all $0$

![](https://i.imgur.com/tqPGLxZ.png)

We use $O_{m \times n}$ to denote that the matrix is a $m$ by $n$ zero matrix

## Transpose
If $A$ is an $m \times n$ matrix, $A^T$ (transpose of A) is an $n \times m$ matrix whose $(i,j)$-entry is the $(j,i)$-entry of $A$

![](https://i.imgur.com/qtXk4LZ.png)

:::success
Column $\Rightarrow$ Row
Row $\Rightarrow$ Column
:::

### 特性 Properties
Let $A$ and $B$ are $m \times n$ matrices, and $s$ is a scalar
- $(A^T)^T = A$
- $(sA)^T = sA^T$
- $(A+B)^T = A^T + B^T$

:::success
Transpose is a linear system
:::

### Symmetric Matrix
A matrix which $A^T = A$

![](https://i.imgur.com/JyMJUth.png)


###### tags: `線性代數筆記`