[DEAP](https://github.com/deap/deap)의 사용 예시 코드 스니펫 모음집

DEAP은 2012년 발표(?)된 유전 알고리즘 관련 파이썬 라이브러리다.  [DEAP: A Python framework for Evolutionary Algorithms](https://www.researchgate.net/publication/235707002_DEAP_A_Python_framework_for_Evolutionary_Algorithms)을 참고.


DEAP의 핵심은 크게 2가지로 나뉜다. **```creator```**, **```toolbox```**, 
- **```creator```**: 상속inheritance와 구성composition을 통해 런타임에 클래스를 생성한다. 만든 클래스에는 데이터나 함수 등의 속성을 추가할 수 있다. 리스트, 셋, 딕셔너리 등 자료구조에 구애받지 않고 유전형을 생성할 수 있다.
- **```toolbox```**: 유전 연산자를 담는 도구상자라고 생각할 수 있다. 프로그래머는 사용할 연산자를 고른 후 toolbox에 등록register하는 과정을 거치고, 후에 등록 시 사용했던 alias를 통해 접근 가능하다.


이런 모듈들도 있다. ```algorithms```, ```base```, ```dtm```

- ```algorithms```: 고전적인 진화 알고리즘을 포함하고 있다. 알고리즘들의 이름이 굉장히 낯설다...
    - generational
    - (\mu . \lambda)
    - (\mu + \lambda)
    - ask-and-tell(Collette et al., 2010)
    
- ```base```: generic fitness object 등이 들어있다. 진화 알고리즘에서 많이 쓰이는 자료구조들에 대한 내용이다.
- ```dtm```: 초창기 논문에는 소개가 되어 있는데, 현재는 사라진 모듈인 것 같다. 대신 [Basic tutorials part 4: Using Multiple Processors](https://deap.readthedocs.io/en/master/tutorials/basic/part4.html)를 참고해서 분산 계산을 해야겠다! 





- DEAP을 사용하는 간단한 튜토리얼 [Using Genetic Algorithms for optimizing your models](https://hub.packtpub.com/using-genetic-algorithms-for-optimizing-your-models-tutorial/) by Natasha Mathur
    - 내가 가진 글자를 알아맞추는 유전 알고리즘을 만들어 봅시다! 
    - LSTM 모델의 RMSE를 줄이는 window size와 hidden unit의 개수를 맞춰봅시다! 
