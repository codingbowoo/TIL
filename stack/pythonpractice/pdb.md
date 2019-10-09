# pdb — The Python Debugger

> 2019.10.09의 이야기: 오늘도 열심히 프린트로 디버깅을 하던 나를 보고 친구가 "언니는 디버깅 어떻게 해?" 했다. 
나는 "아이고.. 저는 프린트로 디버깅을 깎습니다.." 했고 그러자 친구는 "pdb 한번 찾아봐" 라고 했다. 그리고 이 문서가 생겼다 짜잔

pdb는 당연하게도 Python DeBugger의 약자이다. 이 말을 글쓴이는 gdb를 떠올렸다... 때는 2014년 대학교 1학년, C프로그래밍 프로젝트...
PuTTY로 학교 서버에 접속해서 주어진 것이라고는 vi editor와 터미널 뿐인 내게 친구가 알려준.. segmentation fault를 잡는(이라 해봐야 무한 run) 방법...
pdb라니 이름만 봐도 알겠네, gdb 비슷한 것 아니겠어? 그래서 gdb가 뭐였는지 먼저 간단히 정리해보기로 했다.


#### [GDB: The GNU Project Debugger](https://www.gnu.org/software/gdb/)

전체 documentation: http://sourceware.org/gdb/current/onlinedocs/gdb/

GDB는 [GNU 프로젝트](https://ko.wikipedia.org/wiki/GNU_%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8) 디버거이다.
GDB를 사용하면 어떤 프로그램이 실행되는 동안 그 내부에서 무슨 일이 일어나고 있는지/ 충돌이 발생했을 때 어떤 일이 일어나고 있었는지 확인할 수 있다. 

버그를 잡기 위해서, GDB가 할 수 있는 것은 크게 4가지 정도로 나눌 수 있다.
  ```
  1. Start your program, specifying anything that might affect its behavior.
  프로그램 동작에 영향을 줄 만한 것은 무엇이든 지정한 채로 프로그램을 시작할 수 있다.
  
  2. Make your program stop on specified conditions.
  특정한 조건에서 프로그램을 중지할 수 있다. 
  
  3. Examine what has happened, when your program has stopped.
  프로그램이 멈췄을 때 무슨 일이 일어나고 있는지 조사할 수 있다. 
  
  4. Change things in your program, so you can experiment with correcting the effects of one bug and go on to learn about another.
  프로그램의 내용을 변경할 수 있다. 한 버그를 고친 것이 다른 버그에 어떤 영향을 미치는지 실험할 수 있다. 
  ```
아무튼 범용 디버거이고, Ada, Assembly, C, C++, D, Fortran, Go, Objective-C, OpenCL, Modula-2, Pascal, Rust 등의 언어를 지원한다. 
(음! python은 없군!)
여담으로 GNU홈페이지에 웃긴거 있다.... [[1]gdb 노래](https://www.gnu.org/music/gdb-song.html) [[2]gnu 깔깔유머집](https://www.gnu.org/fun/humor.html)

#### PDB
```python3
import pdb
```
(간단 설명 및 실 사용 예 추가할 것)


resource

- [Python3 documentatioin pdb](https://docs.python.org/3/library/pdb.html)
- [Integration of IPython pdb](https://github.com/gotcha/ipdb)
