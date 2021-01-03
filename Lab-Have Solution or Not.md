# Lab - Have solution or not

```python
import numpy as np
```

- Target
    ```
    given a n-D vector A and a n-D vector set S, we wanna know whether A is in the Span(S)
    ```


```python
'''
if there's any non-parrel vector pair in S, then any n-D matrix are included
otherwise, if A is parrel to S, then true, otherwise false
'''
def in_Span(A, S):
    # check legal
    for i in range(1, len(S)):
        if(len(S[i]) != len(S[0])):
            raise Exception('The given vector set are not all n-d like vector.\nfound error in No.{}.\n'.format(i))
    if(len(A) != len(S[0])):
        raise Exception('Then given vector and vector set are not in the same dimension.\nVector: {}, Vector Set: {}'.format(len(A), len(S[0])))
    
    fir = S[0]
    for i in range(1, len(S)):
        sec = S[i]
        tmp = fir.copy()
        mul = tmp[0]
        tmp *= sec[0]
        sec *= mul
        if(not np.array_equal(tmp, sec)):
            # non-parrel
            return True
    tmp = fir.copy()
    mul = tmp[0]
    tmp *= A[0]
    A *= mul
    if(np.array_equal(tmp, A)):
        # parrel
        return True
    return False
```


```python
N = np.array([1,2,3])
M = np.array([[2,5,8], [4,10,16]])
print(in_Span(N, M))
```

    False
    

- Target
    ```
    Given a system of linear equations, we wanna know whether it has solution or not
    ```


```python
'''
We can regard the system of linear equation as Ax=b, which A is a matrix, x is a vector, and b is a vector
if b is in the Span(A), the the equation has solution
'''
def has_solution(A, b):
    return in_Span(b, A)
```

$2x_1 + 6x_2 = -4\\1x_1 + 3x_2 = -2$


```python
A = np.array([[2,6],[1,3]])
b = np.array([-4,-2])
print(has_solution(A, b))
```

    False
    

###### tags: `線性代數筆記`