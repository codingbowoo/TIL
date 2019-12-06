## LSTM이란?

- **L**ong-**s**hort **t**erm **m**emory
- 특별한 형태의 RNN (Recurrent Neural Network)

덧붙이자면, 
아마 LSTM과 관련해서 가장 유명한 블로그 글로 [Understanding LSTM Networks](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)가 있다.

### 어디에 쓰이는가?
(사용 논문)

- 나는 어디에 쓸 것인가? 왜 쓸 것인가?
: 내가 다루는 금융 데이터도 시계열적인 특징이 있지.

### LSTM 이용 다양한 아키텍처
- My code(github link)
#### Vanilla LSTM
가장 기본적인 LSTM 구조. 
뫄뫄 게이트와 뫄뫄 게이트로 구성
뫄뫄를 위한 것임
파이토치에서는 간단히 이렇게 할 수 있음

#### Stacked LSTM
LSTM을 쌓은 구조
쌓았다는 말이 무슨 말이냐면 
한 게이트를 통과해 나온게 
이거 사용한 논문은 뭐가 있냐면 뫄뫄가 있다.
여기서는 인풋을 뭘 쓰고 아웃풋은 뭘 원한다
그래서 기본 구조 안쓰고 쌓아올렸다

#### LSTM-AE
사실 이건 단순히 ㄹㅅㅌㅁ에 ㅇㅌㅇㅋㄷ를 연결한 것이 아니다! 
인코더 ㄽㅌㅁ와 디코더 ㄽㅌㅁ를 사용하는 것.
2016 스리뭐시기의 논문 뫄뫄에서 제안하고 있다.
이 논문에서는 인풋을 뭘 쓰고 아웃풋은 뭘 원한다
그래서 기본 구조 쓰지 않고 인코더 디코더 구조를 쓰는데, 
이때 데이터 특성이 뭐뭐여서 ㄽㅌㅁ를 사용한다. 
구성은 다음과 같다
- 인코더 ㄽㅌㅁ
- 디코더 ㄽㅌㅁ
- 뭔가 세번째 구조가 있을 것만 같군.
호..정이한테 물어보자. 호정아 사랑해.
 
 #### Resource
- Pytorch tutorial
-[SEQUENCE MODELS AND LONG-SHORT TERM MEMORY NETWORKS](https://pytorch.org/tutorials/beginner/nlp/sequence_models_tutorial.html)
