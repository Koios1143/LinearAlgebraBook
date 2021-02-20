# HW2 - Hill Cipher
## What is Hill Cipher?
Hill Cipher is a linear encryption using matrix multiplication

***Encryption***
1. We need to build a look-up table at first, and let $S$ equal to the number of element in table, for example:
	![](https://i.imgur.com/G5AfdJH.png)
2. Set a number $n$
3. Divide the plain text into groups of n, if there's any group's element is less than $n$, fill in the last character until full
4. Transform the divided plain text into an $n \times m$ matrix, m is the number of elements divide $n$
5. Cipher text = key $\times$ plain text mod $S$

![](https://i.imgur.com/HZXk6UL.png)


***Decryption***
Plain text = inverse of key $\times$ Cipher text mod $S$

![](https://i.imgur.com/1z0MQ1J.png)


## Part 1
> Given key and cipher text, calculate plain text

Assume $P$ is plain text, $C$ is cipher text, $k$ is key, and $S$ is the length of table

From the definition of Hill Cipher
$$kP = C\ mod\ S\\
P = k^{-1}C
$$

So, all we need to do is find inverse of key
In order to prevent inverse errors, and to coincide the modular operation

Here, we can't just use `numpy.linalg.inv(key)` to find the inverse of key

As we know
$$A^{-1} = \frac{1}{det(A)}adj\ A\ mod\ S\\
= invert(det(A)) \times (adj\ A\ mod\ S)
$$

### Solution Code
```python=
import gmpy2
import numpy as np

# Build look-up table
str = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ_.,?!'
tbl = {}
r_tbl = {}
for i in range(len(str)):
        tbl[str[i]] = i
        r_tbl[i] = str[i]

# Find inverse of key
key = np.array([[21, 11, 10], [27, 6, 16], [15, 9, 5]])
det = int(np.linalg.det(key))
adj = np.linalg.inv(key).dot(det)
inv = int(gmpy2.invert(det, 31)) # get (det)^{-1} mod 31
inv_key = np.round(np.mod(adj * inv, 31), 1).astype(int)

# Build cipher matrix
cipher_text = '_VGUPIMW!S_TBBS'
cipher_matrix = []
for i in cipher_text:
        cipher_matrix.append(tbl[i])
cipher_matrix = np.array(cipher_matrix).reshape(3, len(cipher_matrix)//3)

# Get plain text
plain_matrix = np.mod(inv_key.dot(cipher_matrix), 31)
plain_text = ''
for i in range(len(plain_matrix)):
        for j in range(len(plain_matrix[0])):
                plain_text += r_tbl[plain_matrix[i][j]]
print(plain_text)
```

## Part 2
> Given Cipher text and Plain text, calculate key, and decrypt another cipher text with this key

The concept is the same as above
$$kP = C\\
\Rightarrow k = CP^{-1}\\
\Rightarrow P = k^{-1}C
$$

### Solution Code
```python=
import gmpy2
import numpy as np

def matrix_inverse(A, mod):
        # inverse(matrix(np array), modular)
        det = int(np.linalg.det(A))
        adj = np.linalg.inv(A).dot(det)
        inv = int(gmpy2.invert(det, mod)) # get (det)^{-1} mod 31
        inv_A = np.round(np.mod(adj * inv, mod), 1).astype(int)
        return inv_A

# Build look-up table
str = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ_.,?!'
tbl = {}
r_tbl = {}
for i in range(len(str)):
        tbl[str[i]] = i
        r_tbl[i] = str[i]

# Stage 1: Find key
cipher_text = 'X.LEGIVPJ'
plain_text = 'I_HATE_TO'

## Get cipher matrix
cipher_matrix = []
for i in cipher_text:
        cipher_matrix.append(tbl[i])
cipher_matrix = np.array(cipher_matrix).reshape(3, len(cipher_matrix)//3)

## Get plain matrix
plain_matrix = []
for i in plain_text:
        plain_matrix.append(tbl[i])
plain_matrix = np.array(plain_matrix).reshape(3, len(plain_matrix)//3)

## Get inverse of plain matrix
inv = matrix_inverse(plain_matrix, 31)
print('inv: {}'.format(inv))

## Get key
key = cipher_matrix.dot(inv)
print('key: {}'.format(key))

# Stage 2: Find plain text
cipher_text = 'DBWCFIBWF'

## Get cipher matrix
cipher_matrix = []
for i in cipher_text:
        cipher_matrix.append(tbl[i])
cipher_matrix = np.array(cipher_matrix).reshape(3, len(cipher_matrix)//3)

## Get inverse of key
inv = matrix_inverse(key, 31)

## Get plain matrix
plain_matrix = np.mod(inv.dot(cipher_matrix), 31)

## Get plain text
plain_text = ''
for i in range(len(plain_matrix)):
        for j in range(len(plain_matrix[0])):
                plain_text += r_tbl[plain_matrix[i][j]]
print(plain_text)
```

## Reference
https://math.stackexchange.com/questions/2686150/inverse-of-a-modular-matrix

###### tags: `線性代數筆記`