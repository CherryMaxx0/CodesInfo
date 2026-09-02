This is an [[py_External_Library|External Library]] so we need to [[pip]] to install library into our [[py_.venv|virtual environment]] or global as your own need.
So using powershell or command prompt, bashing this command:
```powershell
pip install numpy
```
will install numpy into your selected python environment if the environment is ==activated==
>[!Note]
>To check or to activate [[py_.venv|Virtual Environment]], go into this linked note.

After install, bashing this command here:
```powershell
pip show numpy
```

^5caadd

**OR
these two below, if first one shows error.** 

```powershell
python -m pip show numpy
```
**OR**
```powershell
python -c "import numpy; print(numpy.__file__)"
```

>[!Danger]
>Click [[pip#Reinstalling Pip.exe|Reinstall pip.exe]] to know how to fix the [[NumPy#^5caadd|issue]]. Without it being fixed, may cause future problems
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
>(==**[**== [row1],[row2] ==**]**==) need to use brackets after and before paranthesis highlighted. Because, it differs if there states being [[py_list|list]] or [[py_tuple|tuple]]. But doing it doesn't make any affect on numpy array being immutable(unchangeable). [[NumPy#Additional details about tuple and list|More details]]
#### Additional details about tuple and list
```python
numbers = np.array((
	[10,20,30,40,50],
	[60,70,80,90,100]
))
# CAN YOU CHANGE A VALUE? YES!
numbers[0, 0] = 999 print(numbers) 
# Output will change 10 to 999: [[999, 20, 30, 40, 50], [60, ...]]
```
**OR**
```python
numbers = np.array((
	(10,20,30,40,50),
	(60,70,80,90,100)
))
# CAN YOU CHANGE A VALUE? YES! 
numbers[0, 0] = 999 print(numbers) 
# Output will STILL change 10 to 999!
```
This array is like a ==blueprint== to `np.array` which is use to read the values only to make a new array structure not caring what type the blueprint is and throws the blueprint away after that.
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
>In Zeros and Ones function's the default state is float type, that's why ==dot== is printed with "0" or "1".
>And when using full, it is printing ==exactly== "7" or given value instead of seven that's why there is no dot, if "7." is set then it will print [7. 7. 7. 7. 7.]
### Arange and Linspace

#### Arange - *Specifying the Number of steps*
```python
print(np.arange(1,10,2))
```
*Output:*
```json
[1 3 5 7 9]
```

>[!warning]
>There is no function called as Arrange in numpy, it is ==**Arange**==

```python
np.arange[start,stop,step=] # start and step is optional
```
#### Linspace - *Specifying the Number of values*
```python
print(np.linspace(0,10,5))
```
*Output:*
```json
[ 0. 2.5 5. 7.5 10. ]
```
- ==When endpoint is by default equals to true==
```python
np.linspace[start,stop,num=,endpoint=true]
```
$step=\frac{stop-start}{num-1}$
- ==When endpoint=false==
```python
np.linspace[start,stop,num=,endpoint=false]
```
$step=\frac{stop-start}{num}$

And then the value of x is calculated as:
$x_i=start+i\times step$
>[!important]
>The spacing between the numbers like "0.   2.5" in printed array, is just auto alignment done by default.

___
## Array Structure
4 different [[py_Built-in_Functions|built -in functions]] is used, as shown below:
*Consider the array given below:*
```python
data = np.array([
	[10,20,30,40,50],
	[60,70,80,90,100]
])
```
### ndim - *number of dimension*
```python
print(data.ndim)
```
*Output:*
```json
2
```
This means the array given is 2-dimensional array.
### shape - *length of dimensions*
```python
print(data.shape)
```
*Output:*
```json
(2, 5) (row,column)
```
Shows the length of dimension in each direction (row/column).
### size - *number of elements*
```python
print(data.size)
```
*Output:*
```json
10
```
Gives the total number of element in whole array.
### dtype - *type of data*
```python
print(data.dtype)
```
*Output:*
```json
int64 (typeBits)
```
___
## Accessing and Changing Array
### 1D indexing and Slicing
```python
numbers = np.array([10,20,30,40,50]) 
```
#### Access
```python
print(numbers[0])
print(numbers[2])
print(numbers[-1])
print(numbers[-2])
```
*Output:*
```json
10
30
50
40
```
#### Slicing
```python
print(numbers[1:4])
print(numbers[::2])
print(numbers[:])
```
*Output:*
```json
[20 30 40]
[10 30 50]
[]
```
#### Changing
- Only 1 element
```python
numbers[1]=88
print(numbers)
```
*Output:*
```json
[10 88 30 40 50]
```
- Multiple elements together
```python
numbers[2:4]=100
print(numbers)
```
*Output:*
```json
[10 88 100 100 50]
```
### 2D indexing and Slicing
```python
data = np.array([
	[10,20,30,40,50],
	[60,70,80,90,100]
])
```
#### Access
```python
print(data[0,1])
print(data[1,-1])
```
*Output:*
```json
20
100
```
#### Slicing
```python
print(data[0,:])
print(data[:,1])
```
*Output:*
```json
[10 20 30 40 50]
[20 70]
```
#### Changing
 Only 1 element
```python
data[0,1]=88
print(data)
```
*Output:*
```json
[[10 88 30 40 50]
[60 70 80 90 100]]
```
- Multiple elements together
```python
data[0,2:4]=100
data[1,:]=0
print(data)
```
*Output:*
```json
[[10 88 100 100 50]
[0 0 0 0 0]]
```
___
## Vectorized Operations
As you know from the start [[NumPy#Difference using numpy with list|Difference between NumPy Usage]].
Similarly, any operator can be used in here.
### Standard Python
```python
numbers = [1,2,3,4,5]
result = []
for x in numbers:
	result.append(x+5)
print(result)
```
*Output:*
```json
[6 7 8 9 10]
```
### NumPy Version
```python
numbers = np.array([1,2,3,4,5])
result = numbers+5
print(result)
```
*Output:*
```json
[6 7 8 9 10]
```
___
## NumPy Mathematical Operations
There are mathematical operator [[py_Built-in_Functions|built-in functions]].
### Square Root
```python
numbers = np.array([1,4,9,16,25])
print(np.sqrt(numbers))
```
*Output:*
```json
[1. 2. 3. 4. 5.]
```
### Exponential
```python
numbers = np.array([0,1,2])
print(np.exp(numbers))
```
*Output:*
```json
[1.         2.71828183 7.3890561 ]
```
### Trigonometry
```python
angles = np.array([0, np.pi/2, np.pi])
print(np.sin(angles))
```
*Output:*
```json
[0.0000000e+00 1.0000000e+00 1.2246468e-16]
```