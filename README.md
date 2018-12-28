# ml02450
This is a library which extends the toolbox provided in the 02450 course at The Technical University of Denmark, and contains a series of functions that will speed up a lot of exercises found in exam sets, that normally are calculated by hand. 

Tip: *The functions can also be used as a result-checking mechanism, if you still prefer to do the questions by hand.*
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
## Examples from exam sets
### AdaBoost
25 observations in total, 5 of them misclassified in round 1 - what are the weights?
```python
miss = np.zeros(25)
miss[:5] = 1
adaboost(miss, rounds=5)
```

The weights are as follows:
```python
w[0]: 0.100000
w[1]: 0.100000
w[2]: 0.100000
w[3]: 0.100000
w[4]: 0.100000
w[5]: 0.025000
w[6]: 0.025000
w[7]: 0.025000
w[8]: 0.025000
w[9]: 0.025000
w[10]: 0.025000
w[11]: 0.025000
w[12]: 0.025000
w[13]: 0.025000
w[14]: 0.025000
w[15]: 0.025000
w[16]: 0.025000
w[17]: 0.025000
w[18]: 0.025000
w[19]: 0.025000
w[20]: 0.025000
w[21]: 0.025000
w[22]: 0.025000
w[23]: 0.025000
w[24]: 0.025000
```

### Naive bayes
Example from exam, fall 2018. 

Given the following transaction matrix, where the rows correspond to a feature $f_i$, and the classes being given by the vector $y$, 
what is $P(y=1 | f_1=1, f_2=1. f_6=0)$?
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

The probabilities $P(y=c | f_1=1, f_2=1. f_6=0)$ for $c=1,2,3$ is given by the following vector:
```python
array([0.45454545, 0.54545455, 0.        ])
```
The answer is therefore $y=0.45$.

### Confidence and support
Given the transaction matrix, what is the confidence of the rule ${f_1, f_3, f_8, f_9} \rightarrow {f_2,f_6,f_7}$  
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