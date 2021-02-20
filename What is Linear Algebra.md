# What is Linear Algebra?

## System
```
A system has input and output
a.k.a function, transformation, operator
```
### Example
- Speech Recognition System
	- input : voice
	- output : words
- Dialogue System
	- input : Sentences
	- output : Responce Sentences
- Communication System
	- input : Your voice from your phone
	- output : Your voice to others' phone

> In Linear Algebra, we are concerned about **Linear** system

## Definition
A Linear System needs to meet two necessary conditions
1. Presevering Multiplication
	
    When input multiply by $k$, output multiply by $k$ at the same time
	
    一分耕耘，一分收獲; 兩分耕耘，兩分收獲
	
    ![](https://i.imgur.com/qvR4gid.png)

2. Presevering Addition
	
    When two inputs are added, the output are added at the same time
	
    種瓜得瓜，種豆得豆; 種瓜豆得瓜豆
	
    ![](https://i.imgur.com/Y6WOfuW.png)

Inputs are not limited to numbers, it can also be vector, matrix, graph, ...

From vector's point of view

1. Presevering Multiplication
	![](https://i.imgur.com/jfnB5jQ.png)

2. Presevering Addition
	![](https://i.imgur.com/vkq6XEu.png)

### Example

- ![](https://i.imgur.com/LSDf6WH.png)
    - Preserving Multiplication
        ![](https://i.imgur.com/XTDCx0W.png)
    - Preserving Addition
        ![](https://i.imgur.com/f5scopd.png)

    **Non Linear**

- ![](https://i.imgur.com/yrV3j3M.png)
    - Preserving Multiplication
        ![](https://i.imgur.com/3lNXoMY.png)
    - Preserving Addition
        ![](https://i.imgur.com/tM4R7R5.png)

    **Linear**

- ![](https://i.imgur.com/LsfMjDk.png)
    - Preserving Multiplication
    - Preserving Addition
    ![](https://i.imgur.com/Mp8NREm.png)

    **Linear**

- ![](https://i.imgur.com/CUrD3Wr.png)
    - Preserving Multiplication
        ![](https://i.imgur.com/Vn319Sa.png)
    - Preserving Addition
        ![](https://i.imgur.com/QwJF3gx.png)
    **Linear**

:::success
From examples above, we can know that even a complicated system like *differential*, *integral* are also holds the definition of linear, all **Linear System**
:::

## More Example
- Circuits
	![](https://i.imgur.com/aQshpz7.png)
- Signal Tranform system
	![](https://i.imgur.com/UutadDo.png)

## 現實生活中的應用
- Google Search engine
	Page Rank
- Computer Graphics
	Rotate the graph

## What we're going to learn

### Chapter 1, 2
Can we find out input when given output and the linear system?

If we find a solution, will that be the only solution? or there will be infinte solutions?

And how to find the solution?

![](https://i.imgur.com/f39tHUL.png)

### Chapter 3
**Determinant**
How to find out determinant when it is more than $3 \times 3$

### Chapter 4
How to describe a vector set?

subspace, basis, dimension

![](https://i.imgur.com/qyjzsgD.png)

### Chapter 5, 6, 7
How to describe the signature of a linear system?

How to find input when given a output

If there's no solution, how to get close to the input

![](https://i.imgur.com/ZimVGGS.png)

###### tags: `線性代數筆記`