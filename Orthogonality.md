# Orthogonality

## Norm & Distance
- ***Norm***
	
    Norn of vector $v$ is the length of $v$
	- Denoted $||v|| = \sqrt{v_1^2 + v_2^2 + \dots + v_n^2}$
	:::success
	In General Definition, Norm is
	$$||v||_p = (\sum^n_{i=1}{|v_i|^p})^{1/p}
	$$
	:::

- ***Distance***
	
    The distance between two vectors $u$ and $v$ us defined by $||v-u||$

## Dot Product & Orthogonal
- ***Dot product***
	
    dot product of $u$ and $v$ is $u \cdot v = u_1v_1 + u_2v_2 + \dots + u_nv_n \\ = \begin{bmatrix} u_1 & u_2 & \dots & u_n \end{bmatrix}\begin{bmatrix} v_1 \\ v_2 \\ \vdots \\ v_n \end{bmatrix} = u^Tv$

- ***Orthogonal***
	
    $u$ and $v$ are orthogonal if $u \cdot v = 0$
	:::info
	Orthofonal is actually **perpendicular**
	:::
	:::info
	zero vector is orthogonal to every vector
	:::

## More about Dot Product
Let $u$ and $v$ be vectors, $A$ be a matrix, and $c$ be a scalar

- $u \cdot u = ||u||^2$
- $u \cdot u = 0$ if and only if $u = 0$
- $u \cdot v = v \cdot u$
- $u \cdot (v+w) = u \cdot v + u \cdot w$
- $(v + w) \cdot u = v \cdot u + w \cdot u$
- $(cu) \cdot v = c(u \cdot v) = u \cdot (cv)$
- $||cu|| = |c|||u||$
- $Au \cdot v = (Au)^Tv = u^T(A^Tv) = u \cdot A^Tv$

## Example
$||2u+3v||^2\\ = (2u+3v) \cdot (2u+3v)\\ = 2u \dot (2u+3v) + 3v \cdot (2u + 3v)\\ = 2u \cdot 2u + 2u \cdot 3v + 3v \cdot 2u + 3v \cdot 3v \\ = ||2u||^2 + ||3v||^2 + 12(u \cdot v)\\ = 4||u||^2 + 9||v||^2 + 12(u \cdot v)$

## Pythagorean Theorem
> $u$ and $v$ are orthogonal $\Leftrightarrow$ $||u+v||^2 = ||u||^2 + ||v||^2$

***Proof***

$||u+v||^2 = ||u||^2 + 2u \cdot v + ||v||^2$

$u \cdot v = 0 \Rightarrow ||u+v||^2 = ||u||^2 + ||v||^2$

> The diagonals of a parallelogram are orthogonal $\Leftrightarrow$ The parallelogram is a rhombus

***Proof***

$(u+v) \cdot (u-v) = 0 \\ = ||u||^2 - ||v||^2 \Rightarrow ||u|| = ||v||$

## Triangle Inequality
For any vectors $u$ and $v$

$$||u+v|| \leq ||u|| + ||v||
$$

***Proof***

$||u+v||^2 = ||u||^2 + 2u \cdot v + ||v||^2 \\ \leq ||u||^2 + 2|u \cdot v| + ||v||^2 \\ \leq ||u||^2 + 2||u|| \cdot ||v|| + ||v||^2 \quad \texttt{By Cauchy-Schearz Inequality} \\ \leq (||u||+||v||)^2 \\ \Rightarrow ||u+v|| \leq ||u|| + ||v||$

***Proof Cauchy-Schearz Inequality***

Let $u$ and $v$ are vectors

Let $w = \frac{u}{||u||} \quad z = \frac{v}{||v||}$

- $||w+z||^2 \geq 0 \\ ||w||^2 + 2w \cdot z + ||z||^2 \geq 0 \\ 2w \cdot z \geq -2 \\ w \cdot z \geq -1$

- $||w-z||^2 \geq 0 \\ ||w||^2 - 2w \cdot z + ||z||^2 \geq 0 \\ -2w \cdot z \geq -2 \\ w \cdot z \leq 1$

$\Rightarrow ||u||||v|| \geq u \cdot v \geq -||u||||v||$

## Orthogonal Complement
The orthogonal complement of a nonempty vector set $S$ is denoted as $S^{\perp}$

$S^{\perp}$ is the set of vectors that are orthogonal to every vector in $S$

$$S^{\perp} = \{v:v \cdot u = 0, \forall u \in S \}
$$

For example in 2-D

![](https://i.imgur.com/DtvfXY4.png)

More Examples
- $S = \mathscr{R}^n \Rightarrow S^{\perp} = \{0\}$
- $S = \{0\} \Rightarrow S^{\perp} = \mathscr{R}^n$
- $W = \{\begin{bmatrix} w_1 \\ w_2 \\ 0 \end{bmatrix} | w_1, w_2 \in \mathscr{R} \} \Rightarrow W^{\perp} = \{\begin{bmatrix} 0 \\ 0 \\ v_3 \end{bmatrix} | v_3 \in \mathscr{R} \}$

### Properties
- $S^{\perp}$ is always a subspace
	
    But $S$ is not always a subspace
- For any nonempty vector set $S$, $Span(S)^{\perp} = S^{\perp}$
- Let $W$ be a subspace, and $B$ be a basis of $W$ $\Rightarrow B^{\perp} = W^{\perp}$
- $S \cap S^{\perp} = \vec{0}$

:::info
For example

For $W = Span(u_1, u_2)$ where $u_1 = \begin{bmatrix} 1 \\ 1 \\ -1 \\ 4 \end{bmatrix}$ and $u_2 = \begin{bmatrix} 1 \\ -1 \\ 1 \\ 2 \end{bmatrix}$

$v \in W^{\perp}$ if and only if $u_1 \cdot v = u_2 \cdot v = 0$

i.e., $v = \begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix}$ satisfies

$$\begin{cases} x_1 + x_2 - x_3 + 4x_4 = 0 \\ x_1 - x_2 + x_3 + 2x_4 = 0\end{cases} \Leftrightarrow \begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix} = \begin{bmatrix} -3x_4 \\ x_3-x_4 \\ x_3 \\ x_4 \end{bmatrix} = x_3 \begin{bmatrix} 0 \\ 1 \\ 1 \\ 0 \end{bmatrix} + x_4 \begin{bmatrix} -3 \\ -1 \\ 0 \\ 1 \end{bmatrix} \\ \Leftrightarrow B = \{\begin{bmatrix} 0 \\ 1 \\ 1 \\ 0 \end{bmatrix}, \begin{bmatrix} -3 \\ -1 \\ 0 \\ 1 \end{bmatrix} \} \texttt{ is a basis for } W^{\perp}
$$

$A = \begin{bmatrix} 1 & 1 & -1 & 4 \\ 1 & -1 & 1 & 2 \end{bmatrix}$

$W^{\perp} = Ax = 0 = Null(A)$
:::

- $(Row\ A)^{\perp} = Null\ A$
	$$\begin{bmatrix} ── & ── & ── & ── \\ ── & ── & ── & ── \\ ── & ── & ── & ── \end{bmatrix}\begin{bmatrix} | \\ | \\ | \\ | \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0 \end{bmatrix}
	$$
- $(Col\ A)^{\perp} = (Row\ A^{T})^{\perp} =  Null\ A^{T}$
- For any subspace $W$ of $\mathscr{R}^n$ $dimW + dimW^{\perp} = n$
	
    Assume we have a basis of $W$ $B$, 	space of $Col\ B$ is $W$
	
    Assume subspace of $B$'s dimension is $k$, then $B$ is a $n \times k$ matrix
	
	$Col\ B^{\perp} = Null\ B^{T}$, $B^T$ is a $k \times n$ matrix
	
    $Nullity(B) = dim(Null\ B)$
	
    If we want to know $Nullity(B)$, we only need to know $Rank\ B^T$
	
    $$n - Rank\ B^T = Nullity(B) = n - Rank\ B = n-k
	$$

	$\Rightarrow dimW + dimW^{\perp} = k + (n-k) = n$

	:::success
	***Unique***
	
    For any subspace $W$ of $\mathscr{R}^n$ $dimW + dimW^{\perp} = n$
	
    Basis of $W$ is $\{w_1, w_2, \dots, w_k\}$
	
    Basis of $W^{\perp}$ is $\{z_1, z_2, \dots, z_{n-k}\}$
	
    If these two basis can combination to basis for $\mathscr{R}^n$
	
    then, for every vector $u \in \mathscr{R}^n$ $u = w + z$
	:::

###### tags: `線性代數筆記`