

```python
import numpy as np
```


```python
x = np.arange(10)
x
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])



ndarray.reshape(shape, order='C')
___
Returns an array containing the same data with a new shape.


```python
X = np.arange(15).reshape(3, 5)
X
```




    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14]])



### 数组的基本属性

ndarray.ndim数组的维数


```python
x.ndim
```




    1




```python
X.ndim
```




    2



ndarray.shape 返回的是一个元组，表示每个维度的数组大小,元组的长度是维数
n行m列矩阵，返回的是(n, m)


```python
x.shape
```




    (10,)




```python
X.shape
```




    (3, 5)



ndarray.size 数组的总元素个数。


```python
x.size
```




    10




```python
X.size
```




    15



### numpy.array的数据访问


```python
x
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
x[0]
```




    0




```python
x[-1]
```




    9




```python
X
```




    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14]])



建议使用下面的形式访问多维数组的元素，不要使用X[0][0]
___
numpy数组类似Python序列类型支持切片


```python
X[2, 2]
```




    12




```python
x[0:5]
```




    array([0, 1, 2, 3, 4])




```python
x[:5]
```




    array([0, 1, 2, 3, 4])




```python
x[5:]
```




    array([5, 6, 7, 8, 9])




```python
x[::]
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
x[::2]
```




    array([0, 2, 4, 6, 8])




```python
x[::-1]
```




    array([9, 8, 7, 6, 5, 4, 3, 2, 1, 0])




```python
X[:2, :3]
```




    array([[0, 1, 2],
           [5, 6, 7]])



下面两个方块索引二元数组，取前两行前三列出错,要使用,运算符


```python
X[:2][:3]
```




    array([[0, 1, 2, 3, 4],
           [5, 6, 7, 8, 9]])



访问矩阵前两行，从头到尾间隔为2的元素


```python
X[:2, ::2]
```




    array([[0, 2, 4],
           [5, 7, 9]])



从行倒着数，列倒着数访问


```python
X[::-1, ::-1]
```




    array([[14, 13, 12, 11, 10],
           [ 9,  8,  7,  6,  5],
           [ 4,  3,  2,  1,  0]])




```python
X[::, ::-1]
```




    array([[ 4,  3,  2,  1,  0],
           [ 9,  8,  7,  6,  5],
           [14, 13, 12, 11, 10]])




```python
X[::, ::-1]
```




    array([[ 4,  3,  2,  1,  0],
           [ 9,  8,  7,  6,  5],
           [14, 13, 12, 11, 10]])



只取第一行


```python
X[0, :]
```




    array([0, 1, 2, 3, 4])




```python
X[0]
```




    array([0, 1, 2, 3, 4])



只取第一列


```python
X[:, 0]
```




    array([ 0,  5, 10])



在Python中使用切片是重新创建了一个全新矩阵；
___
但是在numpy中，切片后改变切片矩阵，原矩阵也要改变
因为numpy注重效率，使用浅拷贝


```python
subX = X[:2, :3]
subX
```




    array([[0, 1, 2],
           [5, 6, 7]])




```python
subX[0, 0] = 100
subX
```




    array([[100,   1,   2],
           [  5,   6,   7]])




```python
X
```




    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14]])




```python
Y = X
```


```python
X[0, 0] = 0
```


```python
subX
```




    array([[0, 1, 2],
           [5, 6, 7]])



深拷贝,copy(),可以看到SubX变化，X没发生变化


```python
subX = X[:2, :3].copy()
```


```python
subX[0, 0] = 100
subX
```




    array([[100,   1,   2],
           [  5,   6,   7]])




```python
X
```




    array([[ 0,  1,  2,  3,  4],
           [ 5,  6,  7,  8,  9],
           [10, 11, 12, 13, 14]])



reshape


```python
x.shape
```




    (10,)




```python
x.ndim
```




    1




```python
x.reshape(2,5)
```




    array([[0, 1, 2, 3, 4],
           [5, 6, 7, 8, 9]])




```python
x
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
A = x.reshape(2,5)
A
```




    array([[0, 1, 2, 3, 4],
           [5, 6, 7, 8, 9]])




```python
x
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
B = x.reshape(1, 10)
B
```




    array([[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]])



B是二维数组只有一行，每行都有10列，x为有10个元素一维的向量


```python
B.ndim
```




    2




```python
B.shape
```




    (1, 10)




```python
x.shape
```




    (10,)



x.reshape(10, -1)得到一个10行的元素的二维矩阵,


```python
x.reshape(10, -1)
```




    array([[0],
           [1],
           [2],
           [3],
           [4],
           [5],
           [6],
           [7],
           [8],
           [9]])




```python
x.reshape(-1, 10)
```




    array([[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]])


