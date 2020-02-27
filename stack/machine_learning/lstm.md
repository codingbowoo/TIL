## LSTM이란?

- **L**ong-**S**hort **T**erm **M**emory network**s**
- 특별한 형태의 RNN (Recurrent Neural Network)
- [Gers, Felix A., Jürgen Schmidhuber, and Fred Cummins. "Learning to forget: Continual prediction with LSTM." (1999): 850-855.](https://digital-library.theiet.org/content/conferences/10.1049/cp_19991218)
- [Greff, Klaus, Rupesh K. Srivastava, Jan Koutník, Bas R. Steunebrink, and Jürgen Schmidhuber. "LSTM: A search space odyssey." IEEE transactions on neural networks and learning systems 28, no. 10 (2016): 2222-2232.](https://ieeexplore.ieee.org/abstract/document/7508408)

덧붙이자면, 
아마 LSTM과 관련해서 가장 유명한 블로그 글로 [Understanding LSTM Networks](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)가 있다.

### 어디에 쓰이는가?
음성인식/언어모델링/기계번역/이미지에 설명달기(image captioning) 등 다양한 task에 쓰인다. 
- [Sundermeyer, Martin, Ralf Schlüter, and Hermann Ney. "LSTM neural networks for language modeling." In Thirteenth annual conference of the international speech communication association. 2012.](https://www.isca-speech.org/archive/interspeech_2012/i12_0194.html)
- [Graves, Alex, Navdeep Jaitly, and Abdel-rahman Mohamed. "Hybrid speech recognition with deep bidirectional LSTM." In 2013 IEEE workshop on automatic speech recognition and understanding, pp. 273-278. IEEE, 2013.](https://ieeexplore.ieee.org/abstract/document/6707742)

Q. 나는 어디에 쓸 것인가? 왜 쓸 것인가? <br>
A. 내가 다루는 금융 데이터도 시계열적인 특징이 있지.


### LSTM 이용 다양한 아키텍처

#### (Vanilla) LSTM
- 가장 기본 LSTM
- long-term dependency problem: 기존 RNN의 필요한 정보의 거리가 멀어지면 연결이 힘들다는 단점을 극복하고자 한다. 
- 기존 RNN의 반복 구조에 tanh layer 하나가 있었다면, LSTM에는 4개의 layer가 있다. 
- 가장 핵심은 **Cell state**의 존재, 그리고 이 Cell state에 정보를 더하고 빼는 것이 3개의 **gate**라는 구조
  - Gate는 Sigmoid층과 pointwise multiplication 연산으로 구성된다.
  1. Forget gate layer
      - 지난 timestep t-1의 output(hidden state)와 현재 timestep t의 input을 받는다.
      - sigmoid layer에서 잊을 정보를 결정한다. 결과가 0이면 모두 잊는다 / 1이면 모두 기억한다.
  2. Input gate layer
      - 지난 timestep t-1의 output와 현재 timestep t의 input을 받는다.
      - sigmoid layer에서 *cell state에 추가할 정보* 를 결정한다.
  3. tanh layer에서 새로운 후보 value를 생성하고, 두 layer(input gate sigmoid, tanh)의 결과를 합친다.
  4. cell state를 업데이트한다. 
      - forget gate 결과를 multiply
      - input gate 결과를 add
  5. 업데이트한 cell state 결과를 바탕으로 결과output 값을 결정한다. 
      - *sigmoid layer를 통과한 timestep t-1의 hidden state* (범위 0~1)와
      - *tanh layer를 통과한 cell state* (범위 -1 ~ 1)를 더해준다. 

- 파이토치 튜토리얼 [SEQUENCE MODELS AND LONG-SHORT TERM MEMORY NETWORKS](https://pytorch.org/tutorials/beginner/nlp/sequence_models_tutorial.html)

가장 기본적인 LSTM cell 하나는 아래처럼 사용할 수 있다. 
LSTM과 관련한 파이토치 문서는 [여기](https://pytorch.org/docs/stable/nn.html#lstm)를 참고하자.
```python3
import torch
import torch.nn as nn

lstm = nn.LSTM(10, 10, 2)

_input = torch.randn(5, 3, 10)
h0 = torch.randn(2, 3, 20)
c0 = torch.randn(2, 3, 20)

output, (h_n, c_n) = lstm(_input, (h_0, c_0))
```

일반적으로 아래처럼 class를 만들어서 사용한다. 
아래 예시는 output을 만들 때 Fully connected(nn.Linear)
```python3
class LSTM(nn.Module):
    def __init__(self, input_size=1, hidden_size=100, output_size=1):
        super().__init__()
        self.hidden_size = hidden_size
        
        # torch.nn.LSTM(*args, **kwargs)
        self.lstm = nn.LSTM(input_size, hidden_size)
        
        #torch.nn.Linear(in_features, out_features, bias=True)
        self.linear = nn.Linear(hidden_size, output_size) 
        
        self.hidden_cell = (torch.zeros(1,1,self.hidden_size),
                            torch.zeros(1,1,self.hidden_size)) # (h_0, c_0)

    def forward(self, input_seq):
        lstm_out, self.hidden_cell = self.lstm(input_seq.view(len(input_seq) ,1, -1), self.hidden_cell)
        predictions = self.linear(lstm_out.view(len(input_seq), -1))
        return predictions[-1]
```


#### Stacked LSTM

- LSTM을 쌓은 구조. 한 층의 결과값을 위 층의 input으로 사용하자.
- 위로 위로 쌓아 올려서 가장 위의 LSTM 층의 결과값을 최종 결과로 사용한다. 

이거 사용한 논문은 뭐가 있냐면 뫄뫄가 있다.
쌓았다는 말이 무슨 말이냐면
여기서는 인풋을 뭘 쓰고 아웃풋은 뭘 원한다
그래서 기본 구조 안쓰고 쌓아올렸다

#### LSTM-AE
- [Srivastava, Nitish, Elman Mansimov, and Ruslan Salakhudinov. "Unsupervised learning of video representations using lstms." In International conference on machine learning, pp. 843-852. 2015.](http://proceedings.mlr.press/v37/srivastava15.pdf)
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
 
 #### Resource
- Pytorch tutorial
-[SEQUENCE MODELS AND LONG-SHORT TERM MEMORY NETWORKS](https://pytorch.org/tutorials/beginner/nlp/sequence_models_tutorial.html)
