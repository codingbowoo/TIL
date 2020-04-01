# Python dictionary
##### Contents
- [Merge 2+ dictionaries](#merge-dicts)
- [Initialize a dictionary](#init-dicts)


<br>

* * *

#### Initialize a dictionary <a id="init-dicts"></a>
key의 목록만 Dictionary를 빈 리스트로 초기화 할 일이 많은데, 구글링 해보면 처음 찾을 수 있는 답 중에 이런게 있다.
```python3
keys = [1, 2, 3, 4]
d = dict.fromkeys(keys, [])

print(d)
# {1: [], 2: [], 3: [], 4: []}
```
문제는... 이 ```d```라는 dictionary는 초기화가 예쁘게 된 것 같지만 난처한 상황이 발생할 소지가 다분하다. 
key값이 1인 리스트에 1을 append를 하면 아래와 같은 상황을 볼 수 있다.
```python3
d[1].append(1)

print(d)
# {1: [1], 2: [1], 3: [1], 4: [1]} -> ?!
```
fromkeys 메소드의 경우 하나의 list object로 각 key의 value를 몽땅 초기화하기 때문에 이런 상황이 발생하는 것! documentation에 친절하게도

> All of the values refer to just a single instance, so it generally doesn’t make sense for value to be a mutable object such as an empty list. 

라고 쓰여있다. 그렇다면 각 key들을 서로 다른 주솟값을 가지는, 서로 다른 list로 어떻게 초기화해야 하지? 두 가지 방법이 있다! 
```python3
# 방법 1
d = {}
for key in keys:
    d[key] = []

# 방법 2
d = {key: [] for key in keys}

print(d)
# {1: [1], 2: [], 3: [], 4: []} -> 편-안
```
이제 append를 마음껏 할 수 있다! 

related to 
[python3 documentation dict.fromkeys()](https://docs.python.org/3/library/stdtypes.html#dict.fromkeys)

* * *

#### Merge 2 dictionaries <a id="merge-dicts"></a>

```python3
>>> d1 = {'a': 1, 'b': 2}
>>> d2 = {'c': 3, 'd': 4}

>>> d3 = {**d1, **d2}

>>> d3
{'d': 4, 'c': 3, 'b': 2, 'a': 1}
```

related to 
- [PEP448 (원문)](https://www.python.org/dev/peps/pep-0448/) 
- 정리노트 [pep448.md](https://github.com/codingbowoo/codingbowoo.github.io/blob/master/stack/pythonpractice/pep448.md)
