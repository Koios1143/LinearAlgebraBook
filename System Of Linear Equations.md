# System of Linear Equations

```
Linear System = System of Linear Equations
```

## Definition
> The set of two or more equations containing multiple unknowns

$$a_{11}x_1 + a_{12}x_2 + a_{13}x_3 + ... + a_{1n}x_n = b_1 \\ a_{21}x_1 + a_{22}x_2 + a_{23}x_3 + ... + a_{2n}x_n = b_2 \\ . \\ .\\ . \\a_{m1}x_1 + a_{m2}x_2 + a_{m3}x_3 + ... + a_{mn}x_n = b_m
$$

We called $x_1, x_2, x_3, ... , x_n$ are variables

And $a_{11}, a_{12}, a_{1n}, a_{21}, a_{22}, a_{mn}$ are coefficents

### Terminology
- **Domain**
	
    The set of all values that can be entered to a function $f$
- **Co-domain**
	
    The set of all variables that can be output to a function $f$
- **Range**
	
    The values that can be output

:::success
Range must be contained in Co-doamin
:::

![](https://i.imgur.com/hmv45iT.png)

For example: $f(x) = x^2$


| Name      | Value              |
| --------- | ------------------ |
| Domain    | $\mathscr{R}$      |
| Co-Domain | $\mathscr{R}$      |
| Range     | $\mathscr{R}^+, 0$ |


- One-to-one
    
    No two inputs have the same output
- On-to
    
    Co-domain = range

![](https://i.imgur.com/lzEkmI9.png)

---

> It is obvious that Linear Equations is a Linear System
> 
> But, can all Linear System be represented by Linear Equations? (O)

***Proof***

Question: Can we represent $b_1 ~ b_m$ by $x_1 ~ x_m$ ?

we can construct with **standard (unit) vector**

- **standard (unit) vector**
    A vector with only one element is $1$, the others are $0$
    We use $e_m$ to represent a standard vector with only one element $1$ in position $m$

$$v = \begin{bmatrix} v1 \\ v2 \end{bmatrix} = v1 \begin{bmatrix} 1 \\ 0 \end{bmatrix} + v2 \begin{bmatrix} 0 \\ 1 \end{bmatrix} \\ = v1e_1 + v2e_2
$$

![](https://i.imgur.com/9DWngBF.png)

![](https://i.imgur.com/olL59JR.png)

1. **Persevering Multiplication**
	![](https://i.imgur.com/VN5lpSt.png)

2. **Persevering Addition**
	![](https://i.imgur.com/kPwRpqN.png)

:::success
Linear System = System of Linear Equations
:::

###### tags: `線性代數筆記`