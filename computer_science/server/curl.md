## curl

##### 어쩌다 검색하게 되었나
연구실 macbook에 pip를 설치하고 싶은데, 패키지 매니저의 도움을 받기 위해 homebrew를 설치했다.
그런데 애석하게도 뭐가 잘 풀리지 않아서 [pip installing 문서](https://pip.readthedocs.io/en/stable/installing/)의 도움을 받고자 했다...
<br> 요 튜토리얼의 첫 단계는 바로 ```To install pip, securely download get-pip.py``` , 
귀찮음을 이기지 못하고 모든 것을 명령어로 해결할거야!! 라며 구글링을 시작했고, 언젠가 복사 붙여넣기 해넣었던 명령어 curl을 떠올렸다.
 
##### 그래서 찾아본 문서 
[Downloading files with curl](http://www.compciv.org/recipes/cli/downloading-with-curl/)

##### 어떻게 했나
검색해 보고서도 우선 무턱대고 
```
curl (link)
```
를 했다. 하라는 다운로드는 안되고 화면에 ```cat (filename)```한 마냥 get-pip.py의 내용이 주르륵 떴다. 아, 이거 아니구나. 그래서 이렇게 했다.
```
curl (link) --output (filename)
```
--output 옵션을 주고 저장하고 싶은 filename을 적어 넣었다! 만세! 다운로드 완료! 오늘 아침의 작은 발견 :)
