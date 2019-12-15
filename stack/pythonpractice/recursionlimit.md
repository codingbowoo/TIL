살다살다 오늘(191215)은 이런 에러를 봤다.
```python3
RecursionError: maximum recursion depth exceeded
```

이것이 무엇인고 하니, 역시나 documentation에 정리가 되어있다.<br>

> exception [RecursionError](https://docs.python.org/3.7/library/exceptions.html#RecursionError)

이전에는 ```RuntimeError```로 분류되던 것인데, python3.5 버전부터 별도의 이름을 붙여 준 에러라고 한다.
Python에서는 최대 재귀recursion 깊이를 정해두는데, 이 최대 재귀 횟수를 넘어서 재귀 호출을 하고 있다는 뜻이다... <br>

<br>

> 왜 그런게 있나? 그게 뭔가?

최대 재귀 깊이를 설정함으로써 무한 재귀를 막고, <br>
C 스택에 오버플로우가 나서 Python이 정지하는 상황을 방지하기 위함이다.

이 제한limit은 플랫폼에 따라 다르고, 만약 더 깊은 수준의 재귀를 사용해야 한다면 limit값을 크게 해야 한다. 
그렇지만 과도한 재귀로 python이 멈춰버릴 수 있음을 염두에 두자.


이 문제는 여러 방법으로 해결할 수 있는데, 하나는 앞서 언급했듯 limit을 늘려주는 것이다. 

> [sys.setrecursionlimit(limit)](https://docs.python.org/3.7/library/sys.html#sys.setrecursionlimit)

위 함수를 통해 Python 인터프리터 스택의 최대 깊이를 늘릴 수 있다.

<br>

> 언제 이런 문제 상황이 발생하는가?

내 경우는 이런 문제가 있었다. 아래는 문제 부분만 단순화한, 내 코드의 일부분이다.
```python3
import pandas as pd
import utils as u   #자체제작한 모듈 utils.py

class myDataFrame(pd.DataFrame):
    def __init__(self):
        self.daily = u.read_data("../data/Daily.csv") 
        """ utils.py
        def read_data(filepath):
            df_r = pd.read_csv(filepath, index_col=[0])
            . . .
            return df_r
        """
```
요즘 class 연습을 하고 있는데, 이런저런 실험을 하다가 
class를 만들 때 상속을 받아놓고는 그만 내부에서 pd.read_csv라고 호출한 것이 화근이었나보다.
현재 코드에서는 pd.DataFrame을 상속받겠다고 했지만 실제로 사용하고 있지는 않아서, 
해당 상속을 없애주는 것으로 당장의 문제를 해결했다. <br>

그러나 만약 pandas 내부 클래스를 상속한다고 했을 때, 
어떻게 코드를 수정해야 pandas 내부의 함수를 내가 만든 class에서도 사용할 수 있을지는 아직 의문이다.
