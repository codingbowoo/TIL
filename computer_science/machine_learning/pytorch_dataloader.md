# batch



Pytorch에서 minibatch사용을 도와주는 친구는 ```DataLoader```이다.

- [Guidelines for assigning num_workers to DataLoader](https://discuss.pytorch.org/t/guidelines-for-assigning-num-workers-to-dataloader/813)
- [Pytorch documentation torch.utils.data.DataLoader](https://pytorch.org/docs/stable/data.html#torch.utils.data.DataLoader)

일반적으로 가공한 데이터를 DataLoader에 넘길 때는 [Dataset](https://pytorch.org/docs/stable/data.html#torch.utils.data.Dataset) 클래스로 가공해야 한다.
[TensorDataset](https://pytorch.org/docs/stable/data.html#torch.utils.data.TensorDataset)의 인자로 가공한 input, label을 넘겨주면 된다.
(이 때 input과 label의 첫 차원의 값이 같아야 한다.


참고로 TensorDataset은 이렇게 동작한다. tensor를 넣어주면 Dataset을 만들어 주는 것.
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


