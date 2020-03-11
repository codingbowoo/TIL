# TensorDataset and DataLoader


Pytorch에서 minibatch사용을 도와주는 친구는 ```DataLoader```이다.

일반적으로 가공한 데이터를 DataLoader에 넘길 때는 [Dataset](https://pytorch.org/docs/stable/data.html#torch.utils.data.Dataset) 클래스로 가공해야 한다.
[TensorDataset](https://pytorch.org/docs/stable/data.html#torch.utils.data.TensorDataset)의 인자로 가공한 input, label tensor를 넘겨주면 된다. (이 때 input과 label을 mapping하므로 첫 차원의 값이 같아야 한다. )


TensorDataset은 이렇게 동작한다. tensor를 넣어주면 Dataset을 만들어 주는 것.
```python3
class TensorDataset(Dataset):
    r"""Dataset wrapping tensors.

    Each sample will be retrieved by indexing tensors along the first dimension.

    Arguments:
        *tensors (Tensor): tensors that have the same size of the first dimension.
    """

    def __init__(self, *tensors):
        assert all(tensors[0].size(0) == tensor.size(0) for tensor in tensors)
        self.tensors = tensors

    def __getitem__(self, index):
        return tuple(tensor[index] for tensor in self.tensors)

    def __len__(self):
        return self.tensors[0].size(0)
```

**Custom dataset**을 쓸 때는  Kaggle kernel [PyTorch Dataset and DataLoader](https://www.kaggle.com/pinocookie/pytorch-dataset-and-dataloader?fbclid=IwAR2dfKfjljmnoJUdMIttrxffZF4kJOyG5kqzverzIVZoySGq3EJOtFNvqcA)를 참고하면 좋을 듯 하다! torch version이 0.4.0 인 것은 주의(본인 현재 v1.3.1 사용중), MNIST dataset으로 설명하고 있다.



## Dataloader

Pytorch에서는 흔히 ```torch.utils.data.DataLoader```로 접근할 수 있는 DataLoader를 사용한다. minibatch를 활용하기 좋다.
주어진 Dataset에 iterable을 제공한다. 


파라미터들을 간단히 살펴보자면

- ```dataset``` (Dataset): 내가 load할 Dataset이다. map-style과 iterable-style 모두를 지원한다.
- ```batch_size``` (int, optional)```: 한 배치에 들어갈 샘플 개수(default: 1).
- ```shuffle``` (bool, optional): True일 경우 각 에폭마다 데이터 순서를 섞는다(default: False).
    - time-series data에서는 True로 설정할 일이 없어 보인다.
- ```sampler``` (Sampler, optional): dataset에서 sample을 뽑는 방법이다. 사용하려면 shuffle여부가 False여야만 한다. sampler에 대한 설명은 [여기](https://pytorch.org/docs/master/data.html#torch.utils.data.Sampler)를 참고하자.
- ```batch_sampler``` (Sampler, optional): 위 sampler와 비슷하지만 batch에 해당하는 내용이다. batch단위의 샘플링을 할 때 쓴다.  batch_size, shuffle, sampler, drop_last와 공존할 수 없다(mutually exclusive).
- ```num_workers``` (int, optional): 데이터를 불러올 때 몇 개의 subprocess를 사용할 것인가. 0은 메인 프로세스에 불러올 것이라는 뜻이다.(default: 0)

- ```collate_fn``` (callable, optional): 미니배치를 형성하기 위해 샘플들의 리스트를 병합하는 함수를 넣어준다. map-style dataset에서 미니배치를 불러올 때 사용한다. --> input의 길이가 다양할 경우 batch가 자동생성되지 않고 에러가 나므로 collate_fn을 사용한다.
    - [여기](https://pytorch.org/docs/master/data.html#dataloader-collate-fn)를 참고하자. 
- ```pin_memory``` (bool, optional) – True로 설정하면 텐서를 return하기 전에 CUDA pinned memory에 복사한다. 데이터가 custom type이거나 collate_fn을 사용했을 경우 documentation의 별도 예시를 보자.
    - 간단하게 설명하면 CUDA를 사용하는 GPU의 경우 데이터를 더 빠르게 왔다갔다 하게 해주는 것이다.
- ```drop_last``` (bool, optional): True일 경우 배치 사이즈가 모자란 마지막 배치를 제외한다. (default: False)
- ```timeout``` (numeric, optional): 양수일 경우 workers에서 배치를 가지고 올 때의 timeout value에 해당한다. 0이거나 양수여야 한다. (default: 0)

- ```worker_init_fn``` (callable, optional): None이 아닐 경우 각 worker subprocess를 시작할 때 호출할 함수를 설정할 수 있다. (default: None)



###### 참고자료
- [Pytorch documentation torch.utils.data.DataLoader](https://pytorch.org/docs/stable/data.html#torch.utils.data.DataLoader)
- [Guidelines for assigning num_workers to DataLoader](https://discuss.pytorch.org/t/guidelines-for-assigning-num-workers-to-dataloader/813)
- [Github Issue: How to load huge file of data?](https://github.com/pytorch/text/issues/130#issuecomment-531901039) for ```pytorch/text```



