# Vector

A Vector is a set of numbers

- Components: the entries of a vector
	- the i-th components of the vector **V** refers to $v_i$

- Column Vector
	$$v = \begin{bmatrix} 1 \\ 2 \\ 3\end{bmatrix}
	$$
- Row Vector
	$$v = \begin{bmatrix} 1 & 2 & 3 \end{bmatrix}
	$$

:::info
In linear algebra, we usually use Column vector
:::

## Vector Set
A set of vector can contain infinite elements

For example

$$L=\{\begin{bmatrix} x_1 \\ x_2\end{bmatrix} : x_1 + x_2 = 1\}
$$

![](https://i.imgur.com/N9NqtuX.png)

:::success
We denote the set of all **vectors** with n entries by $\mathscr{R}^n$
:::

## Properties
### Scalar Multiplication
$$v = \begin{bmatrix} v_1 \\ v_2 \end{bmatrix} \quad cv = \begin{bmatrix} cv_1 \\ cv_2 \end{bmatrix}
$$

### Vector Addition
$$V_a = \begin{bmatrix} a_1 \\ a_2 \end{bmatrix} \quad V_b = \begin{bmatrix} b_1 \\ b_2 \end{bmatrix} \quad V_a + V_b = \begin{bmatrix} a_1 + b_1 \\ a_2 + b_2 \end{bmatrix}
$$

## Definition
> For any vectors $u$, $v$ and $w$ in $\mathscr{R}^n$, and any scalars $a$ and $b$

- $u + v = v + u$
- $(u + v) + w = u + (v + w)$
- There is an element $0$ in $\mathscr{R}^n$ such that $0 + u = u$
- There is an element $u'$ in $\mathscr{R}^n$ such that $u' + u = 0$
- $1u = u$
- $(ab)u = a(bu)$
- $a(u + v) = au + av$

**Above are the Real Definition of vector!**

###### tags: `線性代數筆記`