# HW4 - Page Rank

Page Rank is an algorithm to measure the importance of a website

## Algorithm
If we have four websites $A, B, C, D$

![](https://i.imgur.com/g49eEwU.png)

If we want to calculate PageRank of $A$

$$PR(A) = (\frac{PR(B)}{2} + \frac{PR(C)}{1} + \frac{PR(D)}{3})d + \frac{1-d}{4}
$$

$\frac{PR(B)}{2}$'s Denominator is $2$, because there are two lines from $B$ to other websites

In General:

$$PageRank(p_i) = \frac{1-d}{N} + d \sum_{p_j \in M(p_i)}{\frac{PageRank(p_j)}{L(p_j)}}
$$

Let $R = \begin{bmatrix} PageRank(p_1) \\ PageRank(p_2) \\ \vdots \\ PageRank(p_N)\end{bmatrix}$

The way we transfer $R$ is:

$$R' = \begin{bmatrix} (1-d)/N  \\ (1-d)/N \\ \vdots \\ (1-d)/N \end{bmatrix} + d \begin{bmatrix} l(p_1, p_1)/L(p_1) & l(p_1, p_2)/L(p_2) & \dots & l(p_1, p_N)/L(p_N) \\
l(p_2, p_1)/L(p_1) & \ddots & \ddots & \vdots \\
\vdots & \ddots & \ddots & \vdots \\
l(p_N, p_1)/L(p_1) & \dots & \dots & l(p_N, p_N)/L(p_N)\end{bmatrix}\\
l(p_i, p_j)\begin{cases} 1 \quad p_j\texttt{ has a link to } p_i \\ 0 \quad \texttt{else} \end{cases} \qquad \texttt{Repeat until } R' \approx R
$$

## Solution

```python=
import sys
import numpy as np
import pandas as pd

def load(fname):
        # if i has a line to j, ret[j][i] = 1
        # else ret[j][i] = 0
        f = open(fname, 'r').readlines()
        n = len(f)
        ret = {}
        for l in f:
                l = l.split('\n')[0].split(',')
                i = int(l[0])
                ret[i] = {}
                for j in range(n):
                        if str(j) in l[1:]:
                                ret[i][j] = 1
                        else:
                                ret[i][j] = 0
        ret = pd.DataFrame(ret).values
        return ret


def get_tran(g, L):
        N = len(g)
        ret = np.zeros((N, N))
        for i in range(N):
                for j in range(N):
                        ret[i][j] = g[i][j]/L[j]
        return ret

def cal_rank(t, d = 0.85, max_iterations = 1000, alpha = 0.001):
        N = len(t)
        R = np.zeros((N, 1))
        M = np.zeros((N, 1))
        for i in range(N):
                R[i][0] = 1.0/N
                M[i][0] = (1.0-d)/N
        # Repeat until R approx R0
        for i in range(1, N):
                R0 = R
                R = M + (d*t).dot(R)
                max_iterations -= 1
                if(dist(R0, R)<=alpha or max_iterations<=0):
                        break
        return R

def save(t, r):
        # use %.5f to prevent scientific notation
        np.savetxt('s1_.txt', t, delimiter = ',', fmt = '%.5f')
        np.savetxt('s2_.txt', r, delimiter = ',', fmt = '%.5f')

def dist(a, b):
        return np.sum(np.abs(a-b))

def main():
        graph = load(sys.argv[1])
        N = len(graph)

        # Build L matrix recorded the number of lines starts from i
        L = np.zeros(N)
        for i in range(N):
                for j in range(N):
                        if(graph[j][i] == 1):
                                L[i]+=1

        transition_matrix = get_tran(graph, L)
        rank = cal_rank(transition_matrix, max_iterations = N)
        save(transition_matrix, rank)
if __name__ == '__main__':
        main()
```

###### tags: `線性代數筆記`