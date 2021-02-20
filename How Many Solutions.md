# How many Solutions

We have already know that if a system of linear equations have solution, then there's only **one solution** or **infinite solutions**.

And we know that,we can use these two conditions to know whether a system of linear equations have solution or not.
- is $b$ a linear combination columns of $A$ ?
- is $b$ in the span of the columns of $A$ ?

If the two conditions are hold, then it has solution, but how many solutions?

![](https://i.imgur.com/lW5hJaS.png)

## Dependent & Independent
### Definition
- A set of n vectors $\{a_1, a_2, ... , a_n\}$ is linear **depentent**
	- if we can find scalars $x_1, x_2, x_3, ... , x_n$, **not all zero**, such that $a_1x_1 + a_2x_2 + ... + an_xn = 0$
- A set of n vectors $\{a_1, a_2, ... , a_n\}$ is linear **indepentent**
	- if we can find scalars $x_1, x_2, x_3, ... , x_n$, such that $a_1x_1 + a_2x_2 + ... + an_xn = 0$, only if $x_1=x_2=...=x_n=0$

:::success
Dependent $\Rightarrow$ Infinite Solutions
Independent $\Rightarrow$ One Solution
:::

***Example 1***

$$A = \{ \begin{bmatrix} -4 \\ 12 \\ 6 \end{bmatrix}, \begin{bmatrix} -10 \\ 30 \\ 15 \end{bmatrix}\}\\
a_1 = \frac{2}{5}a_2 \\
\Rightarrow x_1 = 1,\ x_2 = \frac{-2}{5} \\
\Rightarrow x_1a_1 + x_2a_2 = 0
$$

$x_1,\ x_2$ not all zero $\Rightarrow$ **Dependent**

---

***Example2***

$$A = \{\begin{bmatrix} 6 \\ 3 \\ 3 \end{bmatrix}, \begin{bmatrix} 1 \\ 8 \\ 3 \end{bmatrix}, \begin{bmatrix} 7 \\ 11 \\ 6 \end{bmatrix}\}\\
a_3 = a_1 + a_2 \\
\Rightarrow x_1 = 1,\ x_2 = 1,\ x_3 = 1 \\ \Rightarrow x_1a_1 + x_2a_2 + x_3a_3 = 0
$$
$x_1,\ x_2,\ x_3$ not all zero $\Rightarrow$ **Dependent**

---

***Example 3***

$$A = \{\begin{bmatrix} 3 \\ -1 \\ 7 \end{bmatrix}, \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}, \begin{bmatrix} -2 \\ 5 \\ 1 \end{bmatrix}\}\\
x_1 \triangleq 0 \quad x_3 \triangleq 0 \quad x_2 \neq 0\\
\Rightarrow x_1a_1 + x_2a_2 + x_3a_3 = 0
$$
$x_1,\ x_2,\ x_3$ not all zero $\Rightarrow$ **Dependent**

:::success
Zero vector is the linear combination of any other vectors

Any set contains zero vector would be linear dependent
:::

:::success
If there exists any $a_i$ that is a linear combination of other vectors, then it is dependent (when component of the vector is more than one)
:::

:::success
Dependent: Once we have solution, we have **infinite**. 
:::

***Proof***
#### Homogeneous linear equations
$$Ax = 0 \qquad A=\begin{bmatrix} a_1, a_2, a_3, \dots , a_n \end{bmatrix} \qquad x= \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}
$$
always having $0$ as solution

---

![](https://i.imgur.com/KAzfO5j.png)

- Columns of $A$ are dependent $\Rightarrow$ If $Ax=b$ have solution, it will have Infinite solutions
	![](https://i.imgur.com/Jwblhjf.png)
- If $Ax=b$ have Infinite solutions $\Rightarrow$ Columns of $A$ are dependent 
	![](https://i.imgur.com/wsT6vYF.png)

## Rank & Nullity
### Definition
- **Rank**
	
    the maximum number of *linearly independent columns* in the matrix
- **Nullity**
	
    Numbers of columns - **rank**

### Examples
$$\begin{bmatrix} -3 & 2 & -1 \\ 7 & 9 & 0 \\ 0 & 0 & 2 \end{bmatrix}
$$

|         | Numbers     |
| ------- | ----------- |
| Columns | $3$         |
| Rank    | $3$         |
| Nullity | $3 - 3 = 0$ |

---
$$\begin{bmatrix} 1 & 3 & 10 \\ 2 & 6 & 20 \\ 3 & 9 & 30 \end{bmatrix}
$$
|         | Numbers     |
| ------- | ----------- |
| Columns | $3$         |
| Rank    | $1$         |
| Nullity | $3 - 1 = 2$ |

---
$$\begin{bmatrix} 0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0 \end{bmatrix}
$$
|         | Numbers     |
| ------- | ----------- |
| Columns | $3$         |
| Rank    | $0$         |
| Nullity | $3 - 0 = 3$ |

---
$$\begin{bmatrix} 1 & 3 & 4 \\ 2 & 6 & 8 \end{bmatrix}
$$
|         | Numbers     |
| ------- | ----------- |
| Columns | $3$         |
| Rank    | $1$         |
| Nullity | $3 - 1 = 2$ |

---
$$\begin{bmatrix} 0 & 3 \\ 0 & 5 \end{bmatrix}
$$
Only take $\begin{bmatrix} 3 \\ 5\end{bmatrix}$
|         | Numbers     |
| ------- | ----------- |
| Columns | $2$         |
| Rank    | $1$         |
| Nullity | $2 - 1 = 1$ |

---
$$\begin{bmatrix} 5 \\ 2 \end{bmatrix}
$$
|         | Numbers     |
| ------- | ----------- |
| Columns | $1$         |
| Rank    | $1$         |
| Nullity | $1 - 1 = 0$ |

---
$$\begin{bmatrix} 6 \end{bmatrix}
$$
|         | Numbers     |
| ------- | ----------- |
| Columns | $1$         |
| Rank    | $1$         |
| Nullity | $1 - 1 = 0$ |

---

:::success
Rank A = n

Nullity A = 0

=> independent

=> **One Solution**

---

Rank A < n

Nullity A > 0

=> dependent

=> **Infinite Solutions**

---

![](https://i.imgur.com/onWSZDr.png)

:::

![](https://i.imgur.com/kgDVrIJ.png)

---

![](https://i.imgur.com/Dy1TnXk.png)

> FTFTT

1. If the columns of $A$ are linear independent, then $Ax=b$ has unique solution.
	
    當 $A$ 是 indepedent ，需要再確認 $b$ 是否包含在 $Span\ A$
2. If the columns of $A$ are linear independent, then $Ax=b$ has at most one solution.
	
    當 $b$ 是包含在 $Span\ A$ 時，由於 independent， 根據定義我們只能找到一個解
	
    若 $b$ 不包含，則無解
3. If the columns of $A$ are linear dependent, then $Ax=b$ has infinite solution.
	
    當 $A$ 是 depedent ，需要再確認 $b$ 是否包含在 $Span\ A$
4. If the columns of $A$ are linear independent, then $Ax=0$ (homogeneous equation) has unique solution.
	
    由於 $b$ 是 $0$ ，使得方程式為 homogenous ，$b$ 必定包含在 $Span\ A$
	
    又因為是 independent ，可以知道會是唯一解
5. If the columns of $A$ are linear dependent, then $Ax=0$ (homogeneous equation) has infinite solution.
	
    由於 $b$ 是 $0$ ，使得方程式為 homogenous ，$b$ 必定包含在 $Span\ A$
	
    又因為是 dependent ，可以知道會是無限多解

###### tags: `線性代數筆記`