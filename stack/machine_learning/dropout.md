# Dropout
논문 [Dropout: A Simple Way to Prevent Neural Networks from Overfitting](http://jmlr.org/papers/v15/srivastava14a.html)

- overfitting을 막기 위해 regularize(정규화) ~~개인적으로 standardization표준화와 종종 한국어가 헷갈린다~~하는 방법들 중 하나인 Dropout
- 의도적으로 몇몇 값을 0으로 바꿔버린다. (forward-pass할 때 신경망의 연결을 끊는 것!)

#### Pytorch의 예시
- [PyTorch documentation Dropout layers](https://pytorch.org/docs/stable/nn.html#torch.nn.Dropout)
    - parameters 중 p 는 0이 되는 원소의 비율이다. 기본값은 0.5이고, 베르누이이항분포에 따라 랜덤하게 정한다.
        - ```torch.nn.LSTM```의 parameters 중에도 dropout이 있는데 이 때 기본값은 0이다. <br>
        자세한 것은 공식문서 참고하기 [PyTorch documentation LSTM](https://pytorch.org/docs/stable/nn.html#lstm) 
    - inplace – If set to True, will do this operation in-place. Default: False
    - [FAQ] 앗! dropout은 training할 때만 사용해야 하는거 아닌가요? 그럼 test할 때는 dropout을 제외한 모델을 따로 만들어 사용해야 하나요?
        - A: 그건 아니고, 그저 test 전에 ```model.eval()```을 불러만 주십시오. <br>그럼 알아서 dropout을 건너뜁니다.
        - Q: 왜요?!
        - A: ```torch.nn.functional```의 구현을 보면 training=True일때만 dropout을 적용한다고 해요.


###### 참고자료
- [SOURCE CODE FOR TORCH.NN.MODULES.DROPOUT](https://pytorch.org/docs/stable/_modules/torch/nn/modules/dropout.html)
- [SOURCE CODE FOR TORCH.NN.FUNCTIONAL](https://pytorch.org/docs/stable/_modules/torch/nn/functional.html)
