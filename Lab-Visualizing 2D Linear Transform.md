# Lab - Visualizing 2D Linear Transform

Reference by https://dododas.github.io/linear-algebra-with-python/posts/16-12-29-2d-transformations.html


```python
import numpy as np
import matplotlib as mpl
import matplotlib.pyplot as plt
```


```python
def colorizer(x, y):
        '''
        Map x-y coordinates to a rgb color
        '''
        r = min(1, 1-y/3)
        g = min(1, 1+y/3)
        b = 1/4 + x/16
        return (r, g, b)
```


```python
xvals = np.linspace(-4, 4, 9)
yvals = np.linspace(-3, 3, 7)
xygrid = np.column_stack([[x, y] for x in xvals for y in yvals])
```


```python
a = np.column_stack([[2, 1], [-1, 1]])
print(a)
uvgrid = np.dot(a, xygrid)
```

    [[ 2 -1]
     [ 1  1]]



```python
# Map grid coordinates to color
colors = list(map(colorizer, xygrid[0], xygrid[1]))

# Plot grid points
plt.figure(figsize=(4, 4), facecolor='w')
plt.scatter(xygrid[0], xygrid[1], s=36, c=colors, edgecolor='none')

# Set axis limits
plt.grid(True)
plt.axis('equal')
plt.title('original grid in x-y space')
```


![](https://i.imgur.com/Jr2ms6g.png)



```python
def stepwise_transform(a, points, nsteps=30):
    '''
    Generate a series of intermediate transform for the matrix multiplication
      np.dot(a, points) # matrix multiplication
    starting with the identity matrix, where
      a: 2-by-2 matrix
      points: 2-by-n array of coordinates in x-y space 

    Returns a (nsteps + 1)-by-2-by-n array
    '''
    
    # Create empty array of the right size
    transgrid = np.zeros((nsteps+1,) + np.shape(points))
    
    # Compute intermediate transforms
    for j in range(nsteps+1):
        intermediate = np.eye(2) + j/nsteps*(a-np.eye(2))
        transgrid[j] = np.dot(intermediate, points)
    return transgrid

steps = 30
transform = stepwise_transform(a, xygrid, nsteps=steps)
```


```python
def make_plots(transarray, color, outdir='png-frames', figuresize=(4, 4), figuredpi=150):
    '''
    Generate a series of png images showing a linear transformation stepwise
    '''
    nsteps = transarray.shape[0]
    ndigits = len(str(nsteps)) # to determine filename padding
    maxval = np.abs(transarray.max()) # to set axis limits
    
    # Create directory if not exists
    import os
    if not os.path.exists(outdir):
        os.makedirs(outdir)
    
    # Create figure
    plt.ioff()
    fig = plt.figure(figsize=figuresize, facecolor='w')
    for j in range(nsteps):
        plt.cla()
        plt.scatter(transarray[j, 0], transarray[j, 1], s=36, c=color, edgecolor='none')
        plt.xlim(1.1*np.array([-maxval, maxval]))
        plt.ylim(1.1*np.array([-maxval, maxval]))
        plt.grid(True)
        plt.draw()
        
        outfile = os.path.join(outdir, 'frame-' + str(j+1).zfill(ndigits) + '.png')
        fig.savefig(outfile, dpi=figuredpi)
    plt.ion()

make_plots(transform, colors, outdir='tmp')
```


![](https://i.imgur.com/u58Kp9o.png)



```python
# Convert to gif
def make_gif(targetdir, outfilename='animation'):
    from subprocess import call
    call('cd {} && convert -delay 10 frame-*.png {}.gif'.format(targetdir, outfilename), shell=True)
```

## Rotation

$$\begin{bmatrix} cos(\theta) & -sin(\theta) \\ sin(\theta) & cos(\theta)\end{bmatrix}
$$

```python
# Rotation
theta = np.pi/3
a = np.column_stack([[np.cos(theta), np.sin(theta)], [-np.sin(theta), np.cos(theta)]])
    
# Generate intermediates
transform = stepwise_transform(a, xygrid, nsteps=steps)
make_plots(transform, colors, outdir='Rotation')
make_gif('Rotation')
```


![](https://i.imgur.com/EjWQ7Oh.png)
![](https://i.imgur.com/9T3mki2.gif)



## Shear Transform
$$\begin{bmatrix} 1 & \lambda \\ 0 & 1 \end{bmatrix}
$$


```python
# Shear matrix
Lambda = 2
a = np.column_stack([[1, 0], [Lambda, 1]])

# Generate intermediates
transform = stepwise_transform(a, xygrid, nsteps = steps)
make_plots(transform, colors, outdir='Shear')
make_gif('Shear')
```


![](https://i.imgur.com/tKMgP1U.png)
![](https://i.imgur.com/3tQKQNx.gif)


## Permutation

$$\begin{bmatrix} 0 & 1 \\ 1 & 0 \end{bmatrix}
$$

```python
a = np.column_stack([[0, 1], [1, 0]])

# Generate intermediates
transform = stepwise_transform(a, xygrid, nsteps=steps)
make_plots(transform, colors, outdir='Permutation')
make_gif('Permutation')
```


![](https://i.imgur.com/xKKgE0e.png)
![](https://i.imgur.com/5HKOzrx.gif)



## Projection
$$\begin{bmatrix} 1 & 0 \\ 0 & 0 \end{bmatrix}
$$


```python
a = np.column_stack([[1, 0], [0, 0]])

# Generate intermediates
transform = stepwise_transform(a, xygrid, nsteps=steps)
make_plots(transform, colors, outdir='Projection')
make_gif('Projection')
```


![](https://i.imgur.com/aJIOG8z.png)
![](https://i.imgur.com/QaIPWK3.gif)

###### tags: `線性代數筆記`