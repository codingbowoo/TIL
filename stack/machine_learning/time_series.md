Medium article
- [A basic guide to time series analysis](https://towardsdatascience.com/a-basic-guide-into-time-series-analysis-2ad1979c7438)


time series는 기본적으로 autocorrelation(자기상관) 성질이 있다. 

요즘 관심을 두고 있는 것은 correlation을 활용하는 time series 이다.
- 읽어볼 것 [Learning Correlation Space for Time Series](https://arxiv.org/abs/1802.03628)
- Time-series에서의 Validation
    - [What's Wrong With My Time Series](https://multithreaded.stitchfix.com/blog/2017/02/28/whats-wrong-with-my-time-series/)
        - 시계열은 data에서 shuffle을 할 수 없다 이 말이야! 
        - 어떤 에러(model error/ assumption error)가 있는지 알고, 각각에 맞게 대응할 줄 알아야 한다.


pandas의 DateTimeIndex의 기본값인 Timestamp, 그리고 
```import datetime``` 을 해서 사용할 수 있는 datetime이 생각보다 활용도가 높을 수 있다.
