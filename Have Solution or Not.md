# Have Solution or not

Given Linear System and an output $b$, how to find input $x$ ?

## High School Perspective
Draw two System of Linear Equations on the graph to see if there's an intersrction or not

There are three conditions
- unique solution (consistent)
- no solution (inconsistent)
- infinite silutions (consistent)

:::info
Why there's only **one solution** and **infinite solution** when it has solution, but no **two solution** ?

We can easily create infinite solutions if we have two solutions
![](https://i.imgur.com/nPOzeXk.png)
:::

## Linear Algebra Perspective
![](https://i.imgur.com/sWLxltS.png)

### Linear Combination
- Given a vector set $\{u_1, u_2, ..., u_k\}$
- The Linear combination of the vectors in the set
	- $v = c_1u_1 + c_2u_2 + ... + c_ku_k$
	- $c_1, c_2, ..., c_k$ are scalars

$$\texttt{vector set: }\{\begin{bmatrix} 1 \\ 1\end{bmatrix}, \begin{bmatrix} 1 \\ 3\end{bmatrix}, \begin{bmatrix} 1 \\ -1\end{bmatrix}\} \quad \texttt{coefficients: }\{ -3, 4, 1\} \\
-3\begin{bmatrix} 1 \\ 1 \end{bmatrix} + -4\begin{bmatrix} 1 \\ 3 \end{bmatrix} + 1\begin{bmatrix} 1 \\ -1 \end{bmatrix}
$$

> That is weighted sum

![](https://i.imgur.com/QQd9ZoN.png)

### System of Linear Equations v.s. Linear Combination

Asking whether $Ax = b$ is established is equivalent to ask whether $x_1a_1 + x_2a_2 + \dots + x_na_n$ is equal to $b$ or not

***Example 1***
$$\begin{cases}3x_1 + 6x_2 = 3 \\ 2x_1 + 4x_2 = 4\end{cases} \qquad Ax = b
$$

$$\\ A = \begin{bmatrix} 3 & 6 \\ 2 & 4 \end{bmatrix}, x = \begin{bmatrix} x_1 \\ x_2 \end{bmatrix}, b = \begin{bmatrix} 3 \\ 4 \end{bmatrix}
$$


![](https://i.imgur.com/jWPDfkP.png)

![](https://i.imgur.com/gGKXEv0.png)

***Example 2***
$$\begin{cases}2x_1 + 3x_2 = 4 \\ 3x_1 + 1x_2 = -1 \end{cases} \quad Ax = b
$$

$$A = \begin{bmatrix} 2 & 3 \\ 3 & 1 \end{bmatrix},\
x = \begin{bmatrix} x_1 \\ x_2 \end{bmatrix},\ 
b = \begin{bmatrix} 4 \\ -1 \end{bmatrix}
$$

![](https://i.imgur.com/Chiz1DK.png)

:::success
If **u** and **v** are any nonparallel vectors in $\mathscr{R}^2$, then every vectors in $\mathscr{R}^2$ is a linear combination of $u$ and $v$
![](https://i.imgur.com/O9grlPa.png)
:::

> Now, we know that any two non-parallel vectors can be combined into any plane vectors, does reverse statement also hold? (X)

> If we have three non-parallel vectors **u**, **v**, **w**, can they combined into any $3$-d vectors? (X)
> 
> Established if and only if the three vectors are not in the same plane

#### Example 3
$$\begin{cases}2x_1 + 6x_2 = -4\\
1x_1 + 3x_2 = -2 \end{cases} \quad Ax = b
$$

$$A = \begin{bmatrix} 2&6 \\1&3 \end{bmatrix},\ 
x = \begin{bmatrix} x_1 \\ x_2 \end{bmatrix},\ 
b = \begin{bmatrix} -4  \\ -2 \end{bmatrix}
$$

![](https://i.imgur.com/a4QVDP1.png)

### Span
Given a Vector set $S = \{u_1, u_2, ..., u_k\}$

$Span S$ is the vector set of all linear combinations of $u_1, u_2, ..., u_k$

$$Span S = \{c_1u_1 + c_2u_2 + ... + c_ku_k\ | for\ all\ c_1, c_2, ... , c_k\}
$$

If Vector set $V = Span S$
- *$S$ is a generating set for $V$* or *$S$ generates $V$*
- One way to describe a vector set with infinite components
- we call $V$ is *Space*
	
***Example 1***

Let $S_0 = \{ \begin{bmatrix} 0 \\ 0 \end{bmatrix}\} \quad Span\ S_0 = \{ \begin{bmatrix} 0 \\ 0 \end{bmatrix}\}$

***Example 2***

Let $S_1 = \{\begin{bmatrix} 1 \\ -1 \end{bmatrix}\} \quad Span\ S_1 = \{\begin{bmatrix} 1 \\ -1 \end{bmatrix}, \begin{bmatrix} 2 \\ -2 \end{bmatrix}, \begin{bmatrix} -1 \\ 1 \end{bmatrix}, \dots\}$
	![](https://i.imgur.com/xI9An2N.png)

:::success
If $S$ contains a non zero vector, then $Span\ S$ has infinitely vectors
:::

***Example 3***

Let $S_2 = \{\begin{bmatrix} 1 \\ -1 \end{bmatrix}, \begin{bmatrix} -2 \\ 2 \end{bmatrix}\}$, what is Span $S_2$ ?
	![](https://i.imgur.com/z0eKJvb.png)

$$Span S_1 = Span S_2
$$

:::success
Different number of vectors can generate the same space.
:::

***Example 4***

Let $S_3 = \{\begin{bmatrix} 1 \\ -1 \end{bmatrix}, \begin{bmatrix} -2 \\ 2 \end{bmatrix}\, \begin{bmatrix} 2 \\ 1 \end{bmatrix}\}$, what is Span $S_3$ ?
	
![](https://i.imgur.com/cZmCgIS.png)

---

### Span and System of Linear Equations
![](https://i.imgur.com/9JdLltB.png)

## Summary
![](https://i.imgur.com/RjBh2hu.png)


###### tags: `線性代數筆記`