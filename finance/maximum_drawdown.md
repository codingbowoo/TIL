# Maximum Drawdown(MDD)

**최대 낙폭**이라고 번역할 수 있는 maximum drawdown(이하 MDD)는 [1, T]의 시간동안 어떤 주식을 보유(hold)한 상태에서 발생할 수 있는 최대 손실을 의미한다. 
[1,T]의 시계열 중 이전 최고점(peak)에서 최저점(trough)까지의 낙폭 중 최댓값이다.


수익률이 series로 들어온다고 가정했을 때 mdd를 구하는 코드는 다음과 같다.
- mdd는 price와 관련된 개념이므로 가격으로 변환하여 mdd를 구한다.
- ```get_times=True```면 해당 MDD의 최고점, 최저점이 언제인지 그 날짜도 함께 반환한다.

```python3
import pandas as pd

def maximum_drawdown(rtrn, get_times=False):
    assert isinstance(rtrn, pd.Series)
    p = (rtrn.sort_index(ascending=True)+1).cumprod()
    
    drawdowns = {}
    t_max = p.index[0]
    max_so_far = p.iloc[0]
    
    for idx, item in p.iteritems():
        if item > max_so_far:
            t_max = idx
            max_so_far = item
            drawdown = 0  
        else:
            drawdown = (max_so_far - item)/max_so_far
        drawdowns[(t_max, idx)] = drawdown
        
    mdd = max(drawdowns.values())
    t_max, tau = max(drawdowns, key=drawdowns.get)
    
    if get_times==False:
        return mdd
    else:
        return mdd, t_max, tau
```

https://github.com/GreatYoungShaw/Calculating-maximum-drawdown 의 코드를 참고했다.
- 위 레포와 달리 pandas Series 타입 dependent하다.
- 특정 날짜(혹은 인덱스)를 반환하는 기능을 추가했다.
