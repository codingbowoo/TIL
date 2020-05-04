# PyTorch Loss Function


아래와 같은 Fully Connected Layer 3개(+ 사이사이에 ReLU)로 구성한 Net이 있다고 하자
```python3
import torch
import torch.nn as nn
import torch.nn.functional as F

class Net(nn.Module):
    
    def __init__(self):
        super(MLP, self).__init__()
        self.fc1 = nn.Linear(21*12, 21*6)
        self.fc2 = nn.Linear(21*6, 21)
        self.fc3 = nn.Linear(21, 1)
    
    def forward(self, x):
        x = x.view(-1, self.num_flat_features(x))
        x = F.relu(self.fc1(x))
        x = F.relu(self.fc2(x))
        x = self.fc3(x)
        return x
    
    def num_flat_features(self, x):
        size = x.size()[1:] # all dimensions except the batch dimension
        num_features = 1
        for s in size:
            num_features *= s
        return num_features
```

```python3
net = Net()
_input = torch.randn(1, 252)
output = net(_input)

target = torch.randn(1)
target = target.view(1, -1)

criterion = nn.MSELoss()

loss = criterion(output, target)
```
위와 같이 해주면 ```grad_fn```으로 다음 함수를 확인할 수 있다.
```python3
print(loss.grad_fn)
print(loss.grad_fn.next_functions)

# Output:
# <MseLossBackward object at 0x7fbb7fd070f0>
# ((<AddmmBackward object at 0x7fbb7fd07cf8>, 0),)
```

꼬리에 꼬리를 물고 확인 가능하다. 이 예시에서는 처음에 net의 flow가 아래와 같다.
> input -> view -> linear -> relu -> linear -> relu -> linear <br>
> -> MSELoss <br>
> -> loss <br>

```grad_fn```과 ```next_functions```로 그래프를 백트래킹 해보면 다음과 같다. (괄호 안을 주목, **연결고리는 굵은 글씨**)
> input -> view(<AccumulateGrad, None, TBackward object>) <br>
-> linear(\<**AddmmBackward** object>) -> relu(<AccumulateGrad,**ReluBackward0**, TBackward object>)<br>
-> linear(\<**AddmmBackward** object>) -> relu(<AccumulateGrad,**ReluBackward0**, TBackward object>) <br>
-> linear(\<**AddmmBackward** object>) <br>
> -> MSELoss(\<**MseLossBackward** object>) <br>
> -> loss <br>

###### resources
- [Pytorch tutorial loss function](https://pytorch.org/tutorials/beginner/blitz/neural_networks_tutorial.html#loss-function)
