# python list
> 20191231의 이야기: 파이썬에서 가장 대표적이고 활용도가 좋은 자료형이 아마 list라고 생각한다. 
여러 자료형을 한번에 담을 수 있다는 점에서 다른 컴퓨터 언어들과는 다른- 특이한 자료형이랄까? 2019년의 마지막 날에 정리하기 딱 좋은 주제다 :blush:

## 각종 조작 방법
아래는 자주 쓰는, 기발하다고 여기는 리스트 조작법이다.

- 리스트 뒤집기
```python3
리스트[::-1]
```

- n열종대 줄세우듯 짝 짓는 리스트 만들기
```python3
리스트(zip(리스트1, 리스트2, ... , 리스트n))
```

- 리스트 앞에 인덱스 만들어서 반복문 돌기
```python3
for i, (리스트 내용) in enumerate(리스트):
```

## list comprehension
파이썬에는 물론, 아주 간단한 작업을 편하게 해주는 lambda, map, filter의 함수형 기능이 있지만 처음 보는 사람들이 쓰기에는 모양새도 잘 이해가 안가고, 
유연성이 떨어진다고 생각한다. 진입장벽이 좀 있는 함수형 대신 아래 list comphrehension을 사용해 보는 것은 어떨까?

python3.7 [list comprehension documentation](https://docs.python.org/3.7/tutorial/datastructures.html#list-comprehensions)
```python3
[ (x에 관한 식) for x in 리스트 if (x에 관한 조건) ]
```
크게 두 부분으로 나눌 수 있는데, 

1. ```(x에 관한 식) for x in 리스트``` <br>
(리스트)를 돌면서 각 element에 관한 식을 수행한다. 

2. ``` if (x에 관한 조건)```<br>
이 부분은 선택적으로 넣으면 된다. 이 조건을 만족하는 x에 대해서만 앞의 (x에 관한 식)을 수행한다.

###### resources
- [5 Python features I wish I had known earlier](https://towardsdatascience.com/5-python-features-i-wish-i-had-known-earlier-bc16e4a13bf4) by Eden Au
