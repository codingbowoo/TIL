앞서 [recursionlimit](https://github.com/codingbowoo/codingbowoo-resource/blob/master/stack/pythonpractice/recursionlimit.md) 
문서에서의 문제 상황을 당장 해결했지만, 도무지 recursion이 발생하는 포인트를 찾지 못했다. <br>
그리고 범인은 바로바로...

# metaclass

Metaclass가 뭐야? 한다면 python3.7 documentation [Metaclasses](https://docs.python.org/3.7/reference/datamodel.html#metaclasses)<br>
간단하게 설명하자면, (type을 상속받아서) 클래스를 만드는 클래스 이다. 
실제 사용 예시는 라이브러리의 클래스에서 많이 찾아볼 수 있는데, 구체적인 예시로 pandas의 DataFrame이 있다.

```python3
type(pandas.DataFrame)
```

를 실행시키면 

```
type
```

이라는 결과를 얻을 수 있다.

+) 내가 새로운 class를 만들어서, 예를 들어 pandas의 DataFrame을 상속하는 myDataFrame을 생성했다고 하자. <br>
내가 생성한 myDataFrame은 DataFrame과 동일한 성질을 가진다. (어떤 메타클래스의 instance이다.)

클래스 정의에 지정된 키워드 인수들arguments은 아래 메타클래스 작업을 거친다. 

1. MRO(Method Resolution Order) 결정 <br>
   : ```클래스이름.mro()``` 또는 ```클래스이름.__mro__```로 현재 클래스의 메소드 탐색 순서를 확인할 수 있다.
2. Metaclass 결정 <br>
   : 일반적으로 ```object```
3. class namespace 준비
4. class body 실행


* * *
위 [recursionlimit](https://github.com/codingbowoo/codingbowoo-resource/blob/master/stack/pythonpractice/recursionlimit.md) 문서에서의 문제 상황을 다시 살펴보자.
```python3
import pandas as pd
import utils as u   #자체제작한 모듈 utils.py

class myDataFrame(pd.DataFrame):
    def __init__(self):
        self.daily = u.read_data("../data/Daily.csv") 
        """ utils.py
        def read_data(filepath):
            df_r = pd.read_csv(filepath, index_col=[0])
            # 중략
            return df_r
        """
```


나의 의도는 pd.read_csv()의 결과물을 DataFrame으로 받자!였으나, 이 경우 DataFrame 대신 pd.read_csv가 그 결과를 myDataFrame으로 반환한다. 따라서 recursionlimit 에러가 발생한다. 
DataFrame을 반환하는 다른 판다스 함수들도 myDataFrame으로 반환을 시도할 것이다. 당연히 recursion이 발생한다.


정리해보면 아래와 같다.

> 1. myDataFrame()을 생성
> 2. (init 중) pd.load_csv()를 호출
> 3. pd.load_csv() 결과를 저장하자. 어디에? pd.DataFrame을 상속받은 클래스(myDataFrame)에!
> 4. 1 로 이동 및 무한반복


해당 상속을 없애주는 것/ 함수로 만드는 것으로 문제를 해결할 수 있다. 잘 알아보고 사용하기!
