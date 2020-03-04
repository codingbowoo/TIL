# Series

pandas object 중 dataframe 다음으로 애정하는 Series


유용해보이는 함수 몇 가지를 기록해둘 예정!

아래와 같이 pandas를 import 했고 모종의 데이터가 든 Series object가 있다고 가정한다.
```python3
import pandas as pd
sr = pd.Series()
```

1. **value_counts**: series 안에 서로 다른 값들의 개수를 세어 준다.
   ```python3
   sr.value_counts()               # check if classification problem
   sr.value_counts(normalize=True) # 위 결과(count 수)를 normalize해서 보여준다
   sr.value_counts(ascending=True) # count 수를 기준으로 오름차순/내림차순으로 볼 수 있다. 
   sr.value_counts(dropna=False)   # NaN이 몇 개 인지 볼 수 있다.
   sr.value_counts(bins=10)        # bin 개수를 설정하면 이 경우는 10개 카테고리로 값 range를 나눠서 count 결과를 보여준다.
   ```
   
   
1. **추가 예정**
   ```python3
   ```
