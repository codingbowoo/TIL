# batch normalization

batch: training할 때 전체 데이터를 나누는 단위(?)
normalization: normal distribution으로 만든다. mean과 standard deviation으로 정의하는, 정규분포 형태로 만들어준다.

batch의 mean과 std를 가지고 정규분포를 만들어준다. 

### 왜?
hidden layer의 결과값은 input과 상이한 분포를 가질 수 있기 때문에.
- [Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift](https://arxiv.org/abs/1502.03167)
- [PyTorch nn.BathNorm1d](https://pytorch.org/docs/master/generated/torch.nn.BatchNorm1d.html#torch.nn.BatchNorm1d)

### RNN에 써도 돼?
- [RECURRENT BATCH NORMALIZATION](https://arxiv.org/pdf/1603.09025.pdf)
- 쉽게(?) 구현하는 건 어렵다. batch는 과거를 고려할 수 있는 단위가 아니다(?) 
    - RNN류는 대신 [layer normalization](https://arxiv.org/abs/1607.06450)을 하기도 한다고.

#### 구현체
- https://github.com/hellozgy/bnlstm-pytorch/blob/master/bnlstm.py
- https://github.com/jihunchoi/recurrent-batch-normalization-pytorch/blob/master/bnlstm.py
