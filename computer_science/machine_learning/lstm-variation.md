#### Stacked LSTM

- LSTM을 쌓은 구조. 한 층의 결과값을 위 층의 input으로 사용하자.
- 위로 위로 쌓아 올려서 가장 위의 LSTM 층의 결과값을 최종 결과로 사용한다. 

이거 사용한 논문은 뭐가 있냐면 뫄뫄가 있다.
쌓았다는 말이 무슨 말이냐면
여기서는 인풋을 뭘 쓰고 아웃풋은 뭘 원한다
그래서 기본 구조 안쓰고 쌓아올렸다

#### LSTM-AE
- [Srivastava, Nitish, Elman Mansimov, and Ruslan Salakhudinov. "Unsupervised learning of video representations using lstms." In International conference on machine learning, pp. 843-852. 2015.](http://proceedings.mlr.press/v37/srivastava15.pdf)
사실 이건 단순히 LSTM에 Autoencoder를 연결한 것이 아니다! 인코더 LSTM와 디코더 LSTM을 사용

이 논문에서는 인풋을 뭘 쓰고 아웃풋은 뭘 원한다
그래서 기본 구조 쓰지 않고 인코더 디코더 구조를 쓰는데, 
이때 데이터 특성이 뭐뭐여서 LSTM을 사용한다. 
구성은 다음과 같다
- 인코더 LSTM
- 디코더 LSTM
- 뭔가 세번째 구조가 있을 것만 같군.
