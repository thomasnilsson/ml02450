# ml02450

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
Example from book, section 11.2
```python
y = np.array([1,1,1,2,2,2,3,3])
x1 = [1,0,1,1,1,0,1,0]
x2 = [0,1,1,1,0,0,1,1]
x = [0,1]

naive_bayes(y, x, x1, x2)
```

Output: 
```python
array([0.33333333, 0.16666667, 0.5       ])
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