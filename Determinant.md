# Determinant

- The determinant for a **square matrix** is a scalar that provides information about the matrix (Ex: **Invertibility** of the matrix)

## Determinant in High School
- $2 \times 2$
	
    $A = 
	\begin{bmatrix}
		a & b \\
		c & d \\
	\end{bmatrix} \quad det(A) = ad-bc$
	![](https://i.imgur.com/szLcuVd.png)
- $3 \times 3$
	
    $A = 
	\begin{bmatrix}
		a_1 & a_2 & a_3 \\
		a_4 & a_5 & a_6 \\
		a_7 & a_8 & a_9 \\
	\end{bmatrix} \quad det(A) = a_1a_5a_9 + a_2a_6a_7 + a_3a_4a_8 - a_3a_5a_7 - a_2a_4a_9 - a_1a_6a_8$
	![](https://i.imgur.com/pFCZQyk.png)

## Cofactor Expansion
- Suppose $A$ is an $n \times n$ matrix. 
    
    $A_{ij}$ is defined as the submatrix of $A$ obtained by removing the $i-th$ row and $j-th$ column.
	$A = 
	\begin{bmatrix} 
		a_{1,1} & \dots & a_{1,j} & \dots & a_{i,n} \\
		\vdots &  & \vdots &  & \vdots \\
		a_{i,1} & \dots & a_{i,j} & \dots & a_{i,n} \\
		\vdots &  & \vdots &  & \vdots \\
		a_{n,1} & \dots & a_{i,j} & \dots & a_{n,n} \\
	\end{bmatrix}$
	
	$A_{i,j} = 
	\begin{bmatrix} 
		a_{1,1} & \dots & a_{1,j-1} & a_{1,j+1} & \dots & a_{i,n} \\
		\vdots &  & \vdots &  \vdots & & \vdots \\
		a_{i-1,1} & \dots & a_{i-1,j-1} & a_{i-1, j+1} & \dots & a_{i-1,n} \\
		a_{i+1,1} & \dots & a_{i+1,j-1} & a_{i+1, j+1} & \dots & a_{i-1,n} \\
		\vdots &  & \vdots &  \vdots & & \vdots \\
		a_{n,1} & \dots & a_{i,j-1} & a_{i,j+1} & \dots & a_{n,n} \\
	\end{bmatrix}$

## How to calculate determinant
- Pick row 1
	
    $det(A) = a_{11}c_{11} + a_{12}c_{12} + \dots + a_{1n}c_{1n}$

:::info
$c_{ij}$ is called $(i, j)$-cofactor

$c_{ij} = (-1)^{i+j} \times det(A_{ij})$
:::

:::success
Actually, we can choose anthoer row or even another column nor row 1 and get the same answer!
:::

:::success
We define $det([a]) = a$
:::

### Example
- $2 \times 2$ matrix
	
    $A = 
	\begin{bmatrix}
		a & b \\
		c & d \\
	\end{bmatrix}$
	
	Pick the first row
	$det(A) = ac_{11} + bc_{12}$
	$c_{11} = (-1)^{1+1}det([d]) = d$
	$c_{12} = (-1)^{1+2}det([c]) = -c$
	
- $3 \times 3$ matrix
	
    $A = 
	\begin{bmatrix}
		1 & 2 & 3 \\
		4 & 5 & 6 \\
		7 & 8 & 9 \\
	\end{bmatrix}$
	
	Pick the second row
	
    $det(A) = a_{21}c_{21} + a_{22}c_{22} + a_{23}c_{23}$
	
    $c_{21} = (-1)^{2+1}det(A_{21})$
	
    $c_{22} = (-1)^{2+2}det(A_{22})$
	
    $c_{23} = (-1)^{2+3}det(A_{23})$
	
    $A_{21} = \begin{bmatrix}2 & 3 \\8 & 9 \\\end{bmatrix}$
	
    $A_{22} = \begin{bmatrix}1 & 3 \\7 & 9 \\\end{bmatrix}$
	
    $A_{23} = \begin{bmatrix}1 & 2 \\7 & 8 \\\end{bmatrix}$

- Tridiagonal $n \times n$ matrix $A$
	
    $\begin{bmatrix}
		1 & 1 & 0 & \dots & \dots & 0 & 0 & 0 \\
		1 & 1 & 1 & \dots & \dots & 0 & 0 & 0 \\
		0 & 1 & 1 & \dots & \dots & 0 & 0 & 0 \\
		\vdots & \vdots & \vdots & \ddots & \ddots & \vdots & \vdots & \vdots \\
		\vdots & \vdots & \vdots & \ddots & \ddots & \vdots & \vdots & \vdots \\
		0 & 0 & 0 & \dots & \dots & 1 & 1 & 0 \\
		0 & 0 & 0 & \dots & \dots & 1 & 1 & 1 \\
		0 & 0 & 0 & \dots & \dots & 0 & 1 & 1 \\
	\end{bmatrix}$
	
	$A_2 = \begin{bmatrix}
		1 & 1 \\
		1 & 1 \\
	\end{bmatrix}$
	
    $A_3 = \begin{bmatrix}
		1 & 1 & 0 \\
		1 & 1 & 1 \\
		0 & 1 & 1 \\
	\end{bmatrix} \qquad c_{11} = (-1)^2det(\begin{bmatrix}	1 & 1 \\ 1 & 1 \end{bmatrix}) = det(A_2)$
	
    $A_4 = \begin{bmatrix}
		1 & 1 & 0 & 0 \\
		1 & 1 & 1 & 0 \\
		0 & 1 & 1 & 1 \\
		0 & 0 & 1 & 1 \\
	\end{bmatrix} \qquad c_{11} = (-1)^2det(\begin{bmatrix}1 & 1 & 0 \\1 & 1 & 1 \\0 & 1 & 1 \\\end{bmatrix}) = det(A_3)$
	
	$det(A_4) = a_{11}c_{11} + a_{12}c_{12} + a_{13}c_{13} + a_{14}c_{14} \\ = det(A_3) - det(A_2)$
	
	And so on, we can know
	
	$det(A_4) = det(A_3) - det(A_2) \\det(A_n) = det(A_{n-1}) - det(A_{n-2})$
	
	$det(A_1) = 1 \qquad det(A_2) = 0 \qquad det(A_3) = -1 \\ det(A_4) = -1 \qquad det(A_5) = 0 \qquad det(A_6) = 1 \dots$

	By this law, we can know any $n \times n$ Tridiagonal matrix's determinants

## Properties of Determinants
> **Volume** in high dimensions

- Basic Properties
	1. $det(I) = 1$
		![](https://i.imgur.com/eUWbbHG.png)
	2. Exchange rows only reverses the sign of determinant
		![](https://i.imgur.com/pi7dKXb.png)
	3. Determinant is **linear** for each row
		![](https://i.imgur.com/d9IWKNY.png)

Area in 2d and volume in 3d have the above properties

1. $det(I) = 1$
	- $I_2 = \begin{bmatrix}1 & 0 \\0 & 1 \\\end{bmatrix}$
		
        Square, Area equals to $det(I_2) = 1$
	
	- $I_3 = \begin{bmatrix}1 & 0 & 0 \\0 & 1 & 0 \\0 & 0 & 1 \\\end{bmatrix}$
		
        Cube, Volume equals to $det(I_3) = 1$

2. Exchange rows only reverses the sign of determinant
	- $I_2$
	    
        $det(\begin{bmatrix} 1 & 0 \\ 0 & 1 \end{bmatrix}) = 1 \quad det(\begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}) = -1$
	- $I_3$
	    
        $det(\begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix}) = 1 \quad det(\begin{bmatrix} 1 & 0 & 0 \\ 0 & 0 & 1 \\ 0 & 1 & 0 \end{bmatrix}) = -1 \quad det(\begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ 1 & 0 & 0 \end{bmatrix}) = 1$
	
	![](https://i.imgur.com/UTDugKw.png)

	:::success
	If a matrix $A$ has ***2 equal rows***, $det(A) = 0$
    
	Futhermore, If a matrix $A$ has ***2 parallel rows***, $det(A) = 0$
	:::

3. Determinant is **linear** for each row
	- $det(\begin{bmatrix} ta & tb \\ c & d \end{bmatrix}) = tdet(\begin{bmatrix} a & b \\ c & d \end{bmatrix})$
		
        we can think about this problem in the view of coordinates
		![](https://i.imgur.com/0YcwKEX.png)
		:::success
		In General, if we multiply a $n$-d matrix A by $t$ times,		then $det(A') = t^{n}det(A)$
		:::
		
		If a matrix $A$ has a zero row, then $det(A)$ must be zero
		:::success
		We can regard zero row as $0 \times A$, then $det(A') = 0^{n}det(A) = 0$
		:::
		
	- $det(\begin{bmatrix} a+a' & b+b' \\ c & d \end{bmatrix}) = det(\begin{bmatrix} a & b \\ c & d \end{bmatrix}) + det(\begin{bmatrix} a' & b' \\ c & d \end{bmatrix})$
		![](https://i.imgur.com/R5FyLZC.png)
		
		:::danger
		$det(A) + det(B) \neq det(A+B)$
		:::
		
	- Subtract $k$ $x$ row $i$ from row $j$ (elementary row operation), the Determinant doesn't change
		
        Here, we use $2$-d matrix for example
		
		$det(\begin{bmatrix} a & b \\ c-ka & d-kb \end{bmatrix}) \\
		= det(\begin{bmatrix} a & b \\ c & d \end{bmatrix}) + det(\begin{bmatrix} a & b \\ -ka & -kb \end{bmatrix})\\
		= det(\begin{bmatrix} a & b \\ c & d \end{bmatrix}) -kdet(\begin{bmatrix} a & b \\ a & b \end{bmatrix})\\
		= det(\begin{bmatrix} a & b \\ c & d \end{bmatrix})$
		
		:::success
		**Review : Elementary Row Operation**
		1. Interchange
			
            $det(A') = -det(A)$
		2. Scaling
			
            $det(A') = kdet(A)$
		3. Row Addition
			
            $det(A') = det(A)$
		:::

## Determinants for Upper Triangular Matrix
$U = \begin{bmatrix} d_1 & \dots & * \\ \vdots & \ddots & \vdots \\ 0 & \dots & d_n \end{bmatrix}$

We can kill every components above diagonal by using elementary row operations

$det(U) = det(\begin{bmatrix} d_1 & \dots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \dots & d_n \end{bmatrix})\\
= d_1d_2 \dots d_ndet(\begin{bmatrix} 1 & \dots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \dots & 1 \end{bmatrix}) \qquad \texttt{(By point 3.a above)} \\
= d_1d_2 \dots d_n$

:::success
This property will also holds in Lower Triangular Matrix
:::

## Determinants v.s. Invertible
> If a matrix $A$ is invertible, then $det(A) \neq 0$

![](https://i.imgur.com/LX5SnG2.png)

- If $A$ is invertible, $R$ is identity
	
    $det(R) = 1 \to det(A) \neq 0$
- If $A$ is not invertible, $R$ has zero row
	
    $det(R) = 0 \to det(A) = 0$

:::success
Now we can add $det(A) \neq 0$ into our invertible collection!
![](https://i.imgur.com/7LOj6Xv.png)
:::

## More Properties of Determinants
- $det(AB) = det(A)det(B)$
	:::danger
	$det(A+B) \neq det(A) + det(B)$
	:::
	:::success
	$\because A^{-1}A = I \quad \therefore det(A^{-1})det(A) = det(I) = 1\\
	\because det(A^{-1}) = \frac{1}{det(A)}$
	
	Proof Again that A is invertible if and only if $det(A) \neq 0$
	:::
- $det(A^T) = det(A)$
	:::success
	Determinant of a matrix with Zero row equals to $0$
    
	$\to$ Zero column also holds
	Determinant of a matrix with Same row equals to $0$
    
	$\to$ Same column also holds
	:::

## Cramer's Rule
### Formula for $A^{-1}$
$A^{-1} = \frac{1}{det(A)}C^T \qquad C = \begin{bmatrix} c_{11} & \dots & c_{1n} \\ \vdots & \ddots & \vdots \\ c_{n1} & \dots & c_{nn} \end{bmatrix}$
- $det(A)$: scalar
- $C$: cofactors of $A$
- $C^T$ is adjugate of $A$ ($adj\ A$, 伴隨矩陣)

### Cramer's Rule
$Ax = b \quad x = A^{-1}b = \frac{1}{det(A)}C^Tb$

$x_1 = \frac{det(B_1)}{det(A)} \quad x_2 = \frac{det(B_2)}{det(A)} \quad \dots \quad x_j = \frac{det(B_j)}{det(A)}$

$B_j =$ with column $j$ replaced by $b$

###### tags: `線性代數筆記`