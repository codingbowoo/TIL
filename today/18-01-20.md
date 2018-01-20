### venv, virtualenv, pyenv 너희 도대체 뭐니?

##### 사건의 발단


##### stackoverflow가 답을 알려줄거야
그럼 그렇지, 스택오버플로우에 누군가의 친절한 설명이 있다.

- [What is the difference between venv, pyvenv, pyenv, virtualenv, virtualenvwrapper, pipenv, etc?](https://stackoverflow.com/questions/41573587/what-is-the-difference-between-venv-pyvenv-pyenv-virtualenv-virtualenvwrappe/41573588)

- [What is the relationship between virtualenv and pyenv?](https://stackoverflow.com/questions/29950300/what-is-the-relationship-between-virtualenv-and-pyenv)

정리해보자면,

###### 1. Python standard library
- venv (Python > 3.3)
    - ```$ python3 -m venv``` 하면 바로 사용할 수 있다. 3.4이상 버전에는 깔려 있지롱

###### 2. PyPI package
- virtualenv
- virtualenvwrapper
    - virtualenv의 extension이다.
    - 눈에 띄는 기능으로는 여러 virtualenv 디렉토리들을 넘나드는 ```workon``` 명령어가 있는듯.
- pyenv
    - Python version들을 혼용해서 사용할 때, 그들을 분리해주는 데에 사용한다. 'multiple python'이 핵심 단어라고 할 수 있을 듯
- pyenv-virtualenv
    - ```virtualenv```를 ```pyenv```와 통합하기 위한 플러그인이다.
    
- pyenv-virtualenvwrapper
    - ```virtualenvwrapper```를 ```pyenv```와 통합하기 위한 플러그인이다.  
- pipenv
    - ```pip``` + ```virtualenv``` (좀이따 봅시다)




참고 링크
- [Python3 documentation - venv](https://docs.python.org/3/library/venv.html)
- [Creating Virtual Environment](https://packaging.python.org/tutorials/installing-packages/#creating-virtual-environments)
- [vitrualenvwrapper on PyPIi](https://pypi.python.org/pypi/virtualenvwrapper)
- [virtualenvwrapper on Bitbucket](https://bitbucket.org/virtualenvwrapper/virtualenvwrapper/overview)
- [pyenv-virtualenvwrapper on github](https://github.com/pyenv/pyenv-virtualenvwrapper)
 



* * * 

### pip ? pipenv ?

virtualenv 관련하여 이런 저런 검색을 하다가는 ```pip```와 ```pipenv```와 마주하고야 말았다 (...)

그동안 수도 없이 많은

```
$pip install --upgrade
$pip install (package 이름)

```
을 해왔건만, 정작 pip에 대해서는 "패키지 관리자야~" 이상의 궁금증을 가져본 적이 없는 것 같다. 그래서 찾아보았다!

##### 1. pip
우선 이 친구는
- [pip on Github](https://github.com/pypa/pip)
- [pip Quickstart](https://pip.pypa.io/en/stable/quickstart/) 
이 문서들을 참고했다.

- python.org에서 다운 받은 Python 2.7.9 또는 Python 3.4 이상 버전에는 ```pip``` 가 이미 설치되어 있답니다.
    - 물론 upgrade 해주어야 할거에요.
- 혹시 ```virtualenv``` 나 ```pyvenv```로 만든 가상환경에서 작업중이라면 마찬가지로 ```pip```가 이미 설치되어 있을 거예요.
- ** 그래서 ```pip```가 뭐냐면, PyPA [tool recommendations](https://packaging.python.org/guides/tool-recommendations/) 이에요. Python package들 설치하는..! **




##### 2. pipenv
그런데 세상에나 ```pipenv```라는것도 있다고 하지 않는가...? 
심지어 **  new recommended Python Packaging tool by Python.org ** 라고 동네방네 적혀있다!


얘는 대체 뭐냐면,,

- 위에 적혀있듯 Python 패키징 툴
- 엄청 간략하게 말하면 ```pip```+```virtualenv```
- ```requirements.txt``` 파일 관리하기 골치가 아프지 않나요? [골치아픈 예시](https://www.kennethreitz.org/essays/a-better-pip-workflow) 라면서,  ```pipenv```는 (basic use cases 에 superior한 ~~적절한 번역 실패~~)```pipfile```과 ```pipfile.lock```  를 쓴다고 말한다.
- 모든 곳에 Hash 를 사용해 보안 취약점들을 보완해준다고 한다.
- ```$pipenv graph``` 하면 dependency graph 에 대한 
- ```.env``` 파일을 로드함으로써 개발 작업 흐름을 원활하게 해준다. ( Streamline development workflow by loading .env files. ) 
    - [Streamline](https://dictionary.cambridge.org/dictionary/english/streamline) 이 무슨 뜻인지 몰라서 찾아봤고 그래서 원문을 남겨뒀다 홍홍.

```
$ pip install pipenv
```
이렇게 깔 수 있다!

참고자료
- [pipenv 공홈](https://docs.pipenv.org/)
- [pipenv on PyPI](https://pypi.python.org/pypi/pipenv)
- [Why pipenv?](https://www.ostechnix.com/pipenv-officially-recommended-python-packaging-tool/)


* * *
이어지는 궁금함은
### PyPI랑 PyPA가 뭔가요...?

~~궁금한게 왜 이렇게 많아~~ ~~검색하다보면 그렇지 뭐~~

좀 쉬었다 쓰기로...


