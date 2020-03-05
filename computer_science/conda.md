# conda channel
(2019-09-11) fbprophet package를 update 할 필요가 있어 보여서, 어떤 명령어를 사용해야 하는가에 대한 탐구를 함. 
```shell 
conda update fbprophet
```
하니까 그런 패키지는 없어! 라는 에러를 뱉길래, 다운로드 받을 때 사용한 명령어를 살펴보니 다음과 같았다.
```shell
conda install -c conda-forge fbprophet
```

그런데 **-c**도 **conda-forge**도 당최 뭔지 모르겠는 것이다.. 그래서 아래와 같이 구글링 했다. <br>

```anaconda package upgrade``` --> ```conda install "-c" meaning``` --> [```conda-forge```](https://conda-forge.org/docs/)

- ```-c``` option은 channel의 줄임말이다. default channel은 ~~Anaconda Cloud~~ https://repo.anaconda.com/pkgs/main/win-64 (이곳인듯 하다/내 경우 win-64 platform임)이고, conda-forge는 어떤 channel 이름이다.
- 결론은 fbprophet은 conda-forge 채널에서만 다운받을 수 있는 패키지였다는 말씀이다.


# conda virtual environments
(2019-09-16) 지금까지 jupyter notebook 켤 때 GUI 버튼 눌러서 시작했는데... 무려 그것이 예전에 만들어둔 torchenv 환경이었음을 깨달았다.
결국 fbprophet 사용하는... 새로운 가상환경 만들기로... 매번 찾는 것 같아서 기록해둔다. <br>
- [Managing environments](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)

새로운 환경에 fbprophet을 설치하려고 보니 첫 번째로 해야 할 일은 gcc를 까는 것인듯 했다. 그런데 무려 gcc 패키지가... linux 와 osX 용으로밖에 없는 것이다... 대체 패키지를 찾기 위해선

1. 내 플랫폼을 안다
2. 플랫폼에 맞는 패키지가 있나 https://anaconda.org/ 에서 찾아보고 install!

정도인데, 내 플랫폼을 알려면 ```conda info``` 명령어를 실행해보자. 

### virtualenv 복사하기
같은 스펙의 가상환경을 만들고 싶을 때, 물론 ```pip freeze > requirements.txt```를 사용해 ```pip install -r requirements.txt```
conda에서는 다음 명령어를 사용하면 된다. 
```shell
conda create --name (새로 생성할 가상환경 이름) --clone (원래 가상환경 이름)
```
```conda create```의 옵션으로는 ```--name```외에도
- ```--prefix```, ```--p```: 가상환경의 위치 설정
- ```--no-default-packages``` : 기본 패키지 없이 생성! ... 인데 일반 ```conda create --name (생성할 가상환경 이름)```이랑 다른지 잘 모르겠다.
- ```python=3.6``` 처럼 python 버전을 설정할 수 있다.
- 기타 옵션들은 ```conda create --help``` 를 통해서 확인해보자!

### 프로젝트 관리를 위해 environment.yml로 export! 

```python3
conda env export > environment.yml
```
