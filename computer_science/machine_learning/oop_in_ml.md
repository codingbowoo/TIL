# OOP in ML
Object-Oriented Programming in Machine Learning


내가 슬슬 스스로 코드를 짜면서 아주 난처하게 여기는 순간들이 있었는데, 예를 들면 이런 거다.

> **나: 머신러닝 모델 만들거다! train도 하고 test도 할거다!**

1. 인터넷의 튜토리얼: main에서 train도 test도 한다
    - ```class MLModel():``` 아래에는 ```__init__()```, ```forward()```, 그리고 가끔 ```init_hidden()```정도?
    - ~~그리고 대부분 패키지에서 제공하는 Dataset을 쓴다~~(이 문서와는 무관하나 나는 아주 난처해..)
    
2. 깃헙에서 찾은 누군가의 코드 : 모델 class 내부에 train, test를 메소드로 구현했다.
    - 사실 튜토리얼들 찾아보다가 이런 구성도 봤으나 지나쳤다
    - 물어볼 수가 없다 (여러 이유로)
    
3. 내 코드 : 없을 무


대략 ```???``` 한 상태가 되는데, 1은 따라하기 쉽지만 튜토리얼마다 내용이 조금씩 다르고, 보통 내 (특수한) 상황에 적용하려면 고생을 많이 한다.
2는 다소 복잡하므로 코드를 읽어내는 데 시간이 오래 걸리고, 이 코드의 작성자가 왜 이렇게 짰는지에 대한 고민이 필연적으로 따라온다. 
보통 나는 고민을 많이 하다가 손을 늦게 움직이는 편(...)

그런데 적어도 **머신러닝 모델 클래스**에 대해서는 이런 고민을 좀 덜어줄 글을 발견했다! 

- [Object-oriented programming for data scientists: Build your ML estimator](https://towardsdatascience.com/object-oriented-programming-for-data-scientists-build-your-ml-estimator-7da416751f64) by Tirthajyoti Sarkar
- [Understanding Object-Oriented Programming Through Machine Learning](https://dziganto.github.io/classes/data science/linear regression/machine learning/object-oriented programming/python/Understanding-Object-Oriented-Programming-Through-Machine-Learning/) by David Ziganto


