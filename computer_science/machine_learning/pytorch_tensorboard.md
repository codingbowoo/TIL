자세한 것은 https://www.tensorflow.org/tensorboard/ 를 참고하자.


설치
```shell
pip install tensorboard
```

실행
```shell
tensorboard --logdir=runs
```

# [Tensorboard in PyTorch](https://pytorch.org/docs/stable/tensorboard.html)

기본 세팅은 아래와 같다. 기록을 하는데 핵심이 되는 것은 ```SummaryWriter```다.
```python3
import torch
from torch.utils.tensorboard import SummaryWriter

# Writer will output to ./runs/ directory by default
writer = SummaryWriter()

# 이렇게 comment를 붙일 수 있다. 
writer = SummaryWriter(comment="LR_0.1_BATCH_16")
```
이 상태에서 모델을 부르고, 학습을 시킨다.

그런 다음 Tensorboard에서 확인하고 싶은 항목들을 추가해준다. 


scalar, histogram, image, matplotlib figure, video, audio, text, pr(precision/recall) curve, hyperparameter 등을 추가할 수 있다.
```python3
writer.add_scalar('tagname(eg.Loss/train)', np.random.random(), 0) # tag, scaler_value, global_step=None
writer.add_text('tagname', 'Lorem Ipsum', 0) # tag, text_string, global_step=None
writer.add_graph(model) # model, input_to_model=None, verbose=False
for i in range(5):
        writer.add_hparams({'lr': 0.1*i, 'bsize': i},
                           {'hparam/accuracy': 10*i, 'hparam/loss': 10*i})
```

마무리로 
```python3
writer.close()
```


