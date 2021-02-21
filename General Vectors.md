# General Vectors

Many things can be considered as ***vectors***
- E.g. a function can be regarded as a vector

We can apply the concept we learned on those ***vectors***

## Are they vectors?
- A matrix
	
    $A = \begin{bmatrix} 1 & 2 \\ 3 & 4 \end{bmatrix} \Rightarrow \begin{bmatrix} 1 \\ 2 \\ 3 \\ 4 \end{bmatrix}$
- A linear transform
- A polynomial
	
    $p(x) = a_0 + a_1x + \dots + a_nx^n \Rightarrow \begin{bmatrix} a_0 \\ a_1 \\ \vdots \\ a_n \end{bmatrix}$
- Any function
	
    $f(t) = e^t \Rightarrow v = \begin{bmatrix} \vdots \\ ? \\ \vdots \end{bmatrix}$ (infinity dimension)

## What is a vector?
If a set of objects $V$ is a ***vector space***, then the objects are ***vectors***

### Vector space
There are operations called ***addition*** and ***scalar multiplication***

$u, v$ and $w$ are in $V$, and $a$ and $b$ are scalars.$u+v$ and $au$ are unique elements of $V$

A vector space needs follow these axioms
- $u + v = v + u$
- $(u + v) + w = u + (v + w)$
- There is a ***zero vector*** $0$ in $V$, such that $u + 0 = u$ (Unique)
- There is $-u$ in $V$, such that $u + (-u) = 0$
- $1u = u$
- $(ab)u = a(bu)$
- $a(u + v) = au + av$
- $(a + b)u = au + bu$

For example $\mathscr{R}^n$ is a vector space

## Objects in Different Vector Space
Objects can be represent in different vector spaces

***Example 1***
![](https://i.imgur.com/fjfOxsy.png)

***Example 2***
![](https://i.imgur.com/EksI7oM.png)

## Subspace
### Review
A vector set $V$ is called a subspace if it has the following three properties
1. The zero vector $0$ belongs to $V$
2. If $u$ and $w$ belong to $V$, then $u + w$ belongs to $V$
	
    Closed under (vector) addition
3. If $u$ belongs to $V$, and $c$ is a scalar, then $cu$ belongs to $V$
	
    Closed under scalar multiplication

### Are they subspaces?
- All the functions pass $0$ at $t_0$ (O)
- All the $n \times n$ matrices whose trace equal to zero (O)
- All the matrices of the form $\begin{bmatrix} a & a+b \\ b & 0 \end{bmatrix}$ (O)
- All the continuous function (O)
- All the polynomials with degree $n$ (X)
- All the polynomials with degree less than or equal to $n$ (O)

## Linear Combination and Span
:::info
$P$: all polynomials

$P_n$: all polynomials with degree less than or equal to $n$
:::

- Matrices
	
    $S = \{\begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}, \begin{bmatrix} 0 & 1 \\ 0 & 0 \end{bmatrix}, \begin{bmatrix} 0 & 0 \\ 1 & 0 \end{bmatrix}\}$
	
    Linear combination with coefficient $a, b, c$
	$$a\begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix} + b\begin{bmatrix} 0 & 1 \\ 0 & 0 \end{bmatrix} + c\begin{bmatrix} 0 & 0 \\ 1 & 0 \end{bmatrix} = \begin{bmatrix} a & b \\ c & -a \end{bmatrix}
	$$
	
    What is $Span\ S$?
	
    All $2 \times 2$ matrices whose trace equal to zero

- Polynomials
	$$S = \{1, x, x^2, x^3\}
	$$
	
    Is $f(x) = 2+3x-x^2$ linear combination of the **vectors** in $S$?
	$$f(x) = 2 \times 1 + 3 \times x + (-1) \times x^2 + 0 \times x^3
	$$
	
    $Span\{1, x, x^2, x^3\} = P_3$
	
    $P_3$ is the set of all polynomials that degree less than 3

## Linear Transformation
A mapping (function) $T$ is called linear if for all **vectors**, $u$ and $v$ and scalar $c$
- Preserving Addition
- Preserving Multiplication

> Is matrix Transpose linear ? (O)
> Input: $m \times n$ matrices, output: $n \times m$ matrices

***Derivative*** and ***Integral*** are linear transformation, also, they are function's function

## Null Space & Range
- Null Space
	
    The null space of $T$ us the set of all vectors such that $T(v) = 0$
- Range
	
    The range of $T$ is the set of all image of $T$
	
    That is, the set of all vectors $T(v)$ for all $v$ in the domain

## One-to-one & Onto
- $U: \mathscr{M}_{m \times n} \rightarrow \mathscr{M}_{n \times m}$ define by $U(A) = A^T$
	- Is $U$ one-to-one? (O)
	- Is $U$ onto? (O)
- $D: \mathscr{P}_3 \rightarrow \mathscr{P}_3$ define by $D(f) = f'$
	- Is $D$ one-to-one (X)
	- Is $D$ onto? (X)

## Isomorphism
> Isomorphism means the same or similar in structure or shape

- Biology
	
    They all have wings
	![](https://i.imgur.com/1ayfeHR.png)
- Graph Theory
	![](https://i.imgur.com/WLtqZZZ.png)
- Chemistry
	
    different Molecular Structure, but same Crystal structure
	![](https://i.imgur.com/OZqu2ja.png)

> How about Isomorphism in linear algebra?

Let $V$ and $W$ be vector space
A linear transformation $T: V \rightarrow W$ is called an isomorphism if is is ***one-to-one*** and ***onto***

That is, $T$ is ***invertible***

![](https://i.imgur.com/ZxvHyC5.png)

***Example 1***
$$U: \mathscr{M}_{m \times n} \rightarrow \mathscr{M}_{n \times m} \texttt{ define by } U(A) = A^T
$$

***Example 2***
$$T: \mathscr{P}_2 \rightarrow \mathscr{R}^3
$$

## Basis
A basis for subspace $V$ is a linear independent generation set of $V$

### Independent
***Example 1***

$S = \{x^2 - 3x + 2, 3x^2 - 5x, 2x-3\}$ is a subset of $\mathscr{P}_2$

$$3(x^2 - 3x + 2) + (-1)(3x^2 - 5x) + 2(2x - 3) = 0
$$

$\Rightarrow$ not independent

***Example 2***

$S \{\begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}, \begin{bmatrix} 0 & 1 \\ 0 & 0 \end{bmatrix}, \begin{bmatrix} 0 & 0 \\ 1 & 0 \end{bmatrix}\}$ is a subset of $2 \times 2$ matrices

$$a \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix} + b\begin{bmatrix} 0 & 1 \\ 0 & 0 \end{bmatrix} + c\begin{bmatrix} 0 & 0 \\ 1 & 0 \end{bmatrix} = \begin{bmatrix} a & b \\ c & -a \end{bmatrix} = \begin{bmatrix} 0 & 0 \\ 0 & 0 \end{bmatrix}
$$

$\Rightarrow$ independent

### Basis
***Example 1***

For the subset of all $2 \times 2$ matrices, the basis is
$$S = \{\begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix}, \begin{bmatrix} 0 & 1 \\ 0 & 0 \end{bmatrix}, \begin{bmatrix} 0 & 0 \\ 1 & 0 \end{bmatrix}, \begin{bmatrix} 0 & 0 \\ 0 & 1 \end{bmatrix}\}
$$

***Example 2***

$S = \{1, x, x^2, \dots, x^n, \dots\}$ is a basis of $\mathscr{P}$

### Vector Representation of Object
***Coordinate Transformation***

We have a vector $v$ on subspace $V$

we can represent $v$ in other coordinate system by linear combination of basis $V$

![](https://i.imgur.com/6mzszuK.png)

$\mathscr{P}_n$:
- Basis
	
    $\{1, x, x^2, \dots, x^n\}$

$$p(x) = a_0 + a_1x + \dots + a_nx^n \Rightarrow \begin{bmatrix} a_0 \\ a_1 \\ \vdots \\ a_n \end{bmatrix}
$$

### Matrix Representation of Linear Operator
For example: ***derivative***

We have already know derivative is a lienar system, then it must have a transform matrix

We can figure out what the matrix looks like by inputing standard vectors

![](https://i.imgur.com/hXoLfwd.png)

So, if we want to do derivative, we can transfer the polynomial into vector, and multiply by the matrix above

![](https://i.imgur.com/jHtuZds.png)

:::success
Derivative matrix in polynomial is ***non-invertible***

***Differential is irreversible*** in polynomial
:::

---

Another example

$D$ (derivative): Function set $F$ $\rightarrow$ Function set $F$

Basis of $F$ is $\{e^tcos\ t, e^tsin\ t\}$

![](https://i.imgur.com/p6q6sZ5.png)

We can figure out this matrix is invertible, then we can easily find out Antiderivative matrix

![](https://i.imgur.com/PVzkZQm.png)

## Eigenvalue & Eigenvector
- Consider Derivative
	- Is $f(t) = e^{at}$ an eigenvector of derivative? (O)
		
        $f(t)' = ae^{at}$
		
        $e^{ae}$ is the eigenvector
	- What is the eigenvalue?
		
        $a$ is the eigenvalue
	
	:::success
	Every ***Real number*** is an eigenvalue of derivative
	:::
- Consider Transpose
	- Is $\lambda = 1$ an eigenvalue? (O)
		
        When matrix is a Symmetric matrix
	- Is $\lambda = -1$ an eigenvalue? (O)
		
        When matrix is a Skew-symmetric matrix
	- $2 \times 2$ matrices
		1. Find out the transform matrix
			![](https://i.imgur.com/rZgMKnL.png)
		2. Find out the characteristic polunomial of the matrix
			![](https://i.imgur.com/dSR0uqt.png)
		3. Get eigenvalues
			
            $\lambda = 1 \texttt{ or } -1$

## Inner Product
![](https://i.imgur.com/qL0BlsW.png)

In general, Inner Product is not equal to dot product!

Dot product is a special case in Inner Product

For any vectors $u, v$ and $w$ and any scalar $a$, the following axioms holds
1. $\langle u, u \rangle > 0$ if $u \neq 0$
2. $\langle u, v \rangle = \langle v, u \rangle$
3. $\langle u+v, w \rangle = \langle u, w \rangle + \langle v, w \rangle$
4. $\langle au, v \rangle = a \langle u, v \rangle$

:::success
Norm in general
$$||v|| = \sqrt{\langle v, v \rangle}
$$
:::

:::success
Orthogonal in general
$$\langle v, u \rangle = 0
$$
:::

***For example: Forbenius inner product***
$$\langle A, B \rangle = trace(AB^T) = trace(BA^T)
$$

In other words, multiply the corresponding numbers in the two matrices

![](https://i.imgur.com/y9B18aU.png)

$$A = \begin{bmatrix} a & b \\ c & d \end{bmatrix} \quad ||A|| = \sqrt{a^2 + b^2 + c^2 + d^2}
$$

---

Inner Product for general functions

$$\langle g, h \rangle = \int_{-1}^{1}{g(x)h(x)\ dx} \quad (-1 \leq x \leq 1)
$$

### Orthogonal/Orthonormal Basis
Let $u$ be any vector, and $w$ is the orthogonal projection of $u$ on subspace $W$

- Let $S = \{v_1, v_2, \dots, v_k\}$ be an orthogonal basis of $W$
	$$w = c_1v_1 + c_2v_2 + \dots + c_kv_k\\
	c_1 = \frac{\langle u, v_1 \rangle}{||v_1||^2} \quad c_2 = \frac{\langle u, v_2 \rangle}{||v_2||^2}, \dots, c_k = \frac{\langle u, v_k \rangle}{||v_k||^2}
	$$
- Let $S = \{v_1, v_2, \dots, v_k\}$ be an orthonormal projection of $u$ on subspace $W$
	$$w = c_1v_1 + c_2v_2 + \dots + c_kv_k\\
	c_1 = \langle u, v_1 \rangle \quad c_2 = \langle u, v_2 \rangle, \dots, c_k = \langle u, v_k \rangle
	$$

***Gram-Schmidt Process***

Let $\{u_1, u_2, \dots, u_k\}$ be a basis of a subspace $V$. How to transform it into an orthogonal basis $\{v_1, v_2, \dots, v_k\}$?

$$v_1 = u_1\\
v_2 = u_2 - \frac{\langle u_2, v_1 \rangle}{||v_1||^2}v_1\\
v_3 = u_3 - \frac{\langle u_3, v_1 \rangle}{||v_1||^2}v_1 - \frac{\langle u_3, v_2 \rangle}{||v_2||^2}v_2\\
\vdots\\
v_k = u_k - \frac{\langle u_k, v_1 \rangle}{||v_1||^2}v_1 - \frac{\langle u_k, v_2 \rangle}{||v_2||^2}v_2 - \dots - \frac{\langle u_k, v_{k-1} \rangle}{||v_{k-1}||^2}v_{k-1}
$$

Then, $\{v_1, v_2, \dots, v_k\}$ is an orthogonal basis for $W$

---

Find orthogonal/orthonormal basis for $\mathscr{P}_2$

1. Define an inner product of $\mathscr{P}_2$
	$$\langle f(x), g(x) \rangle = \int_{-1}^{1}{f(t)g(t)\ dt}
	$$
2. Find a basis
	$$\{1, x, x^2\}
	$$
3. Get an orthogonal basis
	$$\{1, x, x^2\} \Rightarrow v_1, v_2, v_3\\
	v_1 = u_1 = 1\\
	v_2 = u_2 - \frac{\langle u_2, v_1 \rangle}{||v_1||^2}v_1 = x - \frac{\int_{-1}^{1}{t \cdot 1\ dt}}{\int_{-1}^{1}{1^2\ dt}}(1) = x - 0 \cdot 1 = x\\
	v_3 = u_3 - \frac{\langle u_3, v_1 \rangle}{||v_1||^2}v_1 - \frac{\langle u_3, v_2 \rangle}{||v_2||^2}v_2 = x^2 - \frac{1}{3}\\
	\Rightarrow \{1, x, x^2 - \frac{1}{3}\}
	$$
4. Get an orthonormal basis
	$$||v_1|| = \sqrt{\int_{-1}^{1}{1^2\ dx}} = \sqrt{2}\\
	||v_2|| = \sqrt{\int_{-1}^{1}{x^2\ dx}} = \sqrt{\frac{2}{3}}\\
	||v_3|| = \sqrt{\int_{-1}^{1}{(x^2 - \frac{1}{3})^2\ dx}} = \sqrt{\frac{8}{45}}\\
	\Rightarrow \{\frac{1}{\sqrt{2}}, \sqrt{\frac{3}{2}}x, \sqrt{\frac{45}{8}}(x^2 - \frac{1}{3})\}
	$$

	![](https://i.imgur.com/wcwWi6r.png)


###### tags: `線性代數筆記`