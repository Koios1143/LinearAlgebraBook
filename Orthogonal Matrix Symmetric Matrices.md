# Orthogonal Matrix & Symmetric Matrices

## Norm-preserving
A linear operator is norm-preserving if
$$||T(u)|| = ||u|| \texttt{ For all } u
$$

- For example
	1. operator $T$ on $\mathscr{R}^2$ that rotates a vector by $\theta$ (O)
		
        $A_{\theta} = \begin{bmatrix} cos \theta & -sin \theta \\ sin \theta & cos \theta\end{bmatrix}$
	2. operator $T$ that reflect a vector (O)
		
        $A = \begin{bmatrix} 1 & 0 \\ 0 & -1 \end{bmatrix}$
	3. linear operator $T$ is projection (X)
		
        $A = \begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix}$
	4. linear operator $U$ on $\mathscr{R}^n$ that has an eigenvalue $\lambda \neq \pm 1$ (X)
		
        assume the corresponding eigenvector is $v$
		
        $||U(v)|| = ||\lambda v|| = |\lambda|\cdot||v|| \neq ||v||$

:::success
Every Norm-preserving operator have two properties
1. The Columns of the operator matrix are orthogonal
2. The operator matrix Columns are unit vector (length is $1$)
:::

## Orthogonal Matrix
An $n \times n$ matrix $Q$ is called an orthogonal matrix if the columns of $Q$ form an ***orthonormal basis*** for $\mathscr{R}^n$

An operator is called an orthogonal operator if its standard matrix is an orthogonal matrix

![](https://i.imgur.com/8D2EmWl.png)

---

:::success
***Norm-preserving*** is equivalent to ***Orthogonal matrix***
:::

:::info
An linear operator is norm-preserving, then its standard matrix is orthogonal matrix
:::

***Proof***

Linear operator $Q$ is norm-preserving
1. length is $1$
	
    $||q_i|| = 1$
	
    Because $Q$ is norm-preserving
	
    $||q_i|| = ||Qe_j|| = ||e_j||$
2. $q_i$ and $q_j$ are orthogonal, $i \neq j$
	
    $||q_i + q_j||^2 = ||Qe_i + Qe_j||^2 = ||Q(e_i + e_j)||^2$
	
    Because $Q$ is norm-preserving
	
    $||Q(e_i + e_j)||^2 = ||e_i + e_j||^2 = 2 = ||q_i||^2 + ||q_j||^2$
	
    $\Rightarrow ||q_i+q_j||^2 = ||q_i||^2 + ||q_j||^2$
	
    By Pythagorean theorem, $q_i$ and $q_j$ are orthogonal

:::info
$Q$ is an orthogonal matrix, then $Q$ is also a norm-preserving matrix
:::

- Properties
	- $Q^TQ = I_n$
	- $Q$ is invertible, and $Q^{-1} = Q^T$
	- $Qu \cdot Qv = u \cdot v$ for any $u$ and $v$
	- $||Qu|| = ||u||$ for any $u$

***Proof***

If $Q$ is an orthogonal matrix, $Q^TQ = I_n$

$$Q = \begin{bmatrix} u_1 & u_2 & \dots & u_n \end{bmatrix} \quad Q^T = \begin{bmatrix} u_1^T \\ u_2^T \\ \vdots \\ u_n^T\end{bmatrix} \quad Q^TQ = \begin{bmatrix} u_1^Tu_1 & u_1^Tu_2 & \dots & u_1^Tu_n\\ u_2^Tu_1 & u_2^Tu_2 & \dots & u_2^Tu_n \\ \vdots & \vdots & \ddots & \vdots  \\ u_n^Tu_1 & u_n^Tu_2 & \dots & u_n^Tu_n\end{bmatrix}
$$

Because $Q$ is an orthogonal matrix, $u_i^T \cdot u_j = 0$, elements on non-diagonal are $0$

$$Q^TQ = \begin{bmatrix}
u_1^Tu_1 & 0 & \dots & 0 \\ 0 & u_2^Tu_2 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & 0 & u_n^Tu_n\end{bmatrix}
$$

Because $Q$ is an orthogonal matrix, $u_i^Tu_i = ||u_i||^2 = 1$, elements on diagonal are $1$

$$Q^TQ = \begin{bmatrix}
1 & 0 & \dots & 0 \\ 0 & 1 & \dots & 0 \\ \vdots & \vdots & \ddots & \vdots \\ 0 & 0 & 0 & 1\end{bmatrix} = I_n
$$

$$\because Q^TQ = I_n \quad \therefore Q^{-1} = Q^T
$$

For every vector $u$ and $v$ in $\mathscr{R}^n$
$$Qu \cdot Qv = (Qu)^T \cdot Qv = u^TQ^T \cdot Qv = u^T \cdot v = u \cdot v
$$

Because $Qu \cdot Qv = u \cdot v$
$$||Qu||^2 = Qu \cdot Qu = ||u||^2\\
||Qu|| = ||u||
$$

:::success
***Norm-preserving*** is equivalent to ***Orthogonal matrix***
:::

### Properties
Let $P$ and $Q$ be $b \times n$ orthogonal matrices

1. $detQ = \pm 1$
2. $PQ$ is an orthogonal matrix
3. $Q^{-1}$ is an orthogonal matrix $\Leftrightarrow$ $Q^T$ is an orthogonal matrix

***Proof***

:::info
$PQ$ is an orthogonal matrix
:::

Because $P$ and $Q$ are orthogonal matrix, no matter which vector $u$ we input to $P$ or $Q$, the output length is also $||u||$

If we have a system $u \rightarrow P \rightarrow Q$, $||u||$ won't change

So, we can compose $P$ and $Q$ to a new matrix, which is also an orthogonal matrix

$$(PQ)^T = Q^TP^T = Q^{-1}P^{-1} = (PQ)^{-1}
$$

:::info
$Q^{-1}$ is an orthogonal matrix $\Leftrightarrow$ $Q^T$ is an orthogonal matrix
:::

$$||Qu|| = ||u||\\
\Rightarrow ||u|| = ||Q^{-1}u||
$$

Because $Q^{-1} = Q^T$, $Q^{-1}$ and $Q^T$ are orthogonal matrices

$$(Q^{-1})^{-1} = Q \quad (Q^{-1})^T = (Q^T)^T = Q\\
\Rightarrow (Q^{-1})^T = (Q^{-1})^{-1}
$$

:::info
$detQ = \pm 1$
:::

From a physical point of view, determinant means volume

Orthogonal matrix has Norm-preserving, every columns are orthogonal, and they're norm are $1$

no matter what, the volume is always $1^n = 1$

$$QQ^T = I_n\\
\Rightarrow det(I_n) = det(QQ^T) = det(Q)det(Q^T) = det(Q)det(Q)\\
= det(Q)^2\\
\Rightarrow det(Q) = \pm 1
$$

### Orthogonal Operator
Applying the properties of orthogonal matrices on orthogonal operators

$T$ is an orthogonal operator
- Preserves dot product
	$$T(u) \cdot T(v) = u \cdot v \texttt{ for all } u \texttt{ and } v
	$$
- Preserves norms
	$$||T(u)|| = ||u|| \texttt{ for all } u
	$$
- $T$ and $U$ are orthogonal operators, then $TU$ and $T^{-1}$ are orthogonal operators

***Example***

Find an orthogonal operator $T$ on $\mathscr{R}^3$ such that
$$T(\begin{bmatrix} 1/\sqrt{2} \\ 0 \\ 1/\sqrt{2} \end{bmatrix}) = \begin{bmatrix} 0 \\ 1 \\ 0\end{bmatrix}
$$

- Norm-Preserving
	$$||\begin{bmatrix} 1/\sqrt{2} \\ 0 \\ 1/\sqrt{2} \end{bmatrix}||  = ||\begin{bmatrix} 0 \\ 1 \\ 0\end{bmatrix}||
	$$

Assume $A$ is the orthogonal operator

$$v = \begin{bmatrix} 1/\sqrt{2} \\ 0 \\ 1/\sqrt{2} \end{bmatrix} \quad Av = e_2 \quad v = A^{-1}e_2
$$

$$A^{-1} = \begin{bmatrix} * & 1/\sqrt{2} & *
\\ * & 0 & * \\ * & 1/\sqrt{2} & *\end{bmatrix} = A^T\\
\Rightarrow A = \begin{bmatrix} * & * & * \\ 1/\sqrt{2} & 0 & 1/\sqrt{2} \\ * & * & *\end{bmatrix}
$$

Actually, there are infinity solutions, for example

$$A = \begin{bmatrix} 1/\sqrt{2} & 0 & -1/\sqrt{2} \\ 1/\sqrt{2} & 0 & 1/\sqrt{2} \\ 0 & 1 & 0 \end{bmatrix}
$$

## Symmetric matrix
### Eigenvalues
:::info
The eigenvalues for symmetric matrices are always ***real***
:::

Consider $2 \times 2$ symmetric matrices
$$A = A^T = \begin{bmatrix} a & b \\ b & c\end{bmatrix} \in \mathscr{R}^{2 \times 2}
$$

$$det(A - tI_2) = t^2 - (a + c)t + ac - b^2
$$

Since $(a + c)^2 - 4(ac - b^2) = (a-c)^2 + 4b^2 \geq 0$

The symmetric matrices always have real eigenvalues

> How about general cases?

Suppose we have a symmetric matrix $A$
$A$ have two eigenvalues $\lambda$ and $\bar{\lambda}$

$$Av = \lambda v \quad Aw = \bar{\lambda} w
$$
$$
w^TAv = w^T\lambda v = \lambda w^T v\\
\because A = A^T\\
\therefore w^TAv = w^TA^Tv = (Aw)^Tv = (\bar{\lambda}w)^Tv$$
$$\because (\bar{\lambda}w)^Tv = (\lambda w)^Tv\\
\therefore \lambda = \bar{\lambda}
$$

> $w^Tv$ might equal to $0$ ? (X)

$$\overline{Av} = \overline{\lambda v}\\
\because A \in \mathbb{R}\\
\therefore \overline{Av} = \overline{\lambda v} = A\overline{v} = \overline{\lambda v}
$$

We can find an eigenvalue $w$ that conjugate to $v$

$$v = \begin{bmatrix} v_1 \\ v_2 \\ \vdots \\ v_n\end{bmatrix} \quad w = \bar{v} = \begin{bmatrix} \bar{v_1} \\ \bar{v_2} \\ \vdots \\ \bar{v_n}\end{bmatrix}\\
w^T = \begin{bmatrix} \bar{v_1} & \bar{v_2} & \dots & \bar{v_n}\end{bmatrix}\\
w^Tv = \begin{bmatrix} \bar{v_1}v_1 + \bar{v_2}v_2 + \dots + \bar{v_n}v_n\end{bmatrix}
$$

$$v_i = a+bi \quad \bar{v_i} = a-bi\\
v_i\bar{v_i} = a^2 + b^2\\
\because v \neq \vec{0}\\
\therefore v_i\bar{v_i} > 0
$$

$$w^Tv \neq \begin{bmatrix} 0 \end{bmatrix}
$$

:::success
The eigenvalues for symmetric matrices are always ***real***
:::

### Eigenvectors
We can factorize $det(A - tI_n) = (t -\lambda_1)^{m_1}(t -\lambda_2)^{m_2} \dots (t -\lambda_k)^{m_k} (\dots$)

|            | $(t - \lambda _1)^{m_1}$ | $(t - \lambda _1)^{m_1}$ | $(t - \lambda _k)^{m_k}$ |
| ---------- | ------------------------ | ------------------------ | ------------------------ |
| Eigenvalue | $\lambda _1$             | $\lambda _2$             | $\lambda _k$             |
| Eigemspace | $d_1$ ($\leq m_1$)       | $d_2$ ($\leq m_2$)       | $d_k$ ($\leq m_k$)       |

vectors in different eigenspace $d_1, d_2, \dots, d_k$ must be independent

:::info
If $A$ is symmetric matrix, vectors in different eigenspace $d_1, d_2, \dots, d_k$ must be ***independent and orthogonal***
:::

Suppose $A$ is a symmetric matrix

If $u$ and $v$ are eigenvectors corresponding to eigenvalues $\lambda$ and $\mu$ ($\lambda \neq \mu$)

$$Au \cdot v = \lambda u \cdot v = \lambda (u \cdot v)\\
\because $A = A^T$\\
\therefore Au \cdot v = u \cdot A^Tv = u \cdot Av = u \cdot \mu v = \mu(u \cdot v)\\
$$

$$\because \lambda (u \cdot v) = \mu (u \cdot v) (\lambda \neq \mu)\\
\therefore u \cdot v = 0
$$

:::success
If $A$ is symmetric matrix, vectors in different eigenspace $d_1, d_2, \dots, d_k$ must be ***independent and orthogonal***
:::

### Diagonalization
If $A$ is symmetric, we must can find a matrix $D = P^TAP$

$P$ is an orthogonal matrix, $D$ is a diagonal matrix

***Proof***
:::info
$P$ is an orthogonal matrix

$D$ is a diagonal matrix

If we can find a matrix $A$ such that $P^TAP = D$

Then $A$ must be symmetric matrix
:::

Because $P$ is an orthogonal matrix
$$P^TAP = D \Rightarrow P^{-1}AP = D \\ 
\Rightarrow A = PDP^{-1} = PDP^T
$$

:::success
If we can find a matrix $A$ such that $P^TAP = D$

Then $A$ must be symmetric matrix
:::
:::success
If $A$ is a symmetric matrix, it must can be diagonalize
:::

***Example 1***

$A = \begin{bmatrix} 2 & -2 \\ -2 & 5\end{bmatrix}$

$A$ has eigenvalues $\lambda_1 = 6$ and $\lambda_2 = 1$, with corresponding eigenspace $\varepsilon_1 = Span\{\begin{bmatrix} -1 \\ 2 \end{bmatrix}\}$ and $\varepsilon_2 = Span\{\begin{bmatrix} 2 \\ 1 \end{bmatrix}\}$

$\begin{bmatrix} -1 \\ 2 \end{bmatrix}$ and $\begin{bmatrix} 2 \\ 1 \end{bmatrix}$ are orthogonal

$\Rightarrow \mathscr{B}_1 = \{\begin{bmatrix} -1 \\ 2 \end{bmatrix}/\sqrt{5}\} \quad \mathscr{B}_2 = \{\begin{bmatrix} 2 \\ 1 \end{bmatrix}/\sqrt{5}\}$ (normalization)

$$P = \frac{1}{\sqrt{5}}\begin{bmatrix} -1 & 2 \\ 2 & 1 \end{bmatrix} \quad D = \begin{bmatrix} 6 & 0 \\ 0 & 1 \end{bmatrix}
$$

***Example 2***
$$A = \begin{bmatrix} 4 & 2 & 2 \\ 2 & 4 & 2 \\ 2 & 2 & 4 \end{bmatrix} = PDP^{-1}
$$
$$\lambda_1 = 2 \quad \lambda_2 = 8
$$

- $\lambda_1$
	
    Eigenspace: $Span\{\begin{bmatrix} -1 \\ 1 \\ 0 \end{bmatrix}, \begin{bmatrix} -1 \\ 0 \\ 1 \end{bmatrix}\}$
	> independent, but not always orthogonal
	
	***Gram-Schmidt normalization***
	$Span\{\begin{bmatrix} -1/\sqrt{2} \\ 1/sqrt{2} \\ 0 \end{bmatrix}, \begin{bmatrix} 1/\sqrt{6} \\ 1/\sqrt{6} \\ -2/\sqrt{6} \end{bmatrix}\}$

- $\lambda_2$
	
    Eigenspace: $Span\{\begin{bmatrix} 1 \\ 1 \\ 1 \end{bmatrix}\}$
	> independent, but not always orthogonal
	
	***Gram-Schmidt normalization***
	$Span\{\begin{bmatrix} 1/\sqrt{3} \\ 1/\sqrt{3} \\ 1/\sqrt{3} \end{bmatrix}\}$

$$P = \begin{bmatrix} -1/\sqrt{2} & 1/\sqrt{6} & 1/\sqrt{3} \\ 1/\sqrt{2} & 1/\sqrt{6} & 1/\sqrt{3} \\ 0 & -2/\sqrt{6} & 1/\sqrt{3} \end{bmatrix} \quad D = \begin{bmatrix} 2 & 0 & 0 \\ 0 & 2 & 0 \\ 0 & 0 & 8 \end{bmatrix}
$$

---

Finding an orthonormal basis consisting of eigenvectors of $A$
1. Compute all distinct eigenvalues $\lambda_1, \lambda_2, \dots, \lambda_k$ of $A$
2.  Determine the corresponding eigenspaces $\varepsilon_1, \varepsilon_2, \dots, \varepsilon_k$
3.  Get an orthonormal basis $\mathscr{B}_i$ for each $\varepsilon_i$
4. $\mathscr{B} = \mathscr{B}_1 \cup \mathscr{B}_2 \cup \dots \cup \mathscr{B}_k$ is an orthonormal basis for $A$

We want to diagonalize a matrix $A$, in general, we need to follow the steps below
But now, $A$ is a symmetric matrix, the calculation will more easier

$P$ will be a orthonormal matrix, a orthonormal basis

That is, we can find a coordinate system, such that $[v]_{\mathscr{B}}$ is an orthonormal basis

![](https://i.imgur.com/QqG8Hb8.png)

### Spectral Decomposition
$$A = PDP^T \qquad P = \begin{bmatrix} u_1 & u_2 & \dots & u_n \end{bmatrix} \quad D = diag \begin{bmatrix} \lambda_1 & \lambda_2 & \dots & \lambda_n \end{bmatrix}
$$

$$
A = P\begin{bmatrix} \lambda_1e_1 & \lambda_2e_2 & \dots & \lambda_ne_n\end{bmatrix}P^T\\
= \begin{bmatrix} \lambda_1Pe_1 & \lambda_2Pe_2 & \dots & \lambda_nPe_n\end{bmatrix}P^T\\
= \begin{bmatrix} \lambda_1u_1 & \lambda_2u_2 & \dots & \lambda_nu_n\end{bmatrix}P^T\\
= \begin{bmatrix} \lambda_1u_1 & \lambda_2u_2 & \dots & \lambda_nu_n\end{bmatrix}\begin{bmatrix} u_1^T \\ u_2^T \\ \vdots \\ u_n^T\end{bmatrix}\\
= \lambda_1u_1u_1^T + \lambda_2u_2u_2^T + \dots + \lambda_nu_nu_n^T
$$

Let $P_i = u_iu_i^T$

$$A = \lambda_1P_1 + \lambda_2P_2 + \dots + \lambda_nP_n
$$

:::success
$P_i$ are symmetric

$Rank\ P_i = Rank\ u_iu^T = 1$
:::

:::info
Because $P$ is a orthogonal matrix, $u_i^Tu_i = 1$

$P_iP_i = u_iu_i^Tu_iu_i^T = u_iu_i^T = P_i$
:::

:::info
Because $P$ is a orthogonal matrix, $u_i^Tu_j = 0$

$P_iP_j = u_iu_u^Tu_ju_j^T = O$
:::

:::info
$P_iu_i = u_iu_i^Tu_i = u_i$

$P_iu_j = u_iu_i^Tu_j = \vec{0}$
:::

***Example***

$A = \begin{bmatrix} 3 & -4 \\ -4 & -3 \end{bmatrix}$ Find spectrum decomposition

Eigenvalues $\lambda_1 = 5$ and $\lambda_2 = -5$

An orthonormal basis consisting of eigenvectors of $A$ is
$$B = \{\begin{bmatrix} -2/\sqrt{5} \\ 1/\sqrt{5} \end{bmatrix}, \begin{bmatrix} 1/\sqrt{5} \\ 2/\sqrt{5} \end{bmatrix}\}
$$

$$P_1 = u_1u_1^T = \begin{bmatrix} \frac{4}{5} & \frac{-2}{5} \\ \frac{-2}{5} & \frac{1}{5} \end{bmatrix} \quad P_2 = u_2u_2^T = \begin{bmatrix} \frac{1}{5} & \frac{2}{5} \\ \frac{2}{5} & \frac{4}{5} \end{bmatrix} \quad A = \lambda_1P_1 + \lambda_2P_2
$$

---

:::success
Any symmetric matrix
- has only real eigenvalues
- has orthogonal eigenvectors
- is always diagonalizable

![](https://i.imgur.com/caJzim0.png)
:::

###### tags: `線性代數筆記`