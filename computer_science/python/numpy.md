# Numpy

https://docs.scipy.org/doc/numpy/index.html

주로 사용하는 데이터 타입이 pandas DataFrame이라 예시도 DataFrame과 함께! <br>
아래처럼 numpy를 import 했고 모종의(?) 데이터가 든 DataFrame이 있다고 가정하자.
```python3
import numpy as np
import pandas as pd

df = pd.DataFrame()
```

# 목차
- [Logical AND](#logical-and)
- [numpy array 0으로 initialize](#np-zeros)
- [Polyfit으로 점들을 이어보자](#polyfit)
- [RuntimeWarning: invalid value encountered in power](#power-warning)
- [조건문에서 True 여부 판단](#np-all)

* * *
### Polyfit <a id="polyfit"></a>
x, y 좌표들이 주어졌을 때 Mean Square Error를 최소화하는 ```degree=N```인 다항식을 찾아보자!
```python3
degree = 2

x_list, y_list = [a for a in range(1, 11)], [a for a in range(2, 21)]

p2 = np.poly1d(np.polyfit(x_list, y_list, degree))

xs = np.linspace(min(x_list), max(x_list), 1000)
ys = p2(xs)
```

1. ```np.polyfit()```:  MSE를 최소화하는, 입력으로 넣어준 degree에 해당하는 다항식을 찾아서 그 계수(coefficient)를 반환하는 함수다. 
2. ```np.poly1d()```: 계수를 입력으로 받는 다항식 클래스
    1) 다항식을 construct하고, 
    2) x값을 넣어서 evaluate하자! (위 예제에서는 xs)

- [numpy.polyfit](https://docs.scipy.org/doc/numpy/reference/generated/numpy.polyfit.html)
- [numpy.poly1d](https://docs.scipy.org/doc/numpy/reference/generated/numpy.poly1d.html)


* * *
### Logical AND <a id="logical-and"></a>
조건을 사용해서 DataFrame을 접근하고 싶은데, 조건이 2개 이상일 때가 있다. 그럴땐 logical_and를 사용하자! 

```python3
np.logical_and([True, False], [False, False])
# Output: 
# array([False, False])
```
```(최종 조건) = np.logical_and((조건1) , (조건2))``` 와 같이 사용하면 좋다! 
- https://docs.scipy.org/doc/numpy/reference/generated/numpy.logical_and.html

* * *
### RuntimeWarning: invalid value encountered in power <a id="power-warning"></a>
코드를 돌렸는데 다짜고짜 에러가 났다! 
> C:\ProgramData\Anaconda3\envs\{내 ENV이름}\lib\site-packages\ipykernel_launcher.py:1: **RuntimeWarning: invalid value encountered in power**
  """Entry point for launching an IPython kernel.
```python3
np.power(a, num)
```
을 수행하는데, a가 음수이고 num이 정수가 아닐 경우 발생하는 에러였다. 실제로 계산 결과에 무려 ```j```가 붙는 것을 확인할 수 있었다. 갑자기 분위기 복소수... 경우에 따라 다르겠지만, 다음과 같이 고칠 수 있다. 
```python3
np.sign(a) * np.power(np.abs(a), num) # 부호는 살리고 power 연산은 수행
```
- https://stackoverflow.com/questions/45384602/numpy-runtimewarning-invalid-value-encountered-in-power

* * *
### np.zeros(shape, dtype=float, order='C') <a id="np-zeros"></a>
df.values의 type은 ```<class 'numpy.ndarray'>``` 이다. 어떤 DataFrame과 동일한 shape의, 0으로 initialize된 numpy array가 필요할 때 사용한다.

```python3
np.zeros(df.values.shape)
# dtype = data type
# order = 'C' : C-style (row-major)
#         'F' : Fortran-style (column-major)
```
- https://docs.scipy.org/doc/numpy/reference/generated/numpy.zeros.html

* * *
### 조건문에서 True 여부 판단시 사용하는 ```np.all``` <a id="np-all"></a>
```python3
# 기본형
numpy.all(a, axis=None, out=None, keepdims=<no value>)

# 실제 사용 예시
np.all(df.values == np.zeros(df.values.shape))
# df.values == np.zeros(df.values.shape) 의 결과는 elementwise한 비교 결과 
# e.g. [True, False, ... , True] : 이 결과의 element가 모두 True면 return값이 True
```
- https://docs.scipy.org/doc/numpy/reference/generated/numpy.all.html

* * *
### 템플릿 <a id=""></a>
```python3
```
    
    
    
##### 모르는 것을 검색할 때 유용한 키워드
 ``` numpy array ... ```, ```elementwise```, ```matrix multiplication```

