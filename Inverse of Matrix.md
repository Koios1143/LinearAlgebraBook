# Inverse of Matrix

## Inverse of Function
- Two function $f$ and $g$ are inverse of each other ($f = g^{-1}$) if for any $v$
	![](https://i.imgur.com/cGNCeG4.png)

## Inverse of Matrix
> please view matrix as a linear system (function)

- Two matrix $A$ and $B$ are inverse of each other if for any $v$
	![](https://i.imgur.com/e2un0r6.png)

:::success
If $A$ and $B$ are inverse of each other, then $AB = BA = I$

that is, $A$ is called invertible if there's a matrix $B$ such that $AB = BA = I$
:::

:::info
invertible = Non-singular

uninvertible = singular
:::

If $A$ is a $m \times n$ matrix, and $B$ is a $n \times m$ matrix

And if $AB = I_m$, and $BA = I_n$

then $$\because I_m \neq I_n \\ \therefore AB \neq BA$$

:::success
If matrix $A$ is non-square, $A$ cannot be invertible
:::

:::success
Not all the square matrix is invertible
:::

If $AB = I\  ,BA = I\  ,AC = I\  ,CA = I$

then $B = BI = B(AC) = (BA)C = IC = C$

:::success
every invertible matrix will only have a inverse matrix
:::

## Inverse for matrix product
- $A$ and $B$ are invertible $n \times n$ matrices, is $AB$ invertible? (O)
	
    $(AB)^{-1} = B^{-1}A^{-1}$
	> proof
	
	$B^{-1}A^{-1}(AB) = B^{-1}(A^{-1}A)B = B^{-1}B = I$
	
    $(AB)B^{-1}A^{-1} = A(BB^{-1})A^{-1} = AA^{-1} = I$
- Let $A_1, A_2, \dots, A_k$ be $n \times n$ invertible matrices. The product $A_1A_2\dots A_k$ is invertible? (O)
	
    $(A_1A_2\dots A_k)^{-1} = (A_k)^{-1}(A_{k-1})^{-1}\dots (A_1)^{-1}$
	
## Inverse for matrix Transpose
- If A is invertible, is $A^T$ invertible? (O)
	
    $(A^T)^{-1} = (A^{-1})^T$
	> proof
	> Remind: $(AB)^T = B^TA^T$

	$A^{-1}A = I$ => $(A^{-1}A)^T = I$ => $A^T(A^{-1})^T = I$
	
    $AA^{-1} = I$ => $(AA^{-1})^T = I$ => $(A^-1)^TA = I$

## Solving System of linear equation
given a system of linear equation $Ax = b$
- If $A$ is invertible
	
    $A^{-1}(Ax) = A^{-1}b$
	
    $(A^{-1}A)x = A^{-1}b$
	
    $x = A^{-1}b$

:::info
However, this method is computationally inefficient
:::

## Invertible
> A is called invertible if there is a matrix B such that $AB = I$ and $BA = I$ ($B = A^{-1}$)

![](https://i.imgur.com/WcwZLGK.png)

- Let $A$ be an $n \times n$ matrix. $A$ is invertible if and only if
	- The columns of $A$ span $\mathscr{R}^n$
	- For every $b$ in $\mathscr{R}$, the system $Ax = b$ is consistent
	- The rank of $A$ is $n$
	- The columns of $A$ are linear independent
	- The only solution to $Ax = 0$ is the zero vector
	- The nullity of $A$ is zero
	- The RREF of $A$ is $I_n$
	- $A$ is a product of elementary matrices
	- There exists an $n \times n$ matrix $B$ such that $BA = I_n$
	- There exists an $n \times n$ matrix $C$ such that $AC = I_n$

### Review : One-to-one
- A function $f$ is one-to-one
	> $f(x) = b$ has at most one solution
	
	If vector $v$ is on the range in co-domain, then there's only a solution
	
    If vector $v$ is not on the range in co-domain, then there's no solution
	
    ![](https://i.imgur.com/CWr6BUJ.png)
	
    If we try to mapping a vector $v$ in domain into co-domain from $nd$ to $md$ ($m<n$)
	
    then the vectors in domain must be compression to co-domain
	
    :::success
	If co-domain is **smaller** than the domain, $f$ cannot be one-to-one
	:::
	
    If a Matrix $A$ is **short** and **fat**, it cannot be one-to-one
	
    **But reverse is not true**
	> For Example, a 2-d vector in co-domain mapping to all vectors in domain
	
    :::success
	If a matrix $A$ is one-to-one, its columns are independent
	:::

### Review : Onto
- A function $f$ is onto
	> $f(x) = b$ is always have solution

	> Co-domain = range

	![](https://i.imgur.com/uIWzeg6.png)
	:::success
	If co-domain is **larger** than the domain, $f$ cannot be onto
	:::
	If a matrix $A$ is **tall** and **thin**, it cannot be onto
	**The reverse is not true**
	:::success
	If a matrix $A$ is onto, rank $A$ = numbers of rows
	:::

---

Because we need to mapping back to the input vector $v$ in co-domain, so $A$ must be one-to-one

Because every vectors in co-domain can mapping to a vector in domain throught $A^{-1}$, so **co-domain = range**

:::success
matrix $A$ must be **one-to-one** and **onto** at the same time
:::

---

### One-to-one and Onto
A function $f$ is one-to-one and onto

:::success
The domain and co-domain must have **the same size**

The corresponding matrix $A$ is **square**
:::

:::success
If a square matrix $A$ is one-to-one, then it is onto, too
:::

---

Let $A$ be an $n \times n$ matrix (that is, $A$ is a square matrix)
- Onto => one-to-one => invertible
	- The columns of $A$ span $\mathscr{R}^n$
	- For every $b$ in $\mathscr{R}^n$, the system $Ax = b$ is consistent
	- The rank of $A$ is $n$
- one-to-one => onto => invertible
	- The columns of $A$ are linear independent
	- The rank of $A$ is the number of columns
	- The nullity of $A$ is zero
	- The only solution to $Ax = 0$ is the zero vector
	- The RREF of $A$ is $I_n$
		Because $Rank(A) = n$, RREF of $A$ is $\begin{bmatrix} I \\ O\end{bmatrix}$
		At the same time, $A$ is a square matrix, so we don't need the $O$ matrix below
	
:::info
most conditions above need to know RREF of $A$ at first
:::

:::success
- Let $A$ be an $n \times n$ matrix. $A$ is invertible if and only if **The RREF of $A$ is $I_n$**
:::

- $A$ is an $n \times n$ matrix, and $A$ is invertible
	- There exists an $n \times n$ matrix $B$ such that $BA = I_n$
	- The only solution to $Ax = 0$ is the zero vector

	Proof : $$ \\ $$If $Av = 0$ and $v \neq 0$$$BA = I_n \\ BAv = I_nv \\ BAv = 0 \neq I_nv = v$$

	- There exists an $n \times n$ matrix $C$ such that $AC = I_n$
	- For every $b$ in $\mathscr{R}^n$, $Ax = b$ is consistence
	
	Proof : $$AC = I_n \\ ACb = I_nb \\ x = Cb \\ Ax = I_nb = b$$ $Cb$ is always a solution for $b$

---

## Inverse of Elementary matrices
Every elementary row operation can be performed by matrix multiplication
1. Interchange
	![](https://i.imgur.com/P5ItoRO.png)
2. Scaling
	![](https://i.imgur.com/GdFIijJ.png)
3. Adding $k$ times row $i$ to row $j$
	![](https://i.imgur.com/tmC7Hz2.png)

:::success
We called these matrices **Elementary Matrix**
:::

### Find Elementary matrices
Because to every matrix, elementary matrix will do the same operation, so we can multiple a $I$ matrix, then we'll find it

:::info
For example: 

we want to find a elementary matrix which will exchange the $2^{nd}$ and $3^{rd}$ row

Assume $E$ is the elementary matrix we want to find, then:$$EI = \begin{bmatrix}1 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0\end{bmatrix} \\ E = \begin{bmatrix}1 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0\end{bmatrix}$$
:::

---

### Find Inverse of Elementary Matrices
Just reverse the operation, and find the new elementary matrix again

:::info
For example:

we have a elementary matrix $E$, which can **exchange** the $2^{nd}$ and $3^{rd}$ row

then $E^{-1}$ can exchange the $3^{rd}$ and $2^{nd}$ row$$E= \begin{bmatrix}1 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0\end{bmatrix} \\ E^{-1} = \begin{bmatrix}1 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0\end{bmatrix}$$
:::

:::info
For example:

we have a elementary matrix $E$, which can **multiply** the $2^{nd}$ row by $-4$

then $E^{-1}$ can multiply the $2^{nd}$ row by $\frac{1}{-4}$$$E = \begin{bmatrix}1 & 0 & 0 \\ 0 & -4 & 0 \\ 0 & 0 & 1\end{bmatrix} \\ E^{-1} = \begin{bmatrix}1 & 0 & 0 \\ 0 & \frac{1}{-4} & 0 \\ 0 & 0 & 1\end{bmatrix}$$
:::

:::info
For example:

we have a elementary matrix $E$, which can add $2$ times row $1$ to row $3$

then $E^{-1}$ can add $-2$ times row $1$ to row $2$$$E = \begin{bmatrix}1 & 0 & 0 \\ 0 & 1 & 0 \\ 2 & 0 & 1\end{bmatrix} \\ E^{-1} = \begin{bmatrix}1 & 0 & 0 \\ 0 & 1 & 0 \\ -2 & 0 & 1\end{bmatrix}$$
:::

---

### RREF & Elementary matrix
- Let $A$ be an $m \times n$ matrix with RREF $R$
	
    $E_k \dots E_2E_1A = R$
- There exists an ivertible $m \times n$ matrix $P$ such that $PA = R$
	
    $P = E_k \dots E_2E_1$
	
    $P^{-1} = E_1^{-1}E_2^{-2} \dots E_k^{-k}$

:::success
An $n \times n$ matrix $A$ is invertible if and only if
**matrix $A$ is a product of elementary matrices**
:::

---

### Inverse of General Matrix
- Let $A$ be an $n \times n$ matrix. $A$ is invertible if and only if
	- The reduced row echelon form of $A$ is $I_n$
		
        $E_k \dots E_2E_1A = R = I_n$
		
        $A^{-1} = E_k \dots E_2E_1$

:::success
So, all we need to do is to **transfer $A$ into RREF**, and **record the passing elementary matrices** $E$

If RREF of $A$ is $I_n$, then $E = A^{-1}$
:::

In other words
- Let $A$ be an $n \times n$ matrix. Transform $\begin{bmatrix} A & I_n \end{bmatrix}$ into its RREF $\begin{bmatrix} R & B \end{bmatrix}$
	- $R$ is the RREF of $A$
	- $B$ is an $n \times n$ matrix (not RREF)
- If $R = I_n$, then $A$ is invertible
	- $B = A^{-1}$

![](https://i.imgur.com/0atGJbV.png)

- If we want to find $A^{-1}C$, then we can transform $\begin{bmatrix} A & C \end{bmatrix}$ into its RREF $\begin{bmatrix} R & C' \end{bmatrix}$
	- $C' = A^{-1}C$


###### tags: `線性代數筆記`