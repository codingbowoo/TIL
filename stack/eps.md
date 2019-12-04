> 파일 이름이 ```eps.md```인게 마음에 든다.

### eps란?
- 프린터 출력을 제어하는 스크립트인 PostScript에서 파생
- 벡터 이미지에 해당


### plt.savefig() 를 사용해 eps 저장하기

```python3
#plt.subplots_adjust(left=0.3, right=0.9, bottom=0.3, top=0.9)
#plt.tight_layout()
plt.savefig('./epsname.eps', format='eps', bbox_inches = 'tight', pad_inches=0, dpi=2000)
```

- ```plt.tight_layout()```의 경우 ```ax = fig.add_axes()```로 생성한 ax와는 호환이 되지 않는다.
- ```bbox_inches='tight'```option을 주면 한 페이지에 모두 들어가도록 내용물을 자동 조정한다. 
(정확히는 모든 내용물을 포함하는 박스를 찾아 맞춘다.)
- ```pad_inches=0```는 말 그대로 주변 패딩의 정도이다.


### 사실 이런 문제일 수도 있다.
- Windows 운영체제에서는 eps 파일을 볼 수 없다...그래서 [eps viewer](https://epsviewer.org)를 사용하고 있는데, 
제대로 생성한 eps 파일이더라도 뷰어에서 잘려보일 수 있다... 따라서 Windows에서 작업 중 파일이 이상하다 싶으면 
  1. mac OS에서 열어본다
  2. (나의 경우에는 latex) eps를 적용할 응용프로그램에 넣어서 확인해보자.
