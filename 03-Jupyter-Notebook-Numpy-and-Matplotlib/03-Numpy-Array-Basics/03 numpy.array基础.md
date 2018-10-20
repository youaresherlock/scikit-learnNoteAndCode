

```python
import numpy
```


```python
numpy.__version__
```




    '1.14.3'




```python
import numpy as np
```


```python
np.__version__
```




    '1.14.3'



## Python List的缺点


```python
L = [i for i  in range(10)]
L
```




    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]




```python
L[5] = "Hello"
L
```




    [0, 1, 2, 3, 4, 'Hello', 6, 7, 8, 9]



array容纳的元素类型要一样，效率比List高，
没有为数据配备与向量和矩阵相关的运算，所以不方便


```python
import array
arr = array.array('i', [i for i in range(10)])
arr
```




    array('i', [0, 1, 2, 3, 4, 5, 6, 7, 8, 9])



numpy.array 有隐形的类型转换


```python
nparr = numpy.array([i for i in range(10)])
nparr
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
print(nparr[5])
nparr[5] = 100
nparr
```

    5
    




    array([  0,   1,   2,   3,   4, 100,   6,   7,   8,   9])




```python
nparr.dtype
```




    dtype('int32')




```python
nparr[5] = 5.0
nparr.dtype
```




    dtype('int32')




```python
nparr[5] = 3.144
nparr[5]
```




    3




```python
nparr2 = np.array([1, 2, 3.0])
```


```python
nparr2
```




    array([1., 2., 3.])




```python
nparr2.dtype
```




    dtype('float64')



## 其他创建numpy.array的方法
下面创建矩阵的时候如果不指定dtype参数，那么就是浮点型
这是机器学习处理数据所使用的最普遍的类型


```python
numpy.zeros(10)
```




    array([0., 0., 0., 0., 0., 0., 0., 0., 0., 0.])




```python
numpy.zeros(10).dtype
```




    dtype('float64')




```python
import numpy as np
```


```python
np.zeros(10, dtype=int)
```




    array([0, 0, 0, 0, 0, 0, 0, 0, 0, 0])




```python
np.zeros(shape = (3, 5), dtype = int)
```




    array([[0, 0, 0, 0, 0],
           [0, 0, 0, 0, 0],
           [0, 0, 0, 0, 0]])




```python
np.ones(10)
```




    array([1., 1., 1., 1., 1., 1., 1., 1., 1., 1.])



fill_value的类型来判断生成的类型，如果是浮点型，则dtype就是浮点型


```python
np.full(shape = (3, 5), fill_value = 666)
```




    array([[666, 666, 666, 666, 666],
           [666, 666, 666, 666, 666],
           [666, 666, 666, 666, 666]])




```python
np.full(shape = (3, 5), fill_value = 666.0 )
```




    array([[666., 666., 666., 666., 666.],
           [666., 666., 666., 666., 666.],
           [666., 666., 666., 666., 666.]])



numpy.arange()
python中range()步长不可以为浮点数，但是arange()可以


```python
[i for i in range(0, 20, 2)]
```




    [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]




```python
np.arange(0, 20, 2)
```




    array([ 0,  2,  4,  6,  8, 10, 12, 14, 16, 18])




```python
np.arange(0, 1, 0.2)
```




    array([0. , 0.2, 0.4, 0.6, 0.8])




```python
np.arange(0, 10)
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])




```python
np.arange(10)
```




    array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])



## linspace
When arange is used with floating point arguments, it is generally not possible to predict the number of elements obtained, due to the finite floating point precision. For this reason, it is usually better to use the function linspace that receives as an argument the number of elements that we want, instead of the step:
当arange当用浮点数做步长的时候，由于有限的浮点数精度，通常不能预测
得到的数字数量，因此用linspace替代，可以生成特定个数的数字


```python
np.linspace(0, 20, 10)
```




    array([ 0.        ,  2.22222222,  4.44444444,  6.66666667,  8.88888889,
           11.11111111, 13.33333333, 15.55555556, 17.77777778, 20.        ])




```python
np.linspace(0, 20, 11)
```




    array([ 0.,  2.,  4.,  6.,  8., 10., 12., 14., 16., 18., 20.])



## random
numpy.random.randint(low, high=None, size=None, dtype='l')
Return random integers from low (inclusive) to high (exclusive).
___
numpy.random.random(size=None)是符合均匀分布的随机浮点数
Return random floats in the half-open interval [0.0, 1.0).
___
numpy.random.normal(loc=0.0, scale=1.0, size=None)是符合标准正态分布的随机数
Drawn samples from the parameterized normal distribution.
loc是均值，scale是方差,size是Outpu Shape


```python
np.random.randint(0, 10)
```




    8




```python
np.random.randint(2, 3)
```




    2




```python
np.random.randint(0, 10, size = 10)
```




    array([2, 2, 5, 6, 0, 3, 9, 3, 9, 9])




```python
np.random.randint(0, 10, size = (3, 5))
```




    array([[4, 1, 2, 9, 6],
           [2, 7, 5, 8, 5],
           [5, 9, 7, 5, 7]])



numpy.random.seed可以设置随机种子，与上次产生的随机数一样
This method is called when RandomState is initialized. It can be called again to re-seed the generator.


```python
np.random.seed(666)
```


```python
np.random.randint(4, 8, size = (3, 5))
```




    array([[4, 6, 5, 6, 6],
           [6, 5, 6, 4, 5],
           [7, 6, 7, 4, 7]])




```python
np.random.seed(666)
np.random.randint(4, 8, size = (3, 5))
```




    array([[4, 6, 5, 6, 6],
           [6, 5, 6, 4, 5],
           [7, 6, 7, 4, 7]])




```python
np.random.random(10)
```




    array([0.28116849, 0.46284169, 0.23340091, 0.76706421, 0.81995656,
           0.39747625, 0.31644109, 0.15551206, 0.73460987, 0.73159555])




```python
np.random.random((3, 5))
```




    array([[0.8578588 , 0.76741234, 0.95323137, 0.29097383, 0.84778197],
           [0.3497619 , 0.92389692, 0.29489453, 0.52438061, 0.94253896],
           [0.07473949, 0.27646251, 0.4675855 , 0.31581532, 0.39016259]])




```python
np.random.normal()
```




    0.9047266176428719



生成均值为10，方差为100的10个元素一维的数组


```python
np.random.normal(10, 100 ,10)
```




    array([ -72.6283265 ,   92.1013692 ,   46.7125916 ,  175.39958581,
             23.94647258, -111.71535503,  -89.49473667, -146.44858645,
           -152.87900441,  133.17486561])




```python
np.random.normal(1, 100, (2, 4))
```




    array([[-155.00397611,  -29.40116113, -118.84359191,  -86.18349948],
           [  18.65971815,  -19.26336417,   97.70290756, -192.16961713]])


