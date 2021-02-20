# What can we know from RREF?

# RREF v.s. Linear Combination
## Column Correspondence Theorem

$A = [a_1\ \dots\ a_n]$ >==RREF==> $R = [r_1\ \dots\ r_n]$

:::success
If $a_j$ is a linear combination of other columns of $A$, then
$r_j$ is a linear combination of the **corresponding** columns of $R$ with **the same coefficientss**
:::

For example
$$a_5 = -a_1 + a_4 \\
\Rightarrow r_5 = -r_1 + r_4
$$

The reverse narrative is also holds

For example
$$r_3 = 3r_1 - 2r_2 \\
\Rightarrow a_3 = 3a_1 - 2a_2
$$

$$A = \begin{bmatrix} 1 & 2 & -1 & 2 & 1 & 2 \\ -1 & -2 & 1 & 2 & 3 & 6 \\ 2 & 4 & -3 & 2 & 0 & 3 \\ -3 & -6 & 2 & 0 & 3 & 9 \end{bmatrix} \quad R = \begin{bmatrix} 1 & 2 & 0 & 0 & -1 & -5 \\ 0 & 0 & 1 & 0 & 0 & -3 \\ 0 & 0 & 0 & 1 & 1 & 2 \\ 0 & 0 & 0 & 0 & 0 & 0 \end{bmatrix}
$$

$$a_2 = 2a_1 \Leftrightarrow r_2 = 2r_2 \\
a_5 = -a_1 + a_4 \Leftrightarrow r_5 = -r_1 + r_4
$$

### Intutive Idea
$$ A = \begin{bmatrix} 6 & 9 & 15 \\ 8 & 0 & 8 \\ 9 & 2 & 11 \end{bmatrix} \quad a_1 + a_2 = a_3
$$

There are three elementary row operations to change the column

1. Interchange
	$$B = \begin{bmatrix} 9 & 2 & 11 \\ 8 & 0 & 8 \\ 6 & 9 & 15 \end{bmatrix} \quad	b_1 + b_2 = b_3
	$$
2. Scaling
	$$C = \begin{bmatrix} 12 & 18 & 30 \\ 8 & 0 & 8 \\ 9 & 2 & 11 \end{bmatrix} \quad c_1 + c_2 = c_3
	$$
3. Row Addition
	$$D = \begin{bmatrix} 6 & 9 & 15 \\ 8 & 0 & 8 \\ 3 & -7 & -4 \end{bmatrix} \quad d_1 + d_2 = d_3
	$$

:::success
we can find that no matter which elementary row operations we take, ***the relation between columns are still the same***
:::

### Reason
- Coefficient Matrix
	
    $A$ >==RREF==> $R$
- Augmented Matrix
	
    $[A\ b]$ >==RREF==> $[R\ b']$

> If we transfer Augmented Matrix into RREF Matrix
> 
> delete the last colums of these two matrix, the remaining Matrix $R$ is still the RREF Matrix of $A$

![](https://i.imgur.com/RoeII07.png)

- The RREF of matrix $A$ is $R$
	
    $Ax = b$ and $Rx = b$ have the same solution set? (X)
- The RREF of augmented matrix $[A\ b]$ is $[R\ b']$
	
    $Ax = b$ and $Rx = b'$ have the same solution set? (O)
- The RREF of matrix $A$ is $R$
	
    $Ax = 0$ and $Rx = 0$ have the same solution set? (O)
	> If $b = 0$, then $b' = 0$

![](https://i.imgur.com/uFWmOoF.png)

:::info
There's no Row Corresponding Theorem
:::

### Span
![](https://i.imgur.com/P7ifA6O.png)

:::info
True in Row but not in column
:::

:::success
The elemetary row operations change the span of columns
:::

## Conclusion
> Origin Matrix v.s. RREF

- Columns
	- The relations between the columns are the same
	- The Span of the columns  different
- Rows
	- The relations between the rows are changed
	- The Span of the rows are the same

# RREF v.s. Idependent
## Column Correspondence Theorem
we have a augmented matrix $A$ , and we transfer it to RREF matix $R$

1. every pivot column in $R$ are linear independent
2. every non-pivot column in $R$ are the linear combination of the previous pivot columns
	
    Because of the REF, made there's no non-zero number before pivot
	
## Independent
we have a matrix that all columns are independent
- then every column is a pivot column
- every column in $RREF(A)$ is standard vector

look in different situations
- $A$ is a square matrix
	
    if the matrix $A$ is square matrix, then $RREF(A)$ is a **identity matrix($I$)**
- $A$ is a $m \times n$ matrix, and $m>n$
	
    because every column is a pivot column, the $RREF(A)$ is a matrix like $\large\begin{bmatrix} I \\ O\end{bmatrix}$
- $A$ is a $m \times n$ matrix, and $m<n$
	
    because every column is a pivot column, the $RREF(A)$ is **not exists**

:::success
Even we don't know what $A$ exactly is, but we can easily find out what $RREF(A)$ is
:::

:::info
If we have a vector set $S$ more than m vectors in $\mathscr{R}^m$ must be dependent
:::

# RREF v.s. Rank
- Rank
	- Maximum number of independent columns
		- $Rank\ A$ $\leq$ Number of columns
	- Number of non-zero rows
		- $Rank\ A$ $\leq$ Number of rows
	- Number of pivot column
		- $Rank\ A$ $\leq$ Min(Number of columns, Number of rows)
	
## Properties of Rank from RREF
Given a $m \times n$ matrix $A$
- $Rank\ A \leq min(m,n)$
	- if $Rank(A) = min(n,m)$, we call $A$ is full rank
- Because *the columns of A are independent* is equivalent to $Rank\ A = n$
	- if $m < n$, the columns of $A$ is dependent
:::success
In $\mathscr{R}^m$, you cannot find more than m vectors that are independent
:::

## Basic, Free Variables v.s. Rank
after we transfer a matrix $A$ into RREF matrix, we can transfer it into a system of linear equations

- number of basic variables
	- number of non-zero row
	- Rank
- number of free variables
	- number of column - number of non-zero row
	- Nullity

:::success
Rank

= Maximum number of independent columns

= Number of pivot column

= Number of non-zero rows of RREF

= Number of basic variables

---

Nullity

= Number of column - Rank

= Number of free variables
:::

# RREF v.s. Span
## Consistent or not
- Given $Ax = b$, if the reduced row echelon form of $[A\ b]$ is
	$$\begin{bmatrix} 1 & 0 & 3 & 1 \\ 0 & 1 & 2 & -2 \\ 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0\end{bmatrix}
	$$
	- consistent
	- b is the span of the columns of A
- Given $Ax = b$, if the reduced row echelon form of $[A\ b]$ is
	$$\begin{bmatrix} 1 & 0 & 3 & 1 \\ 0 & 1 & 2 & -2 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0\end{bmatrix}
	$$
	- inconsistent
	- b is **Not** in the span of the columns of A

:::success
we can found that if the RREF of $[A\ b]$ is $\begin{bmatrix} * & * & * & * \\ * & * & * & * \\ 0 & 0 & 0 & d \\ 0 & 0 & 0 & 0\end{bmatrix}$

then $Ax = b$ is inconsistent, no solution

In other words
- $Rank A \neq Rank [A\ b]$
:::
:::info
we need to know $b$, in order to know a system of linear has solution or not
:::

If $Ax = b$ is consistent for **every** $b$
- RREF of $[A\ b]$ cannot have a row whose only non-zero entry is at the last column
- RREF of $A$ cannot have zero row
- Rank A = Number of rows
- Every $b$ belongs to $Span(\{a_1,\ \dots,\ a_n\})$
- $Span(A) = \mathscr{R}^m$

Because $Rank\ A$ = Number of rows
- m independent vectors can span $\mathscr{R}^m$
- More than m vectors in $\mathscr{R}^m$ must be dependent

![](https://i.imgur.com/xR7W8uz.png)


## Full Rank
### $Rank\ A = n$

> must square or be thin and tall

- The columns of $A$ are linearly independent
	- $Ax = b$ has at most one solution
- All columns are pivot columns
	- RREF of A is $\large \begin{bmatrix} I \\ O\end{bmatrix}$

### $Rank\ A = m$

> must be square or short and fat

- Every row of $R$ contains a pivot position (leading entry)
- $Ax = b$ always have solution (at least one solution) for every $b$ in $\mathscr{R}^m$
- The columns of $A$ generate $\mathscr{R}^m$

###### tags: `線性代數筆記`