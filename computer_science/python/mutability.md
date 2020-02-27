# Mutability

> python 공부를 하다 보면 한 번 쯤은 mutable/ immutable object 라는 말을 들어보았을 것이다. 
나 역시도 예외가 아니고, 그저 바뀌는/ 바뀌지 않는 정도로만 이해하고 있었다. 
그러나 이게 웬걸, 프로젝트에서 pandas의 DataFrame을 엄청나게 자주 사용하면서 '나는 값을 바꿨는데.. 분명 바꿨는데.. 어찌 아무것도 바뀌지 않는가...'의 
굴레에 빠지고 나니 mutable vs immutable 을 정리해 봐야겠다는 생각이 냉큼 들었다. 


먼저 예시를 살펴보는 것도 좋겠다. <br>
앞서 pandas 이야기를 꺼냈는데, 
[Pandas Package Overview: Mutability and copying of data](https://pandas.pydata.org/pandas-docs/stable/getting_started/overview.html#mutability-and-copying-of-data)에
친절한 설명이 나와있다. 
```
All pandas data structures are value-mutable (the values they contain can be altered) but 
not always size-mutable. The length of a Series cannot be changed, but, for example, 
columns can be inserted into a DataFrame. However, the vast majority of methods produce new 
objects and leave the input data untouched. In general we like to favor immutability where sensible.
```

이론으로 가보자. Python3 documentation에서 일부를 따왔다.

```
The value of some objects can change. Objects whose value can change are said to be mutable; objects 
whose value is unchangeable once they are created are called immutable. (The value of an immutable 
container object that contains a reference to a mutable object can change when the latter’s value is 
changed; however the container is still considered immutable, because the collection of objects it 
contains cannot be changed. So, immutability is not strictly the same as having an unchangeable value, 
it is more subtle.) 
An object’s mutability is determined by its type; 
for instance, numbers, strings and tuples are immutable, while dictionaries and lists are mutable.
```

###### 참고문헌
- [python3 documentation 3.1. Objects, values and types](https://docs.python.org/3/reference/datamodel.html)
