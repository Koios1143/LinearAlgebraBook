# Coordinate System

- Each coordinate system is a *viewpoint* for vector representation
	- The same vector is represented differently in different coordinate systems
	- Different vectors can have the same representation in different coordinate systems

## Vector
Suppose we have a vector $\begin{bmatrix} 8 \\ 4\end{bmatrix}$

$$\begin{bmatrix} 8 \\ 4\end{bmatrix} = 8e_1 + 4e_2
$$

![](https://i.imgur.com/wRPRFwz.png)

then $\{e_1, e_2\}$ is a coordinate system

Suppose we have a new coordinate system $\{b_1, b_2\}$
$$b_1 = \begin{bmatrix} 1 \\ 1\end{bmatrix} \quad b_2 = \begin{bmatrix} -1 \\ 1\end{bmatrix}
$$

$$\begin{bmatrix} 8 \\ 4\end{bmatrix} = 6b_1 + (-2)b_2
$$

![](https://i.imgur.com/qfco1Ts.png)

---

In different coordinate, same vector will represent differently
![](https://i.imgur.com/AyNQPtH.png)

## Coordinate System
A vector set $\mathscr{B}$ can be considered as a coordinate system for $\mathscr{R}^n$ if
1. The vector set $\mathscr{B}$ spans $\mathscr{R}^n$
	
    Every vector should have representation
2. The vector set $\mathscr{B}$ is independent
	
    Every vector should have unique representation

:::success
$\mathscr{B}$ is a basis of $\mathscr{R}^n$
:::

### Proof unique
Let $\mathscr{B} = \{u_1, u_2, \dots, u_k\}$ a independent vector set

$a_1, a_2, \dots, a_k$ are scalars, such that $v = a_1u_1 + a_2u_2 + \dots + a_ku_k$

$v = a_1u_1 + a_2u_2 + \dots + a_ku_k$

$v = b_1u_1 + b_2u_2 + \dots + b_ku_k$

$\Rightarrow (a_1-b_1)u_1 + (a_2-b_2)u_2 + \dots + (a_k-b_k)u_k = 0$

Because $\mathscr{B}$ is independent, $Ax = 0$ have only one solution when $x$ is zero vector
Thus, $a_1 = b_1,\ a_2=b_2, \ \dots, \ a_k = b_k$

$\Rightarrow$ $v$ must be unique

---

- Let vector set $\mathscr{B} = \{u_1, u_2, \dots, u_n\}$ a basis for a subspace $\mathscr{R}^n$
	
    $\Rightarrow \mathscr{B}$ is a coordinate system
- For any $v$ in $\mathscr{R}^n$, there are unique scalars $c_1, c_2, \dots, c_n$ such that $v = c_1u_1 + c_2u_2 + \dots + c_nu_n$
	
    $\Rightarrow \mathscr{B}-$coordinate vector of $v = [v]_\mathscr{B} = \begin{bmatrix} c_1 \\ c_2 \\ \vdots \\ c_n \end{bmatrix} \in \mathscr{R}^n$

:::info
$v$ is a vector in Cartesian coordinate system $$\epsilon = \{e_1, e_2, \dots, e_n\}
$$
$[v]_\mathscr{B}$ is a vector in $\mathscr{B}-$ coordinate system
$$\mathscr{B} = \{u_1, u_2, \dots, u_n\}
$$
:::

## Transform coordinate system
### Other System $\to$ Cartesian
$$\mathscr{B} = \{\begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}, \begin{bmatrix} 1 \\ -1 \\ 1 \end{bmatrix}, \begin{bmatrix} 1 \\ 2 \\ 2 \end{bmatrix}\} \quad [v]_{\mathscr{B}} = \begin{bmatrix} 3 \\ 6 \\ -2 \end{bmatrix} \\
v = 3\begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix} + 6\begin{bmatrix} 1 \\ -1 \\ 1 \end{bmatrix} - 2\begin{bmatrix} 1 \\ 2 \\ 2 \end{bmatrix}\ = \begin{bmatrix} 7 \\ -7 \\ 5 \end{bmatrix}
$$

Let vector set $\mathscr{B} = \{u_1, u_2, \dots, u_n\}$ be a basis for a subspace $\mathscr{R}^n$

Matrix $B = \begin{bmatrix} u_1 & u_2 & \dots & u_n \end{bmatrix}$

$$[v]_\mathscr{B} = \begin{bmatrix} c_1 \\ c_2 \\ \vdots \\ c_n \end{bmatrix}
$$
$$v = c_1u_1 + c_2u_2 + \dots + c_nu_n = B[v]_\mathscr{B}
$$

### Cartesian $\to$ Other System
$$v = \begin{bmatrix} 1 \\ -4 \\ 4 \end{bmatrix} \quad \mathscr{B} = \{\begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}, \begin{bmatrix} 1 \\ -1 \\ 1 \end{bmatrix}, \begin{bmatrix} 1 \\ 2 \\ 2 \end{bmatrix}\}\\
c_1\begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix} + c_2\begin{bmatrix} 1 \\ -1 \\ 1 \end{bmatrix} + c_3\begin{bmatrix} 1 \\ 2 \\ 2 \end{bmatrix} = \begin{bmatrix} 1 \\ -4 \\ 4 \end{bmatrix}\\
B = \begin{bmatrix} 1 & 1 & 1 \\ 1 & -1 & 2 \\ 1 & 1 & 2 \end{bmatrix}\\
B[v]_{\mathscr{B}} = v \Rightarrow [v]_{\mathscr{B}} = B^{-1}v = \begin{bmatrix} -6 \\ 4 \\ 3 \end{bmatrix}
$$

:::success
Is $B$ always invertible? (O)

According to *Invertible* lecture before, we know if a matrix are linear independent, then it is invertible

And our coordinate system **must be independent**
:::

---

:::info
Let $\mathscr{B} = \{b_1, b_2, \dots, b_n\}$ be a basis of $\mathscr{R}^n$

$\Rightarrow [b_i]_\mathscr{B} = e_i$
:::

## Changing Coordinate
### Ellipse
> If we want to rotate a ellipse 45 degree
> 
> $\to$ just use another coordinate system

![](https://i.imgur.com/o0WO8He.png)

Let a new coordinate system $\mathscr{B} = \{\begin{bmatrix} \frac{\sqrt{2}}{2} \\ \frac{\sqrt{2}}{2} \end{bmatrix},  \begin{bmatrix} -\frac{\sqrt{2}}{2} \\ \frac{\sqrt{2}}{2} \end{bmatrix}\}$

$$v = \begin{bmatrix} x \\ y\end{bmatrix}, [v]_\mathscr{B} = \begin{bmatrix} x' \\ y' \end{bmatrix} = B^{-1}v
$$

$$\frac{(x')^2}{3^2} + \frac{(y')^2}{2^2} = 1 \to \frac{(\frac{\sqrt{2}}{2}x + \frac{\sqrt{2}}{2}y)^2}{3^2} + \frac{(-\frac{\sqrt{2}}{2}x + \frac{\sqrt{2}}{2}y)^2}{2^2} = 1
$$

![](https://i.imgur.com/UyQ6nLd.png)

### Hyperbola
![](https://i.imgur.com/RZqSvno.png)

$$B = \begin{bmatrix} \frac{\sqrt{3}}{2} & -\frac{1}{2} \\ \frac{1}{2} & \frac{\sqrt{3}}{2} \end{bmatrix}, v = \begin{bmatrix} x \\ y\end{bmatrix}, [v]_\mathscr{B} = \begin{bmatrix} x' \\ y' \end{bmatrix}, v = B[v]_\mathscr{B}
$$
$$\begin{bmatrix} x \\ y\end{bmatrix} = \begin{bmatrix} \frac{\sqrt{3}}{2} & -\frac{1}{2} \\ \frac{1}{2} & \frac{\sqrt{3}}{2} \end{bmatrix}\begin{bmatrix} x' \\ y' \end{bmatrix}\\
\Rightarrow x'y'=3
$$

## Summary
![](https://i.imgur.com/7QfdgTV.png)


###### tags: `線性代數筆記`