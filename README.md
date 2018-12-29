# ml02450
This is a library which extends the toolbox provided in the 02450-course at The Technical University of Denmark and contains a series of functions that will speed up a lot of exercises found in exam sets, that normally are calculated by hand. 

Tip: *The functions can also be used as a result-checking mechanism if you still prefer to do the questions by hand.*
## Install
Install this package with pip:
```bash
pip install ml02450
```

## Usage
Import library in python with:
```python
import ml02450 as ml
import numpy as np
```

Most library functions require numpy vectors as inputs, so numpy needs to be imported as well.

## Examples from exam sets
### AdaBoost
Given a classification problem with 25 observations in total, with 5 of them being misclassified in round 1, the weights can be calculated as:

```python
miss = np.zeros(25)
miss[:5] = 1
ml.adaboost(miss, rounds=1)
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

### Naive Bayes
Example from exam, fall 2018. 

Given the following transaction matrix, where the rows correspond to a feature ![](https://tex.s2cms.ru/svg/%24f_i%24), and the classes being given by the vector ![](https://tex.s2cms.ru/svg/%24y%24), 
what is ![](https://tex.s2cms.ru/svg/%24P%28y%3D1%20%5Cmid%20f_1%3D1%2C%20f_2%3D1.%20f_6%3D0%29%24)?
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

ml.naive_bayes(y, x, f1, f2, f6)
```

The probabilities ![](https://tex.s2cms.ru/svg/%24P%28y%3Dc%20%5Cmid%20f_1%3D1%2C%20f_2%3D1.%20f_6%3D0%29%24) for ![](https://tex.s2cms.ru/svg/%24c%3D1%2C2%2C3%24) is given by the following vector:
```python
array([0.45454545, 0.54545455, 0.        ])
```
The answer is therefore ![](https://tex.s2cms.ru/svg/%24y%3D0.45%24).

### Support
Given the transaction matrix, the support of the item-set ![](https://tex.s2cms.ru/svg/%24%5C%7Bf_1%2C%20f_3%2C%20f_8%2C%20f_9%2C%20f_2%2C%20f_6%2C%20f_7%5C%7D%24)  can be calculated using the `supp(I)` function: 
```python
ml.supp([f1,f3,f8,f9,f2,f6,f7])
```
Output:
```python
0.1
```

### Confidence
Given the transaction matrix, what is the confidence of the rule ![](https://tex.s2cms.ru/svg/%24%5C%7Bf_1%2C%20f_3%2C%20f_8%2C%20f_9%5C%7D%20%5Crightarrow%20%5C%7Bf_2%2Cf_6%2Cf_7%5C%7D%24)  
```python
a = [f1,f3,f8,f9]
b = [f2,f6,f7]
ml.conf(a,b)
```
Output:
```python
1.0
```

### Confusion Matrix
Given a 2x2 confusion matrix with:
 * TP: 18
 * FN: 12
 * TN: 15
 * FP: 9

Calculating the accuracy, error rate, recall, and much more, is done as follows:
```python
M = [[18,12],[9,15]]
ml.confusion_matrix(M)
```

Alternatively, by providing the attributes directly:

```python
ml.confusion_matrix(tp=18, fn=12, tn=15, fp=9)
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
Using K=2 nearest neighbours given the following distances, the avergae relative density becomes:
```python
o1 = np.array([68.1, 165.4])
o3 = np.array([68.1, 111.1])
o4 = np.array([44.74, 32.5])

ml.density(o1) / np.mean([ml.density(o3), ml.density(o4)])
```

Output:
```python
0.46231460448232553
```