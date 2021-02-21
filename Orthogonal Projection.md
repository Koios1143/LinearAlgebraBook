# Orthogonal Projection
We have a subspace $W$, given a vector $u$, we can disassemble $u$ into two vector $w \in W$ and $z \in W^{\perp}$

And the operator of find out $w$ by $u$ is called orthogonal projection

![](https://i.imgur.com/YQk4L2W.png)

We can denote $U_W(u)$ to represent we want to do orthogonal projection on subspace $W$ by vector $u$

> Is $U_W()$ a linear function? (O)

$$u = w + z\\
ku = kw + kz\\
$$

$$u_1 = w_1 + z_1\\
u_2 = w_2 + z_2\\\
u_1 + u_2 = (w_1 + w_2) + (z_1 + z_2)
$$

## Properties
- $w$ in subspace $W$ is *closet* to vector $u$
- $Z$ is always orthogonal to all vectors in $W$

![](https://i.imgur.com/g4zGyiL.png)

***Proof Closet***

![](https://i.imgur.com/fRIS5KC.png)

$\forall w, w', w-w' \in W\\
\Rightarrow (u-w) \cdot (w-w') = 0\\
\Rightarrow ||u-w||^2 = ||(u-w) + (w-w')||^2 = ||u-w||^2 + ||w-w'||^2 + 2 \times 0 \geq ||u-w||^2$

## Orthogonal Projection Matrix
Orthogonal Projection operator is linear $\Rightarrow$ It has standard matrix $\Rightarrow$ Orthogonal Projection Matrix $P_W$

![](https://i.imgur.com/yZr1sr2.png)

---

Assume we are consider orthogonal projection of a vector on a line

![](https://i.imgur.com/wnVhTlC.png)

:::info
$v$: any vector

$u$: any nonzero vector on $\mathscr{L}$

$w$: orthogonal projection of $v$ onto $\mathscr{L}$, $w = cu$

$z$: $v-w$
:::

$$(v-w) \cdot u = (v - cu) \cdot u = v \cdot u - c||u||^2\\
c = \frac{v \cdot u}{||u||^2} \quad w = cu = \frac{v \cdot u}{||u||^2}u\\
||z|| = ||v-w|| = ||v-\frac{v \cdot u}{||u||^2}u
$$

---

Let $C$ be an $n \times k$ matrix whose columns form a basis for a subspace $W$, $dimW = k$

$$P_W = C(C^TC)^{-1}C^T
$$

***Proof***

Let $u \in \mathscr{R}^n$ and $w = U_W(u)$

Since $W = Col\ C, w = Cb$ for some $b \in \mathscr{R}^k$ and $u-w \in W^{\perp}$

$$\Rightarrow 0 = C^T(u-w) = C^Tu - C^Tw = C^Tu - C^TCb\\
\Rightarrow C^Tu = C^TCb\\
\Rightarrow b = (C^TC)^{-1}C^Tu \texttt{ and } w = C(C^TC)^{-1}C^Tu \texttt{ as } C^TC \texttt{ is invertible}
$$

> If $C$ is independent, does $C^TC$ is always invertible?

***Proof***

Suppose $C^TCb = 0$ for some $b$

$$\Rightarrow b^TC^TCb = (Cb)^TCb = (Cb) \cdot (Cb) = ||Cb||^2 = 0 \\
\Rightarrow Cb = 0 \Rightarrow b = 0
$$

Since $C$ has Linear Independent columns, $C^TC$ is invertible

---

:::info
For Example

Let $W$ be the 2-dimension subspace of $\mathscr{R}^3$ with equation $x_1 - x_2 + 2x_3 = 0$

$W$ has a basis $\{\begin{bmatrix} 1 \\ 1 \\ 0 \end{bmatrix}, \begin{bmatrix} -2 \\ 0 \\ 1 \end{bmatrix}\} \quad C = \begin{bmatrix} 1 & -2 \\ 1 & 0 \\ 0 & 1 \end{bmatrix}$

$P_W = \frac{1}{6}\begin{bmatrix} 5 & 1 & -2 \\ 1 & 5 & 2 \\ -2 & 2 & 2 \end{bmatrix} \quad P_W\begin{bmatrix} 1 \\ 3 \\ 4 \end{bmatrix} = \begin{bmatrix} 0 \\ 4 \\ 2 \end{bmatrix}$
:::

## Application of Orthogonal Projection
Suppose $Ax = b$ is an inconsistent system of linear equations, that is, $b$ is not in the column space of $A$, can we find a vector $z$ minimizing $||Az-b||$ ?

$\Rightarrow$ Yes, the answer is the orthogonal projection of vector $b$ on subspace $W$
![](https://i.imgur.com/SvJwedj.png)

### Least Square Approximation
We have some data, We want to find a straight line so that the square of the distance between the point and the line will be the smallest (***Regression***)

![](https://i.imgur.com/l7bD8EE.png)

How to find out the line?

Assume the line is $y = a_0 + a_1x$

![](https://i.imgur.com/xZeZ6Le.png)

Let $e = \begin{bmatrix} y_1-(a_0+a_1x_1) \\ y_2-(a_0+a_1x_2) \\ \vdots \\ y_n-(a_0+a_1x_n) \end{bmatrix}$

$E = [y_1 - (a_0+a_1x_1)]^2 + [y_2 - (a_0+a_1x_2)]^2 + \dots + [y_n - (a_0+a_1x_n)]^2 = ||e||^2$

find $E_{min}$

$y \triangleq \begin{bmatrix} y_1 \\ y_2 \\ \vdots \\ y_n \end{bmatrix} \quad v_1 \triangleq \begin{bmatrix} 1 \\ 1 \\ \vdots \\ 1 \end{bmatrix} \quad v_2 \triangleq \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix}$

$\Rightarrow e = y - a_0v_1 - a_1v_2$

$C \triangleq \begin{bmatrix} v_1 & v_2\end{bmatrix} \quad a = \begin{bmatrix} a_0 \\ a_1 \end{bmatrix}$

$\Rightarrow e = y-Ca$

$\Rightarrow E = ||y-(a_0v_1 + a_1v_2)||^2 = ||y-Ca||^2 = ||Ca - y||^2$

Find $a$ minimizing

Remember, we have no solution such that $Ca = y$

$\mathscr{B} = \{v_1, v_2\}$, and $v_1$ and $v_2$ are Linearly independent

$Ca$ is the orthogonal projection of $y$ on $W = Span\ \mathscr{B}$, find $a$ such that $Ca = P_Wy$

$$\begin{bmatrix} a_0 \\ a_1 \end{bmatrix} = (C^TC)^{-1}C^Ty
$$

---

***Example 1***


| Rough weight $x_i$ (in pounds) | Finished weight $y_i$ (in pounds) |
| ------------------------------ | --------------------------------- |
| 2.60                           | 2.00                              |
| 2.72                           | 2.10                              |
| 2.75                           | 2.10                              |
| 2.67                           | 2.03                              |
| 2.68                           | 2.04                              |

$$C = \begin{bmatrix} 1 & 2.60 \\ 1 & 2.72 \\ 1 & 2.75 \\ 1 & 2.67 \\ 1 & 2.68 \end{bmatrix} \quad y = \begin{bmatrix} 2.00 \\ 2.10 \\ 2.10 \\ 2.03 \\ 2.04 \end{bmatrix} \\
\begin{bmatrix} a_0 \\ a_1 \end{bmatrix} = (C^TC)^{-1}C^Ty \approx \begin{bmatrix} 0.056 \\ 0.745 \end{bmatrix} \\
\Rightarrow y = 0.056 + 0.745x
$$

---

***Example 2***

We can not only predict straight line, but also curve

![](https://i.imgur.com/9bSjLTA.png)

$$v_1 = \begin{bmatrix} 1 \\ 1 \\ \vdots \\ 1 \end{bmatrix} \quad v_2 = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_n \end{bmatrix} \quad v_3 = \begin{bmatrix} x_1^2 \\ x_2^2 \\ \vdots \\ x_n^2 \end{bmatrix} \quad e = \begin{bmatrix} y_1-(a_0+a_1x_1+a_2x_{1}^{2}) \\ y_2-(a_0+a_1x_2+a_2x_{2}^{2}) \\ \vdots \\ y_n-(a_0+a_1x_n+a_2x_{n}^{2}) \end{bmatrix} \\ C = \begin{bmatrix} v_1 & v_2 & v_3 \end{bmatrix}
$$

Find $a_0, a_1, a_2, min(E)$, $E = ||e||^2$

$$\begin{bmatrix} a_0 \\ a_1 \\ a_2 \end{bmatrix} = (C^TC)^{-1}C^Ty
$$

![](https://i.imgur.com/2mEVJjX.png)

$$C = \begin{bmatrix} 1 & 0 & 0 \\ 1 & 1 & 1 \\ 1 & 2 & 4 \\ 1 & 3 & 9 \\ 1 & 3.5 & 12.25 \end{bmatrix} \quad y = \begin{bmatrix} 100 \\ 118 \\ 92 \\ 48 \\ 7 \end{bmatrix} \\ 
\Rightarrow y = 101.00 + 29.77x - 16.11x^2
$$

###### tags: `線性代數筆記`