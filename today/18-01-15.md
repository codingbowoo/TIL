## linux 서버 시간 바꾸기

##### 방법 1

```tzselect``` 라는 명령어가 있다. 터미널 창에 

```
$ tzselect
```
라고 하면 지역을 고른다. 한국 기준 4) Asia --> 23) Korea(South)를 골라주면 된다. Local time 확인창이 나오는데 above information OK? ```Yes``` 해주자. 다 숫자 눌러야 한다!
- 요 커맨드는 사실 ```/usr/bin/tzselect``` 라고 한다. 


##### 방법 2

```
TZ='Asia/Seoul'; export TZ
```
를 ```.profile``` 파일에 추가하면 영구적으로 설정을 변경할 수 있다고 한다.
- 변경한 후에는 로그아웃하고 로그인 다시 해주어야 한다! 
