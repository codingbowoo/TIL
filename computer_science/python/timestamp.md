# Timestamp

DataFrame으로 시계열 자료를 다루다 보면 친해지는 Timestamp


csv파일에서 pandas의 ```read_csv()``` 함수를 읽어올 때 ```parse_dates```옵션을 주면 index를
```pandas.core.indexes.datetimes.DatetimeIndex```로 할 수 있다.


이 때 DatetimeIndex 내부의 element 하나하나는 예를 들자면 아래처럼 생겼다. 

```
Timestamp('1963-07-31 00:00:00')
```

자료형을 확인해보면 ```pandas._libs.tslibs.timestamps.Timestamp```라고 나온다. 


이 Timestamp를 다룰 때 유용하게 사용하는 함수 두 가지를 투척한다. 

1. Timestamp를 원하는 문자열 모양으로 바꾸기 **strftime**
   ```python3
   import pandas as pd
   
   # df 라는 DatetimeIndex를 가지는 DataFrame이 있다고 가정하자 
   # df.index[0] 을 print한 결과가 2020-03-04 00:00:00일 때 
   
   df.index[0].strftime("%Y--%m--%d")
   
   """
   Out: 
   2020--03--04
   """
   
   ```

2. 날짜(숫자) 문자열을 Timestamp로 바꾸기 **to_datetime**
   ```python3
   import pandas as pd
   
   pd.to_datetime('20200304')
   
   """
   Out: 
   2020-03-04 00:00:00
   """
   ```
