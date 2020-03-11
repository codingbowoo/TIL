# Pytorch Datasets

Pytorch에는 두 가지 종류의 Dataset이 존재한다.

- Map-style datasets
- Iterable-style datasets

Map-style datasets는 **```Dataset``` class**와 관련이 있다.
- ```__getitem()__```, ```__len()__``` 메소드와 연관이 있고 인덱스나 키를 데이터 샘플들에 매핑시킨다.

```python3
class Dataset(object):
    r"""An abstract class representing a :class:`Dataset`.

    All datasets that represent a map from keys to data samples should subclass
    it. All subclasses should overwrite :meth:`__getitem__`, supporting fetching a
    data sample for a given key. Subclasses could also optionally overwrite
    :meth:`__len__`, which is expected to return the size of the dataset by many
    :class:`~torch.utils.data.Sampler` implementations and the default options
    of :class:`~torch.utils.data.DataLoader`.

    .. note::
      :class:`~torch.utils.data.DataLoader` by default constructs a index
      sampler that yields integral indices.  To make it work with a map-style
      dataset with non-integral indices/keys, a custom sampler must be provided.
    """

    def __getitem__(self, index):
        raise NotImplementedError

    def __add__(self, other):
        return ConcatDataset([self, other])
```


Iterable datasets는 **```IterableDataset``` class**의 subclass이다.
- ```__iter()__``` 메소드의 구현과 관련이 있다. 



###### resources
- [Pytorch documentation: Dataset Types](https://pytorch.org/docs/master/data.html#dataset-types)
- [Code for Dataset](https://pytorch.org/docs/master/_modules/torch/utils/data/dataset.html#Dataset)
