# Solving System of Linear Equations

## Equivalent
Two systems of linear equations are *equivalent* if they have exactly **the same solution set.**

![](https://i.imgur.com/dtKtN5O.png)

Three ways to produce an equivalent one

1. ***Interchange***
	> Interchange any two rows of the matrix

	![](https://i.imgur.com/AKqt0BL.png)
2. ***Scaling***
	> Multiply every entry of some row by the same **nonzero** scalar
	
	![](https://i.imgur.com/jFvyq8v.png)
3. ***Row Addition***
	> Add a multiple of one row of the matrix to another row
	
	![](https://i.imgur.com/kPK35Gv.png)

we want to use these three ways to make a system of linear equations simpler, and doesn't effect the solution at the same time

## Augmented Matrix
we can use Augmented Matrix to represent a system of linear equations
![](https://i.imgur.com/Iam42gb.png)

Transfer to an augmented matrix to clarify the calculation
![](https://i.imgur.com/gGlXauO.png)

Target: make a complex system into ***RREF***(reduced row echelon form)
![](https://i.imgur.com/7oHAgef.png)

## RREF(Reduced Row Echelon Form)
we denotes $R$ to represent a RREF matrix
### Definition of Row Echelon Form
1. Each nonzero row lies above every zero row
    $$\begin{bmatrix} 0 & 0 \\ 1 & 0 \end{bmatrix} \texttt{(X)} \qquad \begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix} \texttt{(O)}
		$$
	
2. The leading entries are in echelon form
	> echelon means *a particular level or group of people within an organization such as an army or company*
	
    That is, every first non-zero component in the rows, they're positions are decreasing
    
    $$\begin{bmatrix} 0 & 1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 1 \end{bmatrix} \texttt{(X)} \qquad 
\begin{bmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{bmatrix} \texttt{(O)}
		$$
    
### Definition of Reduce Row Echelon Form
1. The matrix is in row echelon form
2. The columns containing the leading entries are standard vectors
	
    That is, the column with the component, which is the first non-zero component in the row is standard vectors
    
    ![](https://i.imgur.com/BY5iex9.png)

### Properties
:::success
RREF is unique
:::

![](https://i.imgur.com/exKgEBK.png)

***Proof by ULETHA*** https://www.cs.uleth.ca/~holzmann/notes/reduceduniq.pdf

### Pivot

![](https://i.imgur.com/2OqOiqQ.png)

- Pivot positions
	> the positions of leading entry in $R$
	
	The pivot positions of $A$ are $(1,1)$, $(2,3)$ and $(3,4)$.
- Pivot columns
	> the columns of leading entry in $R$
	
	The pivot columns of $A$ are 1st, 3rd and 4th columns

### Solve problem with RREF
***Example 1: Unique Solution***
![](https://i.imgur.com/53Jnmyx.png)

***Example 2: Infinite Solution***
![](https://i.imgur.com/PZWoK4J.png)

> Particularly, we called $x_1, x_3, x_5$ *Basic variables*
> And $x_2, x_4$ are *Free variables*

:::success
With free variables, there are infinitely solutions.
:::

:::success
**Parametric Representation**
$$\begin{bmatrix}x_1 \\ x_2 \\ x_3 \\ x_4 \\ x_5\end{bmatrix} = \begin{bmatrix} 7+3x_2-2x_4 \\ x_2 \\ 9-6x_4 \\ x_4 \\ 2\end{bmatrix} = \begin{bmatrix} 7 \\ 0 \\ 9 \\ 0 \\ 2\end{bmatrix} + x_2\begin{bmatrix} 3 \\ 1 \\ 0 \\ 0 \\ 0\end{bmatrix} + x_4\begin{bmatrix} -2 \\ 0 \\ -6 \\ 1 \\ 0\end{bmatrix}
$$
:::

***Example 3: No Solution***
![](https://i.imgur.com/HEDX95L.png)

:::success
When an argumented matrix contains a row in which **the only nonzero entry lies in the last column**
:::

---

![](https://i.imgur.com/jFkNE7t.png)

:::info
Because RREF matrix is unique, so there's no need to completely follow the steps of Gaussian Elimination

Just use **Elementary row operations** to transfer to RREF matrix 
:::

## Gaussian Elimination
Papper of Gaussian Elimination http://www.ams.org/notices/201106/rtx110600782p.pdf

***Example 1***
$$\begin{cases} x_1 + 2x_2 - x_3 + 2x_4 + x_5 = 2 \\
-x_1 - 2x_2 + x_3 + 2x_4 + 3x_5 = 6 \\
2x_1 + 4x_2 - 3x_3 + 2x_4 = 3 \\
3x_1 - 6x_2 + 2x_3 + 3x_5 = 9\end{cases}
$$

- write down augmented matrix
	$$\begin{bmatrix} 1 & 2 & -1 & 2 & 1 & 2 \\
	-1 & -2 & 1 & 2 & 3 & 6 \\
	2 & 4 & -3 & 2 & 0 & 3 \\
	-3 & -6 & 2 & 0 & 3 & 9
	\end{bmatrix}
	$$
- use elementary row operations to transfer to RREF, Just like using Gaussian Elimination
	$$\begin{bmatrix}1 & 2 & 0 & 0 & -1 & -5 \\
	0 & 0 & 1 & 0 & 0 & -3 \\
	0 & 0 & 0 & 1 & 1 & 2 \\
	0 & 0 & 0 & 0 & 0 & 0 \end{bmatrix}
	$$
- Turn back to system of linear equations
	$$\begin{cases} x_1 + 2x_2 - x_5 = -5\\
	x_3 = -3\\
	x_4 + x_5 = 2\end{cases}
	$$
- Get solution
	$$\begin{cases} x_1 = -5 -2x_2 + x_5 \\
	x_2 = \texttt{free} \\
	x_3 = -3 \\
	x_4 = 2-x_5 \\
	x_5 = \texttt{free}\end{cases}
	$$
- Use Parametric representation
	$$\begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \\ x_5 \end{bmatrix} = \begin{bmatrix} -5-2x_2+x_5 \\ x_2 \\ -3 \\ 2-x_5 \\ x_5 \end{bmatrix} = x_2 \begin{bmatrix} -2 \\ 1 \\ 0 \\ 0 \\ 0 \end{bmatrix} + x_5 \begin{bmatrix} 1 \\ 0 \\ 0 \\ -1 \\ 1 \end{bmatrix} + \begin{bmatrix} -5 \\ 0 \\ -3 \\ 2 \\ 0 \end{bmatrix}
	$$

:::success
There's no need to follow every step of Guassian Elimination

That's just one of the operation methods
:::

***Example 2***

$$\begin{bmatrix} 1 & 0 & -3 & 0 \\
0 & 1 & 2 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0 \\
2 & 0 & -6 & 0 \\
0 & 2 & 4 & 0 \\
0 & 0 & 0 & 2 \\
0 & 0 & 0 & 0 \end{bmatrix}
$$

- we define the upper matrix is $R$
	$$R = \begin{bmatrix} 1 & 0 & -3 & 0 \\ 0 & 1 & 2 & 0 \\ 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0\end{bmatrix}
	$$
- we found that the lower matrix is two times than the upper one
	![](https://i.imgur.com/mFgxqQS.png)
- then we get the answer
	$$\begin{bmatrix} 1 & 0 & -3 & 0 \\
	0 & 1 & 2 & 0 \\
	0 & 0 & 0 & 1 \\
	0 & 0 & 0 & 0 \\
	0 & 0 & 0 & 0 \\
	0 & 0 & 0 & 0 \\
	0 & 0 & 0 & 0 \\
	0 & 0 & 0 & 0 \end{bmatrix}
	$$

***Example 3***
$$\begin{bmatrix} 1 & 0 & -3 & 0 & 0 & 0 & 0 & 0 \\ 0 & 1 & 2 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 1 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 0 & 1 & 0 & -3 & 0 \\ 0 & 0 & 0 & 0 & 0 & 1 & 2 & 0 \\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 \\ 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \end{bmatrix}
$$

$$R = \begin{bmatrix} 1 & 0 & -3 & 0\\
0 & 1 & 2 & 0\\
0 & 0 & 0 & 1\\
0 & 0 & 0 & 0\end{bmatrix}
$$

$$\begin{bmatrix} R & O \\ O & R\end{bmatrix}
$$

:::success
應用之道，存乎一心
:::

## Checking Independence
:::info
**Review**

we have a system of linear equations
- we turn these equations into $Ax=b$
	- $A$ is a matrix of equations' scalars
	- $x$ is a vector of $x$s
	- $b$ is a vector of all answer

now if $b$ is in $Span\ A$, then:
- Dependent
	If we can find some scalars $x_1, x_2, x_3, \dots, x_n$ that **non all zero**, such that $x_1a_1 + x_2a_2 + \dots + x_na_b = 0$
	
- Independent
	If we can only find scalars **all zero**, such that $x_1a_1 + x_2a_2 + \dots + x_na_b = 0$
:::

> using Guassian Elimination to solve it

- Transfer the vector set $S$ into a matrix $A$
	$$S = \{ \begin{bmatrix} 1 \\ 2 \\ 1 \end{bmatrix}, \begin{bmatrix} 1 \\ 0 \\ 1 \end{bmatrix}, \begin{bmatrix} 1 \\ 4 \\ 1 \end{bmatrix}, \begin{bmatrix} 1 \\ 2 \\ 3 \end{bmatrix}\}\\
	A = \begin{bmatrix} 1 & 1 & 1 & 1 \\
	2 & 0 & 4 & 2 \\
	1 & 1 & 1 & 3\end{bmatrix}
	$$
- Transfer $Ax = 0$ into an augmented matrix
	$$\begin{bmatrix} 1 & 1 & 1 & 1 \\
	2 & 0 & 4 & 2 \\
	1 & 1 & 1 & 3\end{bmatrix} \begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix} = \begin{bmatrix} 0 \\ 0 \\ 0\end{bmatrix}
	$$
- Using Guassian Elimination to transfer $Ax=0$ into a RREF matrix
	$$\begin{bmatrix} 1 & 1 & 1 & 1 & 0 \\
	2 & 0 & 4 & 2 & 0 \\
	1 & 1 & 1 & 3 & 0\end{bmatrix} \overrightarrow{\texttt{RREF}} \begin{bmatrix} 1 & 0 & 2 & 0 & 0 \\ 0 & 1 & -1 & 0 & 0 \\ 0 & 0 & 0 & 1 & 0 \end{bmatrix}
	$$
- Get solution
	$$\begin{cases} x_1 + 2x_3 = 0 \\ x_2 - x_3 = 0 \end{cases} \Rightarrow \begin{cases} x_1 = -2x_3 \\ x_2 = x_3 \\ x_3 = \texttt{free} \\ x_4 = 0 \end{cases}\\
	\begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix} = \begin{bmatrix} -2x_3 \\ x_3 \\ x_3 \\ 0 \end{bmatrix} = x_3 \begin{bmatrix} -2 \\ 1 \\ 1 \\ 0\end{bmatrix}
	$$

###### tags: `線性代數筆記`