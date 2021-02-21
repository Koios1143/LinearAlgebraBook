# HW3 - Cosine Transform

Given a $1000 \times 1$ matrix $x$, represented the value of signal in time domain

We need to filter $x$ into a more clear signal with cosine transform

## Fourier Transform
Fourier Transform is a transformation that can transfer a function between time domain and frequency domanin

![](https://i.imgur.com/jHgQYN3.gif)

### Basis
:::success
Any periodic signal can be represented as a sum of sinusoids
:::
For every signal, we can disassemble it into many basic signal, these basic signals are just like basis in Linear Algebra

Fourier is complexity, so here we gonna use Cosine Transform

### Cosine Transform
Given a discrete signal $x = [x_0, x_1, \dots, x_{N-1}]$
- Basis matrix
	$$B = \{b_0, b_1, \dots, b_{N-1}\} \quad b_{k, n} = \begin{cases} \frac{1}{\sqrt{N}} \texttt{ if k = 0} \\ \frac{\sqrt{2}}{\sqrt{N}}cos\frac{(n + 0.5)k\pi}{N} \texttt{ else} \end{cases}
	$$
	![](https://i.imgur.com/eluFzOO.png)

Now, let's see how we make ordinal signal more clear!
1. Cosine Transform
	
    Transform $x$ in time domain into $a$ in frequency domain
	![](https://i.imgur.com/HqPfuai.png)
2. Masking
	
    Now, we have frequency of ordinal sigal, we can choose which frequencies we want to save
	
    For example, we want to save $f_1$, we can set our mask like $[1, 0, 0, \dots]$, and let $a$ multiply by mask
	![](https://i.imgur.com/mvHAYml.png)
3. Inverse Cosine Transform
	
    Now, we want to transform $a'$ in frequency domain into time domain, get $x'$
	![](https://i.imgur.com/kxnThc5.png)

## HW
In this homework, our ordinal $x$ is composed by five basic frequencies, we have two tasks
1. Output $f_1$ and $f_3$ signal to two txt files
2. Output the picture of $a$ of input signal

### Solve
```python=
import sys
import numpy as np
import matplotlib
matplotlib.use('Agg')
import matplotlib.pyplot as plt

def plot_wave(x, path = './wave.png'):
        plt.gcf().clear()
        plt.plot(x)
        plt.xlabel('n')
        plt.ylabel('xn')
        plt.savefig(path)

def plot_ak(a, path = './freq.png'):
        plt.gcf().clear()

        # Only plot the mag of a
        a = np.abs(a)
        plt.plot(a)
        plt.xlabel('k')
        plt.ylabel('ak')
        plt.savefig(path)

def CosineTrans(x, B):
        return np.linalg.inv(B).dot(x)

def InvCosineTrans(B, a):
        return B.dot(a)

def gen_basis(N):
        B = np.zeros((N, N))
        for n in range(N):
                for k in range(N):
                        if(k == 0):
                                B[n, k] = np.sqrt(1/N)
                        else:
                                B[n, k] = ( (np.sqrt(2/N)) * np.cos( np.pi*k*(2*n+1)/(2*N)) )
        return B

if __name__ == '__main__':
        signal_path = sys.argv[1]
        data = np.array(open(signal_path, 'r').read().split('\n')[:-1], dtype=np.float32)
        x = []
        for i in data:
                x.append([i])
        x = np.array(x)
        plot_wave(x, 'ordinal_wave.png') # Task 2

        B = gen_basis(1000)
        a = CosineTrans(x, B)
        plot_ak(a, 'ordinal_freq.png')

        # Task 1
        mask = np.zeros((1000, 1))
        mask[1, 0] = 1
        f1 = InvCosineTrans(B, np.multiply(a, mask))
        plot_wave(f1, './f1.png')
        np.savetxt('f1.txt', f1, delimiter = ',')

        mask[1, 0] = 0
        mask[3, 0] = 1
        f3 = InvCosineTrans(B, np.multiply(a, mask))
        plot_wave(f3, './f3.png')
        np.savetxt('f3.txt', f3, delimiter = ',')

        # Transformed Signal
        mask[1, 0] = mask[2, 0] = mask[4, 0] = mask[5, 0] = 1
        a = np.multiply(a, mask)
        x = InvCosineTrans(B, a)
        plot_wave(x)
        plot_ak(a)
```

Here, we use first student's file for example
- ordinal wave
	![](https://i.imgur.com/OhEl382.png)
- ordinal frequency
	![](https://i.imgur.com/UOoBU0g.png)
- masked frequency (mask = $[1, 1, 0, \dots]$)
	![](https://i.imgur.com/NpbQJNB.png)
- masked signal
	![](https://i.imgur.com/RG3lJkc.png)
- $f_1$ signal
	![](https://i.imgur.com/1TDMUXr.png)
- $f_3$ signal
	![](https://i.imgur.com/5xRXwbf.png)

###### tags: `線性代數筆記`