# Matrix-Vector Product

:::success
Linear System
= System of Linear Equations
= Matrix-Vector Product
:::

## Matrix-Vector Product Operation
Take each Row of the matrix and the vector as **Inner Product**
$$A = \begin{bmatrix} a_{11} & a_{12} & \dots & a_{1n} \\
a_{21} & a_{22} & \dots & a_{2n} \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1} & a_{m2} & \dots & a_{mn}\end{bmatrix} \quad x = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n\end{bmatrix}\\
Ax = \begin{bmatrix} a_{11}x_1 & a_{12}x_2 & \dots & a_{1n}x_n \\
a_{21}x_1 & a_{22}x_2 & \dots & a_{2n}x_n \\
\vdots & \vdots & \ddots & \vdots \\
a_{m1}x_1 & a_{m2}x_2 & \dots & a_{mn}x_n\end{bmatrix}
$$

Take each Column of the matrix and the vector as **Weighted Sum**
$$x_1 \begin{bmatrix} a_{11} \\ \vdots \\ a_{m1}\end{bmatrix} + x_2 \begin{bmatrix} a_{12} \\ \vdots \\ a_{m2}\end{bmatrix} + \dots + x_n \begin{bmatrix} a_{1n} \\ \vdots \\ a_{mn}\end{bmatrix}
$$

In general:
![](https://i.imgur.com/Yc2j0UG.png)

## Linear System?
We can regard System of Linear Equations as Matrix-Vector Product
![](https://i.imgur.com/AXBNB7N.png)

:::success
A matrix can be describe as a system of linear equations
:::

## Example
$$\begin{cases} x_1 + 4x_2 = b_1 \\ -3x_1 + 2x_2 = b2 \end{cases}
$$

$$A = \begin{bmatrix} 1 & 4 \\ -3 & 2 \end{bmatrix} \qquad x = \begin{bmatrix} -2 \\ 0.5 \end{bmatrix}
$$

![](https://i.imgur.com/ngPHiMA.png)



| Row Aspect                           | Column Aspect                        |
| ------------------------------------ | ------------------------------------ |
| ![](https://i.imgur.com/WjQtWiG.png) | ![](https://i.imgur.com/Rowoiz4.png) |

## Properties
> The size of matrix and vector should be matched.

:::info
A matrix and a vector can be multiply, if and only if **the number of columns in matrix** is equal to **the number of vector's component**
:::

- $A$ and $B$ are $m \times n$ matrices, $u$ and $c$ are vectors in $\mathscr{R}^n$, and $c$ is a scalar
	- $A(u + v) = Au + Av$
	- $A(cu) = c(Au) = (cA)u$
	- $(A + B)u = Au + Bu$
	- $A0$ is a $m \times 1$ zero vector
	- $Ov$ is also the $m \times 1$ zero vector
	- $I_nv = v$

$A$ and $B$ are $m \times n$ matrices. If $Aw = Bw$ for all $w$ in $\mathscr{R}^n$. Is it true that $A=B$ ?(O)

> $Ae_j = a_j$, where $e_j$ is the $j$-th standard vector in $\mathscr{R}$
> ![](https://i.imgur.com/urOwU5i.png)
> Assume $w = e_n$, then $a_n=b_n$ => $A=B$

:::success
We only need to check all standard vectors multiply by $A$ or $B$ to check if the result are the same
And we can know if $A = B$ holds
:::

###### tags: `線性代數筆記`