# DataFrame

pandas에서 가장 사랑하는 자료형 (여담인데 2020.03.04기준으로 pandas 1.0.1이고, documentation 페이지가 엄청 예뻐졌다..?)
DataFrame! 


자주 쓰는 함수 몇 가지 투척할 예정

아래처럼 pandas를 import 했고 모종의(?) 데이터가 든 DataFrame이 있다고 가정하자.
```python3
import pandas as pd
df = pd.DataFrame()
```

1. 인덱스 기준으로 앞에서부터(**head**), 뒤에서부터(**tail**) N개 데이터 보기
    ```python3
    df.head()    # 빈 칸으로 두면 5개 데이터를 보여준다.
    df.tail(10)  # 숫자 N을 넣으면 N개 데이터를 보여준다.
    ```

2. null이 있는지 확인하기, 각 column마다 null이 몇 개 인지 확인하기
   ```axis``` option 확인하면 각 row를 확인할 수도 있겠다. 
    ```python3
    df.isnull()        # DataFrame의 각 element가 값이 있으면 True, NaN이면 False인 DataFrame을 보여준다.
    df.isnull().sum()  # 이렇게 하면 True 다 더해지니까 NaN값 개수를 쉽게 볼 수 있다.
    
    ```

2. 추가 예정
    ```python3
    ```
