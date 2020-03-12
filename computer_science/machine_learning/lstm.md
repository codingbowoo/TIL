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
- long-term dependency problem: 기존 RNN의 필요한 정보의 거리가 멀어지면 연결이 힘들다는 단점을 극복하고자 한다. 기존 RNN의 반복 구조에 tanh layer 하나가 있었다면, LSTM에는 4개의 layer가 있다. 
- 가장 핵심은 **Cell state**의 존재, 그리고 이 Cell state에 정보를 더하고 빼는 것이 3개(Forget, Update, Output)의 **gate**라는 구조
  - Gate는 Sigmoid층과 pointwise multiplication 연산으로 구성된다.
  - sigmoid, tanh activation이 쓰이므로 input data의 scale에 민감하다! 
  
  
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


##### LSTM on Pytorch
LSTM과 관련한 파이토치 문서는 [여기](https://pytorch.org/docs/stable/nn.html#lstm)를 참고하자.

class torch.nn.LSTM(*args, \*\*kwargs)의 Parameter로는 
- input_size, hidden_size, num_layers, bias와 같은 수치,
- batch_first, dropout, bidirectional 여부 등이 있다.

input은 ```input, (h_0, c_0)``` 꼴인데, 이 때
- input의 shape는 (seq_len, batch, input_size) 
    - ```batch_first=True```인 경우엔 (batch, seq_len, input_size) 
- h_0과 c_0의 shape는 (num_layers * num_directions, batch, hidden_size)

output은 ```output, (h_n, c_n)``` 꼴이고, 
h_n, c_n은 각각 seq_len만큼의 time step의 hidden state와 cell state이다.
output은 LSTM 마지막 layer의 h_t와 동일한 값을 가진다.


LSTM을 아래와 같이 선언했다고 해보자.
```python3
import torch.nn as nn
model = nn.LSTM(input_size=1,\
                hidden_size=10,\
                num_layers=1,\
                batch_first=True,
                dropout=0.5,\
                bidirectional=False)
``` 
이 모델이 학습하는 파라미터들의 모양을 찍어보면 다음과 같다.
```python3
# 이렇게 찍는다
for params in model.parameters():
    print(type(params), params.shape)
    
# 결과
# <class 'torch.nn.parameter.Parameter'> torch.Size([40, 1])
# <class 'torch.nn.parameter.Parameter'> torch.Size([40, 10])
# <class 'torch.nn.parameter.Parameter'> torch.Size([40])
# <class 'torch.nn.parameter.Parameter'> torch.Size([40])
```
위에서부터, 

- LSTM.weight_ih_l[k] : input-hidden weight of shape (4*hidden_size, input_size)
    - num_layer가 1이 넘어갈 경우 두 번째 layer부터는 shape (4*hidden_size, num_directions * hidden_size)
- LSTM.weight_hh_l[k] : hidden-hidden weights of shape (4*hidden_size, hidden_size)
- LSTM.bias_ih_l[k] : input-hidden bias of shape (4*hidden_size)
- LSTM.bias_hh_l[k] : hidden-hidden bias of shape (4*hidden_size)

이고, hidden_size에 곱하는 **4**는 **input, forget, cell, output 4개의 gate**에 해당한다.

 
 #### Resource
- Pytorch tutorial
-[SEQUENCE MODELS AND LONG-SHORT TERM MEMORY NETWORKS](https://pytorch.org/tutorials/beginner/nlp/sequence_models_tutorial.html)
- LSTMCell을 사용한 예제 [LSTM for time series prediction](https://romanorac.github.io/machine/learning/2019/09/27/time-series-prediction-with-lstm.html)
