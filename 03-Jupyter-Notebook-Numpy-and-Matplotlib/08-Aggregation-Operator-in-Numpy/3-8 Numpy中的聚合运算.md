
### 聚合操作



```python
import numpy as np

L = np.random.random(100)
```


```python
L
```




    array([0.79505654, 0.74891559, 0.90702127, 0.4214046 , 0.86913323,
           0.04088298, 0.5603476 , 0.64950059, 0.75545807, 0.19238372,
           0.13008313, 0.74673825, 0.59881937, 0.92812125, 0.55732802,
           0.64309605, 0.40880652, 0.20640605, 0.6951667 , 0.31954118,
           0.30529693, 0.15295391, 0.83067368, 0.05917058, 0.85026434,
           0.98033448, 0.75862908, 0.18133197, 0.14066754, 0.69097642,
           0.50550382, 0.42421297, 0.59704264, 0.81542373, 0.68285103,
           0.43364248, 0.51472235, 0.45830548, 0.0565895 , 0.71470387,
           0.848281  , 0.27078848, 0.49828037, 0.66930117, 0.72812609,
           0.65884457, 0.60874042, 0.6977382 , 0.03127634, 0.43768317,
           0.42600962, 0.72745613, 0.18502911, 0.11265117, 0.57785032,
           0.11329037, 0.21573485, 0.84082048, 0.97266201, 0.07370974,
           0.99638445, 0.51108142, 0.8197789 , 0.15592172, 0.55927893,
           0.38445909, 0.23153947, 0.88378236, 0.76949568, 0.83343699,
           0.17046628, 0.30749092, 0.96440538, 0.65779508, 0.79583128,
           0.65563755, 0.04161683, 0.07789446, 0.89586739, 0.14639915,
           0.46805591, 0.45105646, 0.82422359, 0.31756108, 0.04077766,
           0.71292268, 0.85759007, 0.99174241, 0.546959  , 0.54604659,
           0.58165702, 0.64854518, 0.5116469 , 0.81139416, 0.53408729,
           0.78973897, 0.57572981, 0.96341383, 0.92587138, 0.41047554])



Py3中的内置函数(built-in function)sum()和numpy中array
sum函数区别就在于效率


```python
sum(L)
```




    54.38983999610139




```python
np.sum(L)
```




    54.389839996101394




```python
L.sum()
```




    54.389839996101394




```python
big_array = np.random.rand(1000000)
%timeit sum(big_array)
%timeit np.sum(big_array)
%timeit np.ndarray.sum(big_array)
%timeit big_array.sum()
```

    297 ms ± 4.68 ms per loop (mean ± std. dev. of 7 runs, 1 loop each)
    1.89 ms ± 87.3 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
    1.81 ms ± 115 µs per loop (mean ± std. dev. of 7 runs, 100 loops each)
    1.82 ms ± 88.3 µs per loop (mean ± std. dev. of 7 runs, 1000 loops each)
    

求矩阵中元素的最小值和最大值
a.min()/a.max()


```python
np.min(big_array)
```




    2.2126557035484495e-06




```python
np.max(big_array)
```




    0.9999998278716675




```python
big_array.min()
```




    2.2126557035484495e-06




```python
big_array.max()
```




    0.9999998278716675




```python
X = np.arange(16).reshape(4, -1)
X
```




    array([[ 0,  1,  2,  3],
           [ 4,  5,  6,  7],
           [ 8,  9, 10, 11],
           [12, 13, 14, 15]])




```python
np.sum(X)
```




    120




```python
np.sum(X, axis = 0)
```




    array([24, 28, 32, 36])




```python
np.sum(X, axis = 1)
```




    array([ 6, 22, 38, 54])



numpy.prod(a, axis=None, dtype=None, out=None, keepdims=<no value>, initial=<no value>)
___
Return the product of array elements over a given axis.


```python
np.prod(X)
```




    0




```python
np.prod(X + 1)
```




    2004189184



numpy.mean()求最小值
___
numpy.mean(a, axis=None, dtype=None, out=None, keepdims=<no value>)[source]


```python
np.mean(X)
```




    7.5



numpy.median求中位数
___
numpy.median(a, axis=None, out=None, overwrite_input=False, keepdims=False)[source]


```python
np.median(X)
```




    7.5



统计学中中位数更好的比平均值描述样本


```python
v = np.array([1, 1, 2, 2, 10])
np.mean(v)
```




    3.2




```python
np.median(v)
```




    2.0



numpy.percentile(a, q, axis=None, out=None, overwrite_input=False, interpolation='linear', keepdims=False)
___
数据不同百分位置的值


```python
np.percentile(big_array, q = 50)
```




    0.4994852125340809




```python
np.percentile(big_array, q = 100)
```




    0.9999998278716675




```python
np.max(big_array)
```




    0.9999998278716675




```python
for percent in [0, 25, 50, 75, 100]:
    print(np.percentile(big_array, percent))
```

    2.2126557035484495e-06
    0.2503173535658848
    0.4994852125340809
    0.7494202959093872
    0.9999998278716675
    

求矩阵的方差numpy.var
___
numpy.var(a, axis=None, dtype=None, out=None, ddof=0, keepdims=<no value>)
____
求标准差numpy.std
___
numpy.std(a, axis=None, dtype=None, out=None, ddof=0, keepdims=<no value>)


```python
np.var(big_array)
```




    0.08313968131666415




```python
np.std(big_array)
```




    0.2883395243747623




```python
np.power(np.var(big_array), 1/2)
```




    0.2883395243747623




```python
x = np.random.normal(0, 1, size = 1000000)
```


```python
np.mean(x)
```




    -0.001082797705794394




```python
np.std(x)
```




    0.9991996842979097


