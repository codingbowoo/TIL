LSTM구현의 detail이 보고 싶었을 뿐이고...

디테일은 ```LSTM```을 타고 ```RNNBase```을 거쳐 ```_VF```까지 왔는데 이친구의 상상도 못한 정체를 보았다.

[_VF.py](https://github.com/pytorch/pytorch/blob/f70945b1c34ca730311bc211919107e5f9f26feb/torch/_VF.py)

```python3
import torch
import sys
import types


class VFModule(types.ModuleType):
    def __init__(self, name):
        super(VFModule, self).__init__(name)
        self.vf = torch._C._VariableFunctions

    def __getattr__(self, attr):
        return getattr(self.vf, attr)

sys.modules[__name__] = VFModule(__name__)
```

그럼 torch._C는 어디 있느냐! 했는데 아무리 찾아도 _C.py는 없었고, 아래 링크가 내가 찾은 답변이다.

- [Where does `torch._C` come from?](https://discuss.pytorch.org/t/where-does-torch-c-come-from/2015/10)
- [torch._C._functions](https://github.com/pytorch/pytorch/blob/ded3a3b317fbc8b165235c98f238c193e1482ad5/torch/csrc/autograd/functions/init.cpp#L239)

c++ 이라, 조금 읽어보다가 눈물을 머금고 일단 후퇴했다...<br>

추가로 

- [https://stackoverflow.com/questions/48874968/how-to-find-functions-imported-from-torch-c-in-source-code](https://stackoverflow.com/questions/48874968/how-to-find-functions-imported-from-torch-c-in-source-code)
- [A Tour of PyTorch Internals (Part I)](https://pytorch.org/blog/a-tour-of-pytorch-internals-1/)
