# Subspace

- A vector set $V$ is called a subspace if it has the follwing three properties:
	1. The zero vector $0$ belongs to $V$
	2. If $u$ and $w$ belong to $V$, then $u+w$ belongs to $V$
		
        Closed under (vector) addition
	3. If $u$ belongs to $V$, and $c$ is a scalar, then $cu$ belongs to $V$
		
        Closed under scalar multiplication
	:::info
	2 + 3 is linear combination
	:::

> $\phi$ is not subspace

## Examples
1. $v = \{cw | c \in \mathscr{R} \}$ (O)
2. $S_1 = \{\begin{bmatrix} w_1 \\ w_2\end{bmatrix} \in \mathscr{R}^2 : w_1^2 = w_2^2 \}$ (X)
3. $S_2 = \{\begin{bmatrix} w_1 \\ w_2\end{bmatrix} \in \mathscr{R}^2 : w_1 \geq 0, w_2 \geq 0 \}$ (X)
4. $\mathscr{R}^n$ (O)
5. $\{0\}$ (O)
	zero subspace

## Subspace V.S. Span
- The Span of a vector set is a subspace
	Let $S = \{w_1, w_2, \dots, w_k\}$, $V = Span\ S$ 
	1. $0 \in V$
	2. $u, v \in V, u+v \in V$
	3. $u \in V, cu \in V$

![](https://i.imgur.com/LtdJ3lz.png)

## Null space
- The null space of a matrix $A$ is the solution set of $Ax = 0$. It is denoted as null $A$.
	
    $Null\ A = \{v \in \mathscr{R}^n : Av = 0\}$
	
    The solution set of the homogeneous linear equations $Av = 0$

- Null A is sub space

## Column space
- Column space of matrix $A$ is the span of its columns. It it denoted as $Col\ A$
	
    $A \in \mathscr{R}^{m \times n} => Col\ A = \{Av : v \in \mathscr{R}^n\}$

:::success
If matrix $A$ represents a function

$Col\ A$ is the range of the function

![](https://i.imgur.com/VQ4NsJa.png)
:::

## Row space
- Row space of matrix $A$ is the span of its rows. It it denoted as $Row\ A$
	
    $Row\ A = Col\ A^T$

## RREF
- Original Matrix $A$ v.s. its RREF $R$
	- Columns:
		- The relations between the columns are the same.
		- The span of the columns are different.
			
            $Col\ A \neq Col\ R$
	- Rows:
		- The relations between the rows are changed.
		- The span of the rows are the same.
			
            $Row\ A = Row\ R$

## Consistent
- $Ax = b$ have solution
- $b$ is the linear combination of columns of $A$
- $b$ is in the span of the columns of $A$
- $b$ is in $Col\ A$

![](https://i.imgur.com/kflIW9c.png)

:::success
Subspace is Closed under addition and multiplication
:::

###### tags: `線性代數筆記`