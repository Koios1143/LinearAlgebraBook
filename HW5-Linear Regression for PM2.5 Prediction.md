# HW5 - Linear Regression for PM2.5 Prediction

In this Homework, we're going to predict PM2.5 using orthogonal projection

Here are 17 features


| Name     | Chinese          |
| -------- | ---------------- |
| AMB      | 溫度             |
| CH4      | 甲烷             |
| CO       | 一氧化碳         |
| NMHC     | 非甲烷碳氫化合物 |
| NO       | 一氧化氮         |
| NO2      | 二氧化氮         |
| NOx      | 氮氧化物         |
| O3       | 臭氧             |
| PM10     | 懸浮微粒         |
| PM2.5    | 細懸浮微粒       |
| RAINFALL | 降雨量(不確定)   |
| RH       | 相對濕度         |
| SO2      | 二氧化硫         |
| THC      | 總碳氫化合物     |
| WD_HR    | 小時風向         |
| WIND_DIR | 風向(不確定)     |
| WS_HR    | 小時風速值       |

---

Result $Y$ formula:
$$Y = w_0 + \sum{x_i \times w_i}
$$

We concate every featrues except `PM2.5` in every hours into a matrix $X$

Every row means every features except `PM2.5` in one hour, and a $1$ at the end
$X$ should looks like:

$$\begin{bmatrix} x_{1}^{1} & x_{2}^{1} & \dots & x_{16}^{1} & 1\\
x_{1}^{2} & x_{2}^{2} & \dots & x_{16}^{2} & 1\\
\vdots & \vdots & \ddots & \vdots & \vdots \\
x_{1}^{M} & x_{2}^{M} & \dots & x_{16}^{M} & 1\end{bmatrix} \quad (x_{i}^{j} \begin{cases} i: \texttt{i-th feature} \\ j: \texttt{j-th hour}\end{cases})
$$

Here, given $X$ and $Y_{predict}$, our target is to find a best matrix $W$, such that $XW$ is nearest to $Y_{predict}$ and $Y_{real}$

---

From lecture before, we had learned orthogonal projection

$$e \triangleq Y - XW
$$

Our target is equal to find $||e||_{min}$

$$e = Y - XW = Y - CW\\
CW = P_wY\\
W = (C^TC)^{-1}C^TY
$$

By this formula, we can train our data
```python=
def train(self, train_X, train_Y):
    W = np.matmul(np.matmul(np.linalg.inv(np.matmul(np.transpose(train_X), train_X)), np.transpose(train_X)), train_Y)
    self.W = W #save W for later prediction
```

Once we have $W$, we can predict our test data
$$Y_{predict} = XW
$$
```python=
def predict(self, test_X):
    predict_Y = np.matmul(test_X, self.W)
    return predict_Y
```

To calculate our model is good or bad, we can use ***MSE***, formula below
$$MSE(Y_{predict}, Y_{real}) = \frac{1}{N}\sum_{i=1}^{N}{(Y_{predict} - Y_{real})^2}
$$
```python=
def MSE(predict_Y, real_Y):
    N = len(predict_Y)
    loss = np.sum((predict_Y - real_Y)**2)/N
    return loss
```

With these background knowledges, we can plot our first picture

```python=
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

Read data
```python=
def read_TrainData(filename, N):
    #N: how many hours to be as inputs
    raw_data = pd.read_csv(filename).values
    # 12 months, 20 days per month, 18 features per day. shape: (4320 , 24)
    data = raw_data[:, 3:] #first 3 columns are not data
    data = data.astype('float')
    X, Y = [], []
    for i in range(0, data.shape[0], 18*20):
        # i: start of each month
        days = np.vsplit(data[i:i+18*20], 20) # shape: 20 * (18, 24)
        concat = np.concatenate(days, axis=1) # shape: (18 feat, 480(day*hr))
        # take every N hours as x and N+1 hour as y
        for j in range(0, concat.shape[1]-N):
            features = concat[:, j:j+N].flatten() #the data of previous N hours
            features = np.append(features, [1]) # add w0
            X.append(features)
            Y.append([concat[9, j+N]]) #9th feature is PM2.5
    X = np.array(X)
    Y = np.array(Y)
    return X, Y

#from 1/23 0am, 1am ..23pm... 2/23, 0am, .... ~ 12/31 23p.m, total 2424 hours
#will give you a matrix 2424 * (18*N features you need)
def read_TestData(filename, N):
	#only handle N <= 48(2 days)
    assert N <= 48
    raw_data = pd.read_csv(filename).values
    data = raw_data[:, 3:]
    data = data.astype('float')
    surplus = DAYS - 20 #remaining days in each month after 20th
    test_X = []
    test_Y = [] #ground truth
    for i in range(12): # 12 month
        # i: start of each month
        start = sum(surplus[:i])*18
        end = sum(surplus[:i+1])*18
        days = np.vsplit(data[start:end], surplus[i])
        concat = np.concatenate(days, axis=1) # shape: (18 feat, (day*hr))
        for j in range(48, concat.shape[1]): #every month starts from 23th
            features = concat[:, j-N:j].flatten()
            features = np.append(features, [1]) # add w0
            test_X.append(features)
            test_Y.append([concat[9, j]])
    test_X = np.array(test_X)
    test_Y = np.array(test_Y)
    return test_X, test_Y
```

```python=
class Linear_Regression(object):
    def __init__(self):
        pass
    def train(self, train_X, train_Y):
        W = np.matmul(np.matmul(np.linalg.inv(np.matmul(np.transpose(train_X), train_X)), np.transpose(train_X)), train_Y)
        self.W = W #save W for later prediction
    def predict(self, test_X):
        predict_Y = np.matmul(test_X, self.W)
        return predict_Y

def MSE(predict_Y, real_Y):
    N = len(predict_Y)
    loss = np.sum((predict_Y - real_Y)**2)/N
    return loss
```

Plot MSE
```python=
def plot_MSE(train_set_loss, test_set_loss, filename):
    assert len(train_set_loss) == len(test_set_loss)
    length = len(train_set_loss)
    plt.figure(figsize = (12, 8))
    plt.xticks(range(1, length + 1))
    plt.plot(range(1, length+1), train_set_loss, 'b', label = 'train loss')
    plt.plot(range(1, length+1), test_set_loss, 'r', label = 'test loss')
    plt.legend()
    plt.xlabel('N')
    plt.ylabel('MSE loss')
    plt.show()
    plt.savefig(filename + '.png')
```

```python=
if __name__ == '__main__' :
	for i in range(1, 49):
		N = i

		train_X, train_Y = read_TrainData('train.csv', N=N)
		model = Linear_Regression()
		model.train(train_X, train_Y)
		test_X, test_Y = read_TestData('test.csv', N=N)

		predict_Y = model.predict(test_X)
		test_loss = MSE(predict_Y, test_Y)
		predict_Y = model.predict(train_X)
		train_loss = MSE(predict_Y, train_Y)

		train_set_loss.append(train_loss)
		test_set_loss.append(test_loss)
	plot_MSE(train_set_loss, test_set_loss, 'Normal_loss')
```

![](https://i.imgur.com/mZqK03N.png)

---

Now, we're going to improve our model!

Here, we want to figure out which features are unnecessary

I use ***Pearson product-moment correlation coefficient*** to find the relevance between fetures and PM2.5, formula below:
$$R(x, y) = \frac{\sum_{i = 1}^{N}(x_i-\mu_x)(y_i-\mu_y)}{\sqrt{\sum_{i = 1}^{N}{(x_i-\mu_x)^2}} \sqrt{\sum_{i = 1}^{N}{(y_i-\mu_y)^2}}}
$$

```python=
# Pearson product-moment correlation coefficient
# X: feature	Y: PM2.5
def Pearson(X, Y):
    N = len(X)
    mu_X = np.sum(X)/N
    mu_Y = np.sum(Y)/N

    Deno = 0
    for i in range(N):
        Deno += (X[i]-mu_X)*(Y[i]-mu_Y)

    sigma_X = 0
    sigma_Y = 0
    for i in range(N):
        sigma_X += (X[i]-mu_X)**2
        sigma_Y += (Y[i]-mu_Y)**2
    sigma_X = np.sqrt(sigma_X)
    sigma_Y = np.sqrt(sigma_Y)

    return Deno/(sigma_X*sigma_Y)
```

And I also plot figures to visulize relation between feature and PM2.5

This function will return a list of Pearson numbers

```python=
def plot_relation(train_X, train_Y):
    features = ['AMB', 'CH4', 'CO', 'NMHC', 'NO', 'NO2', 'NOx', 'O3', 'PM10', 'RAINFALL', 'RH', 'SO2', 'THC', 'WD_HR', 'WIND_DIR', 'WIND_SPEED', 'WS_HR']
    Ret_Pearson = []
    N = len(features)
    length = len(train_X)
    X = np.hsplit(train_X, len(train_X[0]))
    Y = train_Y.flatten('F')
    for i in range(N):
        filename = 'Relation/{}-relation.png'.format(features[i])
        plt.figure(figsize = (12, 8))
        plt.xticks(range(1, length+1))
        plt.plot(range(1, length+1), X[i].flatten('F'), 'b', label = features[i])
        plt.plot(range(1, length+1), Y, 'r', label = 'PM2.5')
        plt.legend()
        plt.xlabel('N')
        plt.show()
        plt.savefig(filename)
        Pearson_number = Pearson(X[i], Y)
        Ret_Pearson.append(Pearson_number)
        print('{} Pearson number: {}'.format(features[i], Pearson_number))
    return Ret_Pearson
```

Here use $N = 1$ (hour = 1) for example
I use $0.3$ be our $R_{min}$
```python=
# plot relation
if(i == 1):
	Ret = plot_relation(train_X, train_Y)
	min_R = 0.3
	for i in range(len(Ret)):
		if(np.absolute(Ret[i]) < min_R):
			del_features.append(features[i])
	print(del_features)
```

And heres what I get

|                                      |                                      |                                      |
| ------------------------------------ | ------------------------------------ | ------------------------------------ |
|![](https://i.imgur.com/xyO1UkY.png)| ![](https://i.imgur.com/nx9x1mK.png)|![](https://i.imgur.com/MIHFrUp.png)|
|![](https://i.imgur.com/tQGTkjt.png)|![](https://i.imgur.com/ICgCZCF.png)|![](https://i.imgur.com/WgWUsro.png)|
|![](https://i.imgur.com/cbT0Dl2.png)|![](https://i.imgur.com/08ppScY.png)|![](https://i.imgur.com/vourbUV.png)|
|![](https://i.imgur.com/4kco7jz.png)|![](https://i.imgur.com/awc5uqJ.png)|![](https://i.imgur.com/W9ionBz.png)|
|![](https://i.imgur.com/hJGuIXk.png)|![](https://i.imgur.com/qnP04to.png)|![](https://i.imgur.com/GohYTjY.png)|
|![](https://i.imgur.com/9trQicr.png)|![](https://i.imgur.com/HRFIMbJ.png)|![](https://i.imgur.com/QdZ6J1v.png)|

```
AMB Pearson number: [-0.01653301]
CH4 Pearson number: [0.13210958]
CO Pearson number: [0.41424262]
NMHC Pearson number: [0.34844811]
NO Pearson number: [0.06344583]
NO2 Pearson number: [0.358251]
NOx Pearson number: [0.28166542]
O3 Pearson number: [0.26602844]
PM10 Pearson number: [0.72083873]
PM2.5 Pearson number: [0.86637141]
RAINFALL Pearson number: [-0.09616555]
RH Pearson number: [-0.27509624]
SO2 Pearson number: [0.27327388]
THC Pearson number: [0.23252488]
WD_HR Pearson number: [0.18613633]
WIND_DIR Pearson number: [0.16474147]
WIND_SPEED Pearson number: [-0.03608803]
WS_HR Pearson number: [-0.09389372]
```

Features that we don't need:
```
['AMB', 'CH4', 'NO', 'NOx', 'O3', 'RAINFALL', 'RH', 'SO2', 'THC', 'WD_HR', 'WIND_DIR', 'WIND_SPEED', 'WS_HR']
```

So, next we're going to filter these features, and plot a new MSE again

I wrote a function to filter features
```python=
def filter(data, del_features):
	features = ['AMB', 'CH4', 'CO', 'NMHC', 'NO', 'NO2', 'NOx', 'O3', 'PM10', 'RAINFALL', 'RH', 'SO2', 'THC', 'WD_HR', 'WIND_DIR', 'WIND_SPEED', 'WS_HR']
	del_pos = []
	for i in del_features:
		for j in range(len(features)):
			if(i == features[j]):
				del_pos.append(j)
	return np.delete(data, del_pos, 1)
```

And than plot figure
```python=
if __name__ == '__main__' :
	features = ['AMB', 'CH4', 'CO', 'NMHC', 'NO', 'NO2', 'NOx', 'O3', 'PM10', 'RAINFALL', 'RH', 'SO2', 'THC', 'WD_HR', 'WIND_DIR', 'WIND_SPEED', 'WS_HR']
	del_features = ['AMB', 'NO', 'RAINFALL', 'WIND_SPEED', 'WS_HR']
	train_set_loss_filtered = []
	test_set_loss_filtered = []

	for i in range(1, 49):
		N = i
		train_X, train_Y = read_TrainData('train.csv', N=N)
		model = Linear_Regression()
		test_X, test_Y = read_TestData('test.csv', N=N)
		train_X = filter(train_X, del_features)
		test_X = filter(test_X, del_features)
		model.train(train_X, train_Y)

		predict_Y = model.predict(test_X)
		test_loss = MSE(predict_Y, test_Y)
		predict_Y = model.predict(train_X)
		train_loss = MSE(predict_Y, train_Y)

		train_set_loss_filtered.append(train_loss)
		test_set_loss_filtered.append(test_loss)

	plot_MSE(train_set_loss_filtered, test_set_loss_filtered, 'Filtered_loss')
```

![](https://i.imgur.com/cMTeS8x.png)

---

Now, let's try another way, try to delete $w_0$

Normal MSE
![](https://i.imgur.com/3U3Cl0D.png)

Filtered MSE
![](https://i.imgur.com/7rFuHD4.png)

Well, there is not much difference, too

## Full Code
```python=
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

attrs = ['AMB', 'CH4', 'CO', 'NMHC', 'NO', 'NO2',
        'NOx', 'O3', 'PM10', 'PM2.5', 'RAINFALL', 'RH',
        'SO2', 'THC', 'WD_HR', 'WIND_DIR', 'WIND_SPEED', 'WS_HR']

'''
AMB		溫度
CH4		甲烷
CO		一氧化碳
NMHC		非甲烷碳氫化合物
NO		一氧化氮
NO2		二氧化氮
NOx		氮氧化物
O3		臭氧
PM10		懸浮微粒
PM2.5		細懸浮微粒
RAINFALL	降雨量(不確定)
RH		相對濕度
SO2		二氧化硫
THC		總碳氫化合物
WD_HR		小時風向
WIND_DIR	風向(不確定)
WS_HR		小時風速值
'''

DAYS = np.array([31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31])

def read_TrainData(filename, N):
    #N: how many hours to be as inputs
    raw_data = pd.read_csv(filename).values
    # 12 months, 20 days per month, 18 features per day. shape: (4320 , 24)
    data = raw_data[:, 3:] #first 3 columns are not data
    data = data.astype('float')
    X, Y = [], []
    for i in range(0, data.shape[0], 18*20):
        # i: start of each month
        days = np.vsplit(data[i:i+18*20], 20) # shape: 20 * (18, 24)
        concat = np.concatenate(days, axis=1) # shape: (18 feat, 480(day*hr))
        # take every N hours as x and N+1 hour as y
        for j in range(0, concat.shape[1]-N):
            features = concat[:, j:j+N].flatten() #the data of previous N hours
            features = np.append(features, [1]) # add w0
            X.append(features)
            Y.append([concat[9, j+N]]) #9th feature is PM2.5
    X = np.array(X)
    Y = np.array(Y)
    return X, Y

#from 1/23 0am, 1am ..23pm... 2/23, 0am, .... ~ 12/31 23p.m, total 2424 hours
#will give you a matrix 2424 * (18*N features you need)
def read_TestData(filename, N):
	#only handle N <= 48(2 days)
    assert N <= 48
    raw_data = pd.read_csv(filename).values
    data = raw_data[:, 3:]
    data = data.astype('float')
    surplus = DAYS - 20 #remaining days in each month after 20th
    test_X = []
    test_Y = [] #ground truth
    for i in range(12): # 12 month
        # i: start of each month
        start = sum(surplus[:i])*18
        end = sum(surplus[:i+1])*18
        days = np.vsplit(data[start:end], surplus[i])
        concat = np.concatenate(days, axis=1) # shape: (18 feat, (day*hr))
        for j in range(48, concat.shape[1]): #every month starts from 23th
            features = concat[:, j-N:j].flatten()
            features = np.append(features, [1]) # add w0
            test_X.append(features)
            test_Y.append([concat[9, j]])
    test_X = np.array(test_X)
    test_Y = np.array(test_Y)
    return test_X, test_Y

class Linear_Regression(object):
    def __init__(self):
        pass
    def train(self, train_X, train_Y):
        W = np.matmul(np.matmul(np.linalg.inv(np.matmul(np.transpose(train_X), train_X)), np.transpose(train_X)), train_Y)
        self.W = W #save W for later prediction
    def predict(self, test_X):
        predict_Y = np.matmul(test_X, self.W)
        return predict_Y

def MSE(predict_Y, real_Y):
    N = len(predict_Y)
    loss = np.sum((predict_Y - real_Y)**2)/N
    return loss

def filter(data, del_features):
    features = ['AMB', 'CH4', 'CO', 'NMHC', 'NO', 'NO2', 'NOx', 'O3', 'PM10', 'PM2.5', 'RAINFALL', 'RH', 'SO2', 'THC', 'WD_HR', 'WIND_DIR', 'WIND_SPEED', 'WS_HR']
    del_pos = []
    for i in del_features:
        for j in range(len(features)):
            if(i == features[j]):
                del_pos.append(j)
    return np.delete(data, del_pos, 1)

# Pearson product-moment correlation coefficient
# X: feature	Y: PM2.5
def Pearson(X, Y):
    N = len(X)
    mu_X = np.sum(X)/N
    mu_Y = np.sum(Y)/N

    Deno = 0
    for i in range(N):
        Deno += (X[i]-mu_X)*(Y[i]-mu_Y)

    sigma_X = 0
    sigma_Y = 0
    for i in range(N):
        sigma_X += (X[i]-mu_X)**2
        sigma_Y += (Y[i]-mu_Y)**2
    sigma_X = np.sqrt(sigma_X)
    sigma_Y = np.sqrt(sigma_Y)

    return Deno/(sigma_X*sigma_Y)

def plot_MSE(train_set_loss, test_set_loss, filename):
    assert len(train_set_loss) == len(test_set_loss)
    length = len(train_set_loss)
    plt.figure(figsize = (12, 8))
    plt.xticks(range(1, length + 1))
    plt.plot(range(1, length+1), train_set_loss, 'b', label = 'train loss')
    plt.plot(range(1, length+1), test_set_loss, 'r', label = 'test loss')
    plt.legend()
    plt.xlabel('N')
    plt.ylabel('MSE loss')
    plt.show()
    plt.savefig(filename)

def plot_relation(train_X, train_Y):
    features = ['AMB', 'CH4', 'CO', 'NMHC', 'NO', 'NO2', 'NOx', 'O3', 'PM10', 'PM2.5', 'RAINFALL', 'RH', 'SO2', 'THC', 'WD_HR', 'WIND_DIR', 'WIND_SPEED', 'WS_HR']
    Ret_Pearson = []
    N = len(features)
    length = len(train_X)
    X = np.hsplit(train_X, len(train_X[0]))
    Y = train_Y.flatten('F')
    for i in range(N):
        filename = 'Relation/{}-relation.png'.format(features[i])
        plt.figure(figsize = (12, 8))
        plt.xticks(range(1, length+1))
        plt.plot(range(1, length+1), X[i].flatten('F'), 'b', label = features[i])
        plt.plot(range(1, length+1), Y, 'r', label = 'PM2.5 Next hour')
        plt.legend()
        plt.xlabel('N')
        plt.show()
        plt.savefig(filename)
        Pearson_number = Pearson(X[i], Y)
        Ret_Pearson.append(Pearson_number)
        print('{} Pearson number: {}'.format(features[i], Pearson_number))
    return Ret_Pearson

if __name__ == '__main__' :
    features = ['AMB', 'CH4', 'CO', 'NMHC', 'NO', 'NO2', 'NOx', 'O3', 'PM10', 'PM2.5', 'RAINFALL', 'RH', 'SO2', 'THC', 'WD_HR', 'WIND_DIR', 'WIND_SPEED', 'WS_HR']
    del_features = []

    train_set_loss = []
    test_set_loss = []

    train_set_loss_filtered = []
    test_set_loss_filtered = []

    for i in range(1, 49):
        N = i

        # Normal
        train_X, train_Y = read_TrainData('train.csv', N=N)

        # plot relation
        if(i == 1):
            Ret = plot_relation(train_X, train_Y)
            min_R = 0.3
            for i in range(len(Ret)):
                if(np.absolute(Ret[i]) < min_R):
                    del_features.append(features[i])
            print(del_features)

        model = Linear_Regression()
        model.train(train_X, train_Y)
        test_X, test_Y = read_TestData('test.csv', N=N)

        predict_Y = model.predict(test_X)
        test_loss = MSE(predict_Y, test_Y)
        predict_Y = model.predict(train_X)
        train_loss = MSE(predict_Y, train_Y)

        train_set_loss.append(train_loss)
        test_set_loss.append(test_loss)

        # Filtered
        train_X = filter(train_X, del_features)
        test_X = filter(test_X, del_features)
        model = Linear_Regression()
        model.train(train_X, train_Y)
        
        predict_Y = model.predict(test_X)
        test_loss = MSE(predict_Y, test_Y)
        predict_Y = model.predict(train_X)
        train_loss = MSE(predict_Y, train_Y)

        train_set_loss_filtered.append(train_loss)
        test_set_loss_filtered.append(test_loss)

    plot_MSE(train_set_loss, test_set_loss, 'Normal_loss.png')
    plot_MSE(train_set_loss_filtered, test_set_loss_filtered, 'Filtered_loss.png')
```

###### tags: `線性代數筆記`