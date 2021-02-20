# HW1 - Cycle Detection

## Question
Given a directed graph, find whether there's any cycle in the graph or not

## Using Row Addition
In this problem, we need to find out whether the directed graph has cycle or not, with **only matrix row addition**

And we can proof that, when there's any row are all-zero, then there's a cycle in the graph

### How?
1. select edge from head to end
2. find out start point $s$ and end point $e$
3. find another edge, which start point is $e$
4. Do row Addition of these edges
5. back to step 1

### Why?
Every time we do row addition, we make every edge point to next dot

For Example:
![](https://i.imgur.com/3nAc1GA.png)
Let's look at first row, $2$ point to $1$
We can find every edge(row), which start at point $1$

$1 \rightarrow 0$ and $1 \rightarrow 3$

Because our first end point's value is $1$, and new start point's value is $-1$, first start point and new end point don't changed

So, after row addition, we get $2 \rightarrow 0$ and $2 \rightarrow 3$

![](https://i.imgur.com/zMY6h7b.png)

:::info
Every time we do row addition, we repoint our edges to next point
:::

Back to the definition of cycle, the simpliest cycle graph is compose by two dots like this

![](https://i.imgur.com/GxIBRyY.png)


What does this graph looks like in array?
Look at red numbers

![](https://i.imgur.com/uWEqmxG.png)

What will happened after Row Addition?
It becomes to zero row! $[0, 0, 0, 0]$

:::success
After Row Addition, if there's any zero row, there's a cycle in graph
:::

### Solve
```python=
import numpy as np
import random
import matplotlib.pyplot as plt
import networkx as nx
import sys

def generate_graph(N, M):
        ret = np.zeros((N, M))
        for i in range(N):
                a, b = random.sample(range(M), 2)
                ret[i][a] = -1
                ret[i][b] = 1
        return ret

def plot_graph(data, path):
        N = len(data)
        G = nx.DiGraph()
        for i in range(N):
                G.add_node(chr(48+i))
        for i in range(N):
                start = int(np.where(data[i] == -1)[0])
                end = int(np.where(data[i] == 1)[0])
                G.add_edge(chr(48+start), chr(48+end))
        nx.draw_networkx(G, nx.spring_layout(G), arrows = True, cmap = plt.get_cmap('jet'), node_size = 1200)
        plt.savefig(path)

def has_cycle(G):
        N = len(G)
        M = len(G[0])
        for row in range(N):
                if(np.array_equal(G[row], np.zeros(M, dtype = 'i'))):
                        return True
                print(G[row])
                start = int(np.where(G[row] == -1)[0])
                end = int(np.where(G[row] == 1)[0])
                for i in range(N):
                        if(G[i][end] == -1):
                                # find next point
                                G[i] += G[row]
                                if(np.array_equal(G[i], np.zeros(M, dtype = 'i'))):
                                        return True
        return False

if __name__ == '__main__':
        N = int(sys.argv[1])
        M = int(sys.argv[2])
        G = generate_graph(N, M)
        #G = np.array([[0, 0, -1, 1, 0, 0], [0, 1, 0, 0, -1, 0], [0, 0, 0, -1, 0, 1], [0, 0, 1, 0, 0, -1], [-1, 1, 0, 0, 0, 0]]) # Graph for test
        plot_graph(G, './graph.png')
        print(has_cycle(G))
```

![](https://i.imgur.com/wVsywQM.png)

		False

## Using Matrix Multiplication
In this problem, you need to find out whether the directed graph has cycle or not, with **only matrix multiplication**

And you can proof that, if there's any non-zero component in the diagonal, then it has cycle

### Input
Given a adjecency matrix, if $arr[i][j] = 1$, there's a connection from $i$ to $j$
$0$ otherwise

### How?
1. Record the ordinal adjecency matrix $R$ with $N$ columns and rows
2. $R' = R$
3. $R' = R' \cdot R$
4. Repeat Step 3 at most $N$ times
	If there's any non-zero number appear on diagonal of $R'$, there's a cycle

### Why?
Every time when we dot $R'$ with $R$, we actually repoint every nodes to next point

For Example

Our ordinal matrix $R$ is

![](https://i.imgur.com/ndXtPGM.png)

Look at row 1, there's an edge from $0 \rightarrow 2$

Now look at col 2, there's an edge from $2 \rightarrow 1$

So, when we apply dot operation on row 1 and col 2, it denote $1$ on $R'(0, 1)$, which means there's an edge from $0 \rightarrow 1$

That is, if we have a row means there's an edge $A \rightarrow B$

At the same time, there's column means there's an edge $B \rightarrow C$

After matrix multiplication, we'll have an edge $A \rightarrow C$

:::info
Every time we do matrix multiplication, we repoint every edges to next point
:::

Back to the definition of cycle graph, we can take the simpliest cycle graph here for example

![](https://i.imgur.com/ltt2Fpj.png)

If there's an edge is a loop, what does it looks like in matrix?

There will be a $1$ on diagonal

:::success
If there's any non-zero number appears in diagonal, there's a cycle in the graph
:::

Because every cycle will point back to itself, after taking some matrix multiplication, there must ba a loop

### Solve
```python=
import numpy as np
import matplotlib.pyplot as plt
import sys
import random
import networkx as nx

def generate_graph(N):
        ret = np.zeros((N, N))
        for i in range(N):
                a = random.choice(list(range(0, i-1)) + list(range(i+1, N)))
                ret[i][a] = 1
        return ret

def plot_graph(data, path):
        N = len(data)
        G = nx.DiGraph()
        for i in range(N):
                G.add_node(chr(48+i))
        for i in range(N):
                for j in range(N):
                        if(data[i][j] == 1):
                                G.add_edge(chr(48+i), chr(48+j))
        nx.draw_networkx(G, nx.spring_layout(G), arrows = True, cmap = plt.get_cmap('jet'), node_size = 1200)
        plt.savefig(path)

def check_diag(G):
        N = len(G)
        j = 0
        for i in range(N):
                if(G[i][j] != 0):
                        return True
                j += 1
        return False

def has_cycle(G):
        N = len(G)
        ordi = G.copy()
        R = G.copy()
        while(N > 0):
                if(check_diag(R)):
                        return True
                R = R.dot(ordi)
                N -= 1
        return False

if __name__ == '__main__':
        N = int(sys.argv[1])
        G = generate_graph(N)
        #G = np.array([[0, 1, 0, 0, 0, 0], [0, 0, 0, 0, 0, 0], [0, 0, 0, 1, 0, 0], [0, 0, 0, 0, 0, 1], [0, 1, 0, 0, 0, 0], [0, 0, 1, 0, 0, 0]]) # Test Graph
        plot_graph(G, './graph.png')
        print(has_cycle(G))
```

![](https://i.imgur.com/wWh5gBo.png)

	True

###### tags: `線性代數筆記`