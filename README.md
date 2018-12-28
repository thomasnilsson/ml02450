# ml02450
## Install
Install this package with pip:
```bash
pip install ml02450
```

## Usage
Import library in python with:
```python
from ml02450 import *
```
## Examples
### AdaBoost
```python
miss = np.zeros(25)
miss[:5] = 1
adaboost(miss, rounds=5)
```

Output:
```python
w[0]: 0.199222
w[1]: 0.199222
w[2]: 0.199222
w[3]: 0.199222
w[4]: 0.199222
w[5]: 0.000195
w[6]: 0.000195
w[7]: 0.000195
w[8]: 0.000195
w[9]: 0.000195
w[10]: 0.000195
w[11]: 0.000195
w[12]: 0.000195
w[13]: 0.000195
w[14]: 0.000195
w[15]: 0.000195
w[16]: 0.000195
w[17]: 0.000195
w[18]: 0.000195
w[19]: 0.000195
w[20]: 0.000195
w[21]: 0.000195
w[22]: 0.000195
w[23]: 0.000195
w[24]: 0.000195
```

### Naive bayes
Example from exam, fall 2018
```python
X = np.array([
    [1,1,0,0,0,1,0,0,0,1],
    [1,0,0,0,0,0,0,0,0,0],
    [1,1,0,0,0,1,0,0,0,1],
    [0,1,1,1,0,0,0,1,1,0],
    [1,1,0,0,0,1,0,0,0,1],
    [0,1,1,1,0,0,1,1,1,0],
    [1,1,1,0,0,1,1,1,1,0],
    [0,1,1,1,0,1,1,0,0,1],
    [0,0,0,0,1,1,1,0,1,1],
    [1,0,0,0,0,1,1,1,1,0],
])

labels = ['f%i' %i for i in range(1,11)]
f1,f2,f3,f4,f5,f6,f7,f8,f9,f10 = X.T

y = [1,1,1,2,2,2,2,2,3,3]
x = [1,1,0]

naive_bayes(y, x, f1, f2, f6)
```

Output: 
```python
array([0.45454545, 0.54545455, 0.        ])
```

### Confidence and support
```python
a = [f1,f3,f8,f9]
b = [f2,f6,f7]
conf(a,b)
```
Output:
```python
1.0
```

### Confusion Matrix
```python
M = [[18,12],[9,15]]
confusion_matrix(M)
```

Output:
```python
TP: 18 FN: 12 TN: 15 FP: 9
Accuracy: 0.6111111111111112
Error rate: 0.38888888888888884
Recall: 0.6
Precision: 0.6666666666666666
FPR: 0.375
TPR: 0.6
```


### ARD
```python
o1 = np.array([68.1, 165.4])
o3 = np.array([68.1, 111.1])
o4 = np.array([44.74, 32.5])

density(o1) / np.mean([density(o3), density(o4)])
```

Output:
```python
0.46231460448232553
```