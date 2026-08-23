## Difference using numpy with list
Why Numpy even though there is already [[py_list|list]] in python?
### List (Standard Python)
```python
numbers = [10,20,30,40,50]
result = []
for number in numbers:
	result.append(number*2)
print(result)
```
*Output:*
```json
[20,40,60,80,100]
```
### NumPy (Vectorized)
Always need to ==import numpy== when using it.
```python
import numpy as np

numbers = np.array([10,20,30,40,50])
result = numbers*2
print(result)
```
*Output:*
```json
[20,40,60,80,100]
```

>[!info]
>List often needs loops that is inefficient than numpy using the entire collection at once givcs better performance.

___
## Creating NumPy [[py_list#^29f46a|Array]]
### 1D array
```python
numbers = np.array([10,20,30,40,50]) 
```
### Matrix system (2D array)
```python
numbers = np.array([
	[10,20,30,40,50],
	[60,70,80,90,100]
]) 
```

>[!Caution]
>(==**[**== [row1],[row2] ==**]**==) need to use brackets after and before paranthesis highlighted.
### Zeros, Ones and Full
```python
print(np.zeros(5))
print(np.ones(5))
print(np.full(5,7))
```
*Output:*
```json
[0. 0. 0. 0. 0.]
[1. 1. 1. 1. 1.]
[7 7 7 7 7]
```

>[!important]
>In Zeros and Ones function the default state is float type, that's why ==dot== is printed with "0" or "1".
>And when using full, it is printing ==exactly== "7" or given value instead of seven that's why there is no dot, if "7." is set then it will print [7. 7. 7. 7. 7.]
### Arange and Linspace
- Arange - *Specifying the Number of steps*
- linspace - *Specifying the Number of values*
>[!warning]
>There is no function called as Arrange in numpy, it is Arange

```python
print(np.arange(1,10,2))
print(np.linspace(0,10,5))
```
*Output:*
```json
[1 3 5 7 9]
[ 0. 2.5 5. 7.5 10. ]
```

>[!important]
>The spacing between the numbers like "0.   2.5" in printed array, is just auto alignment done by default.
#### Linspace
```python
np.linspace[start,stop,num=,endpoint=true]
```
==endpoint is by default true==
$step=\frac{stop-start}{num-1}$

```python
```python
np.linspace[start,stop,num=,endpoint=false]
```
==when endpoint=false==
$step=\frac{stop-start}{num}$

And the value of x is:
$x_i=start+i\times step$
___
## Array Structure
4 different functions is used, as shown below:
- ndim - *number of dimension*
- shape - 
- size
- dtype
*Consider the array given below:*
```python
data = np.array([
	[10,20,30,40,50],
	[60,70,80,90,100]
])
```
### ndim (number of dimension)
```python
print(data.ndim)
```

```json
2
```
This means the array given is 2-dimensional array.
### shape
```python
print(data.shape)
```

```json
(2, 3)
```