## RNN

- networks with loops in them (they looks similar to original neural network when unrolled)
- sequence, list 형태의 데이터를 처리하는 구조(아키텍처)
  - 직전의 정보와 현재의 정보를 연결할 수 있다.
- 음성인식, 언어 모델링, 번역, 이미지 캡셔닝 등에 쓰임


#### 문제점

##### Long-term dependencies
이론상으로는 서로 영향을 주는 요소들이 멀리 떨어져 있어도 반영이 가능하지만, 실제로는 이 간격이 멀어질수록 정보를 연결하기 어려워진다.


###### 링크
[Chris(송호연)님의 LSTM(RNN)소개](https://brunch.co.kr/@chris-song/9)
