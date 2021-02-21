# Subspaces associated with Matrix

## Column Space
Let $A$ be a $m \times n$ matrix

$Col\ A$ is in $\mathscr{R}^m$

![](https://i.imgur.com/BDUFoyM.png)

- Basis
	
    The pivot columns of $A$ form a basis for $Col\ A$
- Dimension
	
    $Dim(Col\ A) =$ number of pivot columns $= Rank\ A$
	
### Revisit Rank
- Rank =
	- Maximum number of Independent Columns
	- Number of Pivot Columns
	- Number of Non-zero rows
	- Number of Basic Variables
	- $Dim(Col\ A)$: dimension of column space
	- Dimension of the range of $A$

## Null Space
Let $A$ is a $m \times n$ matrix

$Null\ A$ is in $\mathscr{R}^n$

![](https://i.imgur.com/jj3JBvq.png)

- Basis
	
    Eash free variable in the parametric representation of the general solution is multiplied by a vector form the basis
	![](https://i.imgur.com/TiSVGrR.png)
	![](https://i.imgur.com/KtouKX2.png)

- Dimension
	$Dim(Null\ A) =$ number of free variables $= Nullity\ A = n - Rank\ A$

## Row Space
Let $A$ be a $m \times n$ matrix

$Row\ A$ is in $\mathscr{R}^n$

- Basis
	
    Non-zero rows of $RREF(A)$
	![](https://i.imgur.com/noCSrLj.png)
	$Row\ A = Row\ R$
	:::success
	The elementary row operations do not change the row space.
	:::

- Dimension
	
    $Dim(Row\ A) =$ number of non-zero rows $= Rank\ A$

---

:::success
$Dim(Col\ A) = Dim(Row\ A) = Rank\ A$
:::

:::success
> $Rank\ A = Rank\ A^T$

$Rank\ A \\= Dim(Col\ A) \\= Dim(Row\ A) \\= Dim(Col\ A^T) \\= Rank\ A^T$
:::

## Dimension Theorem
> $Dim$ of Range + $Dim$ of Null = $Dim$ of Domain

$Dim$ of Range = $Dim(Col\ A) = Rank\ A$

$Dim$ of Null = $Dim(Row\ A) = n - Rank\ A$

$Dim$ of Domain = $Dim(\mathscr{R}^n) = n$

$\to Dim$ of Range + $Dim$ of Null = $Dim$ of Domain

![](https://i.imgur.com/glpqamj.png)

## Summary

|           | Dimension             | Basis                                                                    |
| --------- | --------------------- | ------------------------------------------------------------------------ |
| $Col\ A$  | $Rank\ A$             | The pivot columns of $A$                                                 |
| $Null\ A$ | $Nullity\ A$          | The vectors in the parametric representation of the solution of $Ax = 0$ |
| $Row\ A$  | $Rank\ A^T = Rank\ A$ | The non-zero rows of the $RREF(A)$                                       |

###### tags: `線性代數筆記`