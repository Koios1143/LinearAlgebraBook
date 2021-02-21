# HW6 - Singular Value Decomposition

In this homework, we're going to use SVD to compress graph

Although we don't know how to impelment SVD, but we can use `numpy.linalg.svd` instead

There's 3 $m \times n$ matrices $R, G, B$ in our origin graph, which means 3 channels

Now, let's use $R$ for example
After SVD, we can get a $m \times m$ matrix $U$, $m \times n$ matrix $\Sigma$, and a $n \times n$ matrix $V^T$

:::info
$\Sigma$ given by `numpy.linalg.svd` will be a 1d array, which means components on diagonal
:::

Now, given a scalar $k$, we're going to use $k$ to do compression
$$U_{m \times m} \Rightarrow U_{m \times k}\\
\Sigma_{m \times n} \Rightarrow \Sigma_{k \times k}\\
V^T_{n \times n} \Rightarrow V^T_{k \times n}
$$

Then, we can get new $R' = U_{m \times k}\Sigma_{k \times k} V^T_{k \times n}$

Repeat this operation on $G$ and $B$, too
Then concate these three matrix, and draw the new pictures!

To calculate ***approximation error***, we can use this formula:

Assume the origin graph is $A$, and new graph is $AK$
$$error = ||A-AK||
$$

## Code
```python=
from PIL import Image
import numpy as np
import matplotlib.pyplot as plt

def ReadImage(filename):
	img = Image.open(filename)
	img.load()
	data = np.asarray(img, dtype="int32")
	width = data.shape[1]
	height = data.shape[0]

	R, G, B = [], [], []

	for x in range(height):
		for y in range(width):
			r, g, b = data[x][y]
			R.append(r)
			G.append(g)
			B.append(b)
	R = np.asarray(R, dtype='int32').reshape((height, width))
	G = np.asarray(G, dtype='int32').reshape((height, width))
	B = np.asarray(B, dtype='int32').reshape((height, width))
	return data, R, G, B, width, height

def compress(U, sigma, VT, k):
	m, n = U.shape[0], VT.shape[0]
	assert k<=n and k<=m
	return np.dot(np.dot(U[:, :k], np.diag(sigma[:k])), VT[:k, :])

if __name__ == '__main__':
	K = [1, 5, 50, 150, 400, 1050, 1289]
	A, R, G, B, width, height = ReadImage('LinusTorvalds.jpg')

	# SVD
	# sigma will only return diagonal values
	RU, Rsigma, RVT = np.linalg.svd(R)
	GU, Gsigma, GVT = np.linalg.svd(G)
	BU, Bsigma, BVT = np.linalg.svd(B)

	# Compress image
	AK = []
	for k in K:
		filename = 'k={}.png'.format(k)
		Rc = compress(RU, Rsigma, RVT, k).astype(int)
		Gc = compress(GU, Gsigma, GVT, k).astype(int)
		Bc = compress(BU, Bsigma, BVT, k).astype(int)

		img_out = Image.new('RGB', (width, height))
		Graph = []
		for x in range(height):
			Row = []
			for y in range(width):
					img_out.putpixel((y, x), (Rc[x][y], Gc[x][y], Bc[x][y]))
					Row.append([Rc[x][y], Gc[x][y], Bc[x][y]])
			Graph.append(Row)
		AK.append(Graph)
		img_out.save(filename)
	AK = np.asarray(AK)

	# Calculate error
	error = []
	for i in range(AK.shape[0]):
		error.append(np.linalg.norm(A-AK[i]))

	# Plot error
	plt.figure(figsize = (12, 8))
	plt.plot(K, error, 'o-', color = 'b')
	plt.xlabel('K')
	plt.ylabel('approximation error')
	plt.savefig('approximation_error.png')
```

- Origin Graph
	![](https://i.imgur.com/j8P74VC.jpg)


| **k = 1**     | **k = 5**     | **k = 50**    | **k = 150**|
|---|---|---|---|
|![](https://i.imgur.com/ZfTTDKn.jpg)| ![](https://i.imgur.com/ZX8C4x8.jpg)|![](https://i.imgur.com/fKz3pY6.jpg)|![](https://i.imgur.com/dmFvuC5.jpg)|
| **k = 400** | **k = 1050**| **k = 1289** ||
|![](https://i.imgur.com/S6U9wmI.jpg)|![](https://i.imgur.com/LUgdwM2.jpg)|![](https://i.imgur.com/It3dmNu.jpg)||

- Approximation Error
	![](https://i.imgur.com/ljhWCA0.png)

We can find that, when $k = 150$, our new graph is very close to origin graph!



###### tags: `線性代數筆記`