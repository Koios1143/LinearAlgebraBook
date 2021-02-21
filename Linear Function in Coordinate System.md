# Linear Function in Coordinate System

## Baisc Idea
Why we need to know how to represent in other coordinate system?

Because sometimes in other coordinate system, function can be **simpler** to understand

### Example
Reflect about a line $\mathscr{L}$ through the origin in $\mathscr{R}^2$

This problem seems to be hard in cartesian coordinate system
![](https://i.imgur.com/bWvbRj5.png)

How about change the coordinate system to make it simpler
![](https://i.imgur.com/jTgudy2.png)

:::info
In this kind of special case, we can easily find out what the $T'$ matrix is, and we can transform back to $T$
:::

## Describe function in another coordinate system
:::info
We denote $[T]_\mathscr{B}$ to describe a system $T$ in $\mathscr{B}$ coordinate system
:::

Reflection about a line $\mathscr{L}$ through the origin in $\mathscr{R}^2$
![](https://i.imgur.com/3LY36XG.png)

- $[T]_{b_1} = b_1$
	- $[T]_{\mathscr{B}}([b_1]_{\mathscr{B}}) = [b_1]_{\mathscr{B}}$
	- $[T]_{\mathscr{B}}(e_1) = e_1$
- $[T]_{b_2} = -b_2$
	- $[T]_{\mathscr{B}}([b_2]_{\mathscr{B}}) = [-b_2]_{\mathscr{B}}$
	- $[T]_{\mathscr{B}}(e_2) = -e_2$

$\Rightarrow [T]_{\mathscr{B}} = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}$

![](https://i.imgur.com/JOd3V3V.png)

![](https://i.imgur.com/Ze5DV0G.png)

Now we know how to represent $[T]_{\mathscr{B}}$, then we can transform between two coordinate system

$[T] = B[T]_{\mathscr{B}}B^{-1}$

$[T]_{\mathscr{B}} = B^{-1}[T]B$

:::info
We called two matrix A and B are **similar**, if there's a invertible matrix $P$, such that $PAP^{-1} = B$, $P^{-1}BP = A$
:::

### Example 1
Reflection operator $T$ about the line $y = \frac{1}{2} x$

![](https://i.imgur.com/0jAOCpI.png)

### Example 2
A known matrix $A$, we want to know $[T]_{\mathscr{B}}$

![](https://i.imgur.com/0vInJ2y.png)

### Example 3
![](https://i.imgur.com/WA5PcTV.png)

![](https://i.imgur.com/Q27D4Rs.png)


###### tags: `線性代數筆記`