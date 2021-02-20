# Matrix Multiplication

## Review
Given two matrices $A$ and $B$, the $(i,j)-entry$ of $AB$ is the inner product of **row $i$ of $A$** and **column $j$ of $B$**

![](https://i.imgur.com/B1fFdcf.png)

## Another 3 ways to calculate matrix multiplication
### 1. Linear combination of columns
![](https://i.imgur.com/4FrY9rg.png)

:::info
For example
![](https://i.imgur.com/wv7Le8M.png)
:::

- Multiple input
	![](https://i.imgur.com/UfPKzQr.png)
	:::success
	In other words
    
	we view the matrix $A$ as a coefficient, and we have multiple input $b_n$, combine every $Ab_n$ will get the result column $C=AB$
	:::
- Composition

	Given two functions $f$ and $g$, the function $g(f())$ is the composition $g \circ f$
    
	that is, $y = g(f(x))$
	![](https://i.imgur.com/kBLGb1W.png)

	:::success
	- we input $x$ to $B$
		
        $v = Bx$
	- then we input $v$ to $A$
		
        $y = Av$
	- lastly, we get a matrix $C$
		
        $C=AB$
		
        $y = Cx = ABx$
	
	![](https://i.imgur.com/OIO8fng.png)
	:::

### 2. Linear combination of rows
![](https://i.imgur.com/YbmLQwa.png)
:::info
For example
![](https://i.imgur.com/TyVgSHB.png)
:::

### 3. Summation of matrices
![](https://i.imgur.com/WlCTFq3.png)
:::info
For example
![](https://i.imgur.com/QUiMN48.png)
And these matrices' Rank are the same
:::

#### Block Multiplication
we can split matrix $A$ and $B$ in any way we want

just make sure that the splited matrixes in $A$ and $B$ can multiple

that is, numbers of columns of $A_i$ is same as numbers of rows of $B_j$

![](https://i.imgur.com/lemRgTX.png)

:::info
For example
![](https://i.imgur.com/66ops8Z.png)
:::

:::success
In general, if we have two matrix $A_{mn}$, $B_{np}$

$C_{mp} = AB = \begin{split} \sum_{x=1}^{n}{A_{mx}B_{xp}} \end{split}$
:::

If we use block multiplication wisely, it might Simplified calculation
![](https://i.imgur.com/0nnPOVG.png)

---

## Properties
### Not communicative
- $AB \neq BA$

![](https://i.imgur.com/Lh9bHde.png)

:::success
If $A$ and $B$ are matrices, then both $AB$ and $BA$ are defined if and only if $A$ and $B$ are **square matrix** ? (X)

---
**Sol**
if $A$ is $m \times n$ matrix, and $B$ is $n \times p$ matrix, then the condition might be established
:::

### General properties
> Let $A$ and $B$ be $k \times n$ matrices, $C$ be an $m \times n$ matrix, and $P$ and $Q$ be $n \times p$ matrices, and $N$ is any matrix

- For any scalars $s$, $s(AC) = (sA)C = A(sC)$
- $(A+B)C = AC + BC$
- $C(P+Q) = CP + CQ$
- $I_kA = A = AI_m$
- $NO = O$

Power of square matrices $A \in \mathscr{M}_{n \times n}$, $A^k = AA \dots A$ ($k$ times)
$A^1 = A$, $A^0 = I_n$

> Let $A$ be $k \times m$ matrices, $C$ be an $m \times n$ matrix

- $(AC)^T = C^TA^T\neq A^TC^T$
	if $k \neq n$, then it'll never exist

## Special matrix
### Diagonal matrix
![](https://i.imgur.com/eeQBb7M.png)

### Symmetric matrix
$A^T = A$

$AA^T$ and $A^TA$ are square and symmetric

$(AA^T)^T = A^{TT}A^T = AA^T$

$(A^TA)^T = A^TA^{TT} = A^TA$

## Practical Issue
> Althought we can choose which two matrices to multiple first, and get the same result in the end
> 
> But the Computational magnitude might be far different

> Let $A$ and $B$ be $k \times m$ matrices, $C$ be an $m \times n$ matrix, and $P$ and $Q$ be $n \times p$ matrices

![](https://i.imgur.com/PO9itBr.png)

### GPU
![](https://i.imgur.com/UxlzpEJ.png)


###### tags: `線性代數筆記`