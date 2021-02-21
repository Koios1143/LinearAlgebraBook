# PageRank

- Webpages with a higher PageRank are more likely to appear at the top of Google search results
- PageRank relies on the uniquely democratic nature of the web by using its vast link structure as an indocator of an individual page's value
- ***Google interprets a link from page A to page B as a vote, by page A, for page B***

![](https://i.imgur.com/oEw02eY.png)

## Formulas
![](https://i.imgur.com/5Zw7hTZ.png)

$$x_1 = x_3 + \frac{1}{2}x_4\\
x_2 = \frac{1}{3}x_1\\
x_3 = \frac{1}{3}x_1 + \frac{1}{2}x_2 + \frac{1}{2}x_4\\
x_4 = \frac{1}{3}x_1 + \frac{1}{2}x_2
$$

> How to calculate $x_n$ ?

$A = \begin{bmatrix} 0 & 0 & 1 & \frac{1}{2} \\ \frac{1}{3} & 0 & 0 & 0 \\ \frac{1}{3} & \frac{1}{2} & 0 & \frac{1}{2} \\ \frac{1}{3} & \frac{1}{2} & 0 & 0 \end{bmatrix} \quad x = \begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4 \end{bmatrix}$
$Ax = x$

> $x$ is eigenvector of $A$, $1$ is eigenvalue of $A$

> Does Column-stochastic matrix always have eigenvalue $\lambda = 1$ ?(O, if there's no webpage have zero hyperlink)

:::success
If every columns' sum of a matirx are all $1$, then it must have eigenvalue equals to $1$
:::

> Unique Ranking?

The dimension of the subspace is $1$ $\Rightarrow$ Unique Ranking $\Rightarrow$ Unique Score

> How about dimention > 1 ?

$A = \begin{bmatrix} 0 & 1 & 0 & 0 & 0 \\ 1 & 0 & 0 & 0 & 0 \\ 0 & 0 & 0 & 1 & \frac{1}{2} \\ 0 & 0 & 1 & 0 & \frac{1}{2} \\ 0 & 0 & 0 & 0 & 0 \end{bmatrix}$

Dim for $\lambda = 1$ is $2$

$\Rightarrow$ Not unique ranking

> So, how page rank solve this problem?

$$M = (1-m)A + mS
$$

There are two ways to surf the web
- Follow the link
	
    $A$
	
    ![](https://i.imgur.com/vprgSb3.png)
- Random
	
    $S$ All entries are $\frac{1}{n}$
	
    It may not be uniform, effect by ADs, etc
	
    ![](https://i.imgur.com/bCMChkH.png)

Then we can make sure the dimension of eigenvalue $\lambda = 1$ is $1$
	
> How to find out eigenvector quickly?
	
***Power method***
- Find $x^*$, such that $x^* = Mx^*, ||x^*||_1 = 1$
- start from $x_0, ||x_0||_1 = 1$
- $x_1 = Mx_0 \\ x_2 = Mx_1 \\ \vdots \\ x_k = Mx_{k-1}$
- If $k \to \infty$ $x_k = x^*$
	
	
	
	
###### tags: `線性代數筆記`