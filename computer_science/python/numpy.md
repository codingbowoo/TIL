# Numpy

https://docs.scipy.org/doc/numpy/index.html

자주 검색하는 함수 몇 가지 투척할 예정

주로 사용하는 데이터 타입이 pandas DataFrame이라 예시도 DataFrame과 함께! <br>
아래처럼 numpy를 import 했고 모종의(?) 데이터가 든 DataFrame이 있다고 가정하자.
```python3
import numpy as np
import pandas as pd

df = pd.DataFrame()
```

1. np.zeros(shape, dtype=float, order='C')
    ```python3
    np.zeros(df.values.shape)
    # dtype = data type
    # order = 'C' : C-style (row-major)
    #         'F' : Fortran-style (column-major)
    ```
    df.values의 type은 ```<class 'numpy.ndarray'>``` 이다. 어떤 DataFrame과 동일한 shape의, 0으로 initialize된 numpy array가 필요할 때 사용한다.
    https://docs.scipy.org/doc/numpy/reference/generated/numpy.zeros.html
    
    
2. 조건문에서 True 여부 판단시 사용하는 ```np.all```
    ```python3
    # 기본형
    numpy.all(a, axis=None, out=None, keepdims=<no value>)
    
    # 실제 사용 예시
    np.all(df.values == np.zeros(df.values.shape))
    # df.values == np.zeros(df.values.shape) 의 결과는 elementwise한 비교 결과 
    # e.g. [True, False, ... , True] : 이 결과의 element가 모두 True면 return값이 True
    ```
    https://docs.scipy.org/doc/numpy/reference/generated/numpy.all.html

3. 추가 예정
    ```python3
    ```
    
    
    
##### 모르는 것을 검색할 때 유용한 키워드
 ``` numpy array ... ```, ```elementwise```, ```matrix multiplication```

