# Basis

Let vector set $V$ be an nonzero subspace of $\mathscr{R}^n$. A basis $B$ for $V$ is a **linearly independent** **generation set** of $V$

So here are three conditions of basis
1. $V$ is an nonzero subspace
2. $B$ is linearly independent
3. $B$ is a generation set of $V \Leftrightarrow Span\ B = V$

## Examples
$\{e_1, e_2, \dots, e_n\}$ is a basis for $\mathscr{R}^n$ ? (O)
1. $\{e_1, e_2, \dots, e_n\}$ is independent
2. $\{e_1, e_2, \dots, e_n\}$ generates $\mathscr{R}^n$

$\{\begin{bmatrix} 1 \\ 0\end{bmatrix}, \begin{bmatrix} 0 \\ 1\end{bmatrix}\}$ is a basis for $\mathscr{R}^2$ ? (O)

:::success
any $n$ independent vectors form a basis for $\mathscr{R}^n$
:::

## Properties
- vector set $S$ is contained in $Span\ S$
	:::success
	Basis is always in its subspace
	:::
- If a finite set $S'$ is contained in $Span\ S$, then $Span\ S'$ is also contained in $Span\ S$
	- Because $Span\ S$ is a subspace
	![](https://i.imgur.com/ldm9QZQ.png)

- For any vector $z$, $Span\ S = Span\ S \ \cup\{z\}$ if and only if $z$ belongs to $Span\ S$
	![](https://i.imgur.com/IfX5Osa.png)

## Columns space V.S. Basis
The **pivot columns** of a matrix form a basis for its columns space.

:::info
Remember, when we transfer a matrix $A$ into RREF, the relation between columns doesn't change.
:::

> Pivot columns space of a matrix is a basis? (O)

1. Nonzero subspace
	
    Yes, at least a conponent $1$
2. Linearly independent
	
    Yes, Remenber the blue block above.
	
    So, just see the $RREF(A)$, pivot columns are linearly independent
3. Generation set of $V$
	
    Yes, because RREF will made any non-pivot columns can be combine by the precious pivot columns

## Theorem
1. A basis is the **smallest** generation set
2. A basis is the **largest** independent vector set in the subspace
3. Any two bases for a subspace **contain the same number of vectors**
	- The number of vectors in a basis for a nonzero subspace $V$ is called **dimension** of $V$ ($dim\ V$)

## Theorem 3
> Any two bases for a subspace **contain the same number of vectors**

Suppose $\{u_1, u_2, \dots, u_k\}$ and $\{w_1, w_2, \dots, w_k\}$ are two bases of $V$
Let $A = [u_1\ u_2\ \dots\ u_k]$ and $B = [w_1\ w_2\ \dots\ w_k]$

- Step 1
	
    $Span\ \{u_1, u_2, \dots, u_k\} = V$
	
    $\Rightarrow \exists\ c_i \in \mathscr{R}^k$ such that $Ac_i = w_i$ for all $i$
	
    $\Rightarrow A[c_1\ c_2\ \dots\ c_p] = [w_1\ w_2\ \dots\ w_k]$
	
    $\Rightarrow AC = B$
	
    :::info
	$\exists$ means exists
	:::
- Step 2
	- $Cx = 0$ for some $x \in \mathscr{R}^p$
		
        $\Rightarrow ACx = Bx = 0$
	- $B$ is independent vector set 
		
        $\Rightarrow x = 0 \to c_1, c_2, \dots, c_p$ are independent
	
	$c_i \in \mathscr{R}^k \Rightarrow p \leq k$
	![](https://i.imgur.com/yUSno3a.png)
	:::success
	Because the matrix is independent, it's **number of rows** must larger than **number of columns**
	:::

Reversing the roles of the two bases, and do *Step 1* and *Step 2* again, we'll get $k \leq p$

:::success
$$k \leq p \land p \leq k\\
\Rightarrow k = p
$$
:::

---

> Numbers of vectors in a basis for a nonzero subspace $V$ is called **dimension** of $V$ ($dim\ V$)

We define the dimension of *zero subspace* is $0$

![](https://i.imgur.com/u53r9vu.png)

:::success
Every basis of $\mathscr{R}^n$ has $n$ vectors
:::

### Example
$V = \Biggl\{ \begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix} \in \mathscr{R}^4 \ : \ x_1 - 3x_2 + 5x_3 - 6x_4\Biggr\}$ Find $dim\ V$

$\begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix} = \begin{bmatrix} 3x_2 - 5x_3 + 6x_4 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix} = x2 \begin{bmatrix} 3 \\ 1 \\ 0 \\ 0 \end{bmatrix} + x3 \begin{bmatrix} -5 \\ 0 \\ 1 \\ 0 \end{bmatrix} + x_4 \begin{bmatrix} 6 \\ 0 \\ 0 \\ 1 \end{bmatrix}$

then $\Biggl\{ \begin{bmatrix} 3 \\ 1 \\ 0 \\ 0 \end{bmatrix}, \begin{bmatrix} -5 \\ 0 \\ 1 \\ 0 \end{bmatrix}, \begin{bmatrix} 6 \\ 0 \\ 0 \\ 1 \end{bmatrix} \Biggr\}$ is Independent vector set that generates $V$

## Theorem 1 - Reduction Theorem
> A basis is the **smallest** generation set

> $S$ can be reduced to a basis for $V$ by removing some vectors

Suppose $S = \{u_1, u_2, \dots, u_k\}$ is a generation set of subspace $V$

Let $A = [u_1\ u_2\ \dots\ u_k]$

Subspace $V = Span\ S = Col\ A$

The basis of $Col\ A$ is the pivot columns of $A$, Subset of $S$

:::success
All generation sets have a basis
:::

### Example
$$S = \Biggl\{ \begin{bmatrix} 1 \\ -1 \\ 2 \\ 3 \end{bmatrix}, \begin{bmatrix} 2 \\ -2 \\ 4 \\ 6 \end{bmatrix}, \begin{bmatrix} -1 \\ 1 \\ -3 \\ 2 \end{bmatrix}, \begin{bmatrix} 2 \\ 2 \\ 2 \\ 0 \end{bmatrix}, \begin{bmatrix} 1 \\ 3 \\ 0 \\ 3 \end{bmatrix}, \begin{bmatrix} 2 \\ 6 \\ 3 \\ 9 \end{bmatrix}\Biggr\}
$$

$$A = \begin{bmatrix} 1 & 2 & -1 & 2 & 1 & 2 \\
-1 & -2 & 1 & 2 & 3 & 6 \\
2 & 4 & -3 & 2 & 0 & 3 \\
3 & 6 & 2 & 0 & 3 & 9\end{bmatrix}
$$

$$RREF(A) = \begin{bmatrix} 1 & 2 & 0 & 0 & -1 & -5 \\
0 & 0 & 1 & 0 & 0 & -3 \\
0 & 0 & 0 & 1 & 1 & 2 \\
0 & 0 & 0 & 0 & 0 & 0\end{bmatrix}
$$

$$Subspace\ V = Span\ S = Col\ A = Span \Biggl\{ \begin{bmatrix} 1 \\ -1 \\ 2 \\ 3 \end{bmatrix}, \begin{bmatrix} -1 \\ 1 \\ 3 \\ 2 \end{bmatrix}, \begin{bmatrix} 2 \\ 2 \\ 2 \\ 0 \end{bmatrix}\Biggr\}
$$

## Theorem 2 - Extension Theorem
> A basis is the **largest** independent vector set in the subspace

Suppose we have a subspace $V$

Given a independent vector set $S$ (elements of $S$ in $V$)

- If $Span\ S = V$, then $S$ is a basis
- If $Span\ S \neq V$, find $v_1$ in $V$ but not in $Span\ S$ and add it to $S$

Check these two conditions until $Span\ S = V$, and you'll find the basis in the end

![](https://i.imgur.com/wV1q8O8.png)

:::success
I am either a basis or I am becoming a basis
:::

## More From Theorem
> Look back lecture before, some properties can easily proofed by basis

- A basis is the smallest generation set
	- A vector set generates $\mathscr{R}^m$ must contain at least $m$ vectors
	- $\mathscr{R}^m$ have a basis $\{e_1, e_2, \dots, e_m\}$

- A basis is the largest independent set in the subspace
	- Any independent vector set in $\mathscr{R}^m$ contain at most $m$ vectors

## Summary
![](https://i.imgur.com/xHnTmgw.png)

## Confirming that a set is a Basis
### Intutive way
Just use definition to check

1. is an nonzero subspace
2. $B$ is linearly independent
3. $B$ is a generation set of $V$
	that is, $Span\ B = V$

:::info
To check independent is easy
But to check generation set is difficult
:::

### Another way
Given a subspace $V$, assume we already know $dim\ V = k$. Suppose $S$ is a subset of $V$ with $k$ vectors
- If $S$ is independent $\Rightarrow$ $S$ is basis
- If $S$ is a generation set $\Rightarrow$ $S$ is basis

Any of the two conditions is true, then $S$ is basis

---

#### Example
$V = \Biggl\{ \begin{bmatrix} v_1 \\ v_2 \\ v_3 \end{bmatrix} \in \mathscr{R}^3\ : \ v_1 - v_2 + 2v_3 = 0 \Biggr\}$
$C = \Biggl\{ \begin{bmatrix} 1 \\ 1 \\ 0\end{bmatrix}, \begin{bmatrix} -1 \\ 1 \\ 1\end{bmatrix} \Biggr\}$

$Dim\ V = 2$ (parametric represetation)
Is $C$ a basis of $V$ ?(O)

$C$ is a subset of $V$ with 2 vectors and is independent $\Rightarrow$ $C$ is a basis of $V$

---

***Proof***
- **If $S$ is independent $\Rightarrow$ $S$ is basis**
	
    By *Theorem 2*, we know $S$ is neither a basis nor is becomming a basis
	
    And we knew that $S$ is already have $k$ vectors, so it is already basis
- **If $S$ is a generation set $\Rightarrow$ $S$ is basis**
	
    By *Theorem 1*, we can remove some vectors from $S$ to form a basis
	
    However, $S$ is already have $k$ vectors, so it is already basis

###### tags: `線性代數筆記`