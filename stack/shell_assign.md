## = 와 := 의 차이
[Makefile](https://opensource.com/article/18/8/what-how-makefile) 에 대해 읽다가, 
```CC = gcc``` 라고 variable을 선언했을 때, 후에 스스로를 재할당(reassign)하는 경우 무한루프에 빠진다는 내용이 나왔다.
예를 들어,
```shell
CC = gcc
CC = ${CC}

all:
    @echo ${CC}
```
위와 같은 Makefile을 ```make```하며 다음과 같은 에러메시지를 남긴다.

    Makefile:8: *** Recursive variable 'CC' references itself (eventually).  Stop.
    
그래서 Makefile을 작성할 때 ```=``` 대신 ```:=```연산자(operator)를 사용한다. <br>

**그런데 대체 ```=```와 ```:=```은 무엇이 다른 것인가?**<br>

```:=```은 **simply expanded variable**이라고 부른단다.  (```=```은 recursively expanded variables라고 부른다.) <br>

변수(variable)에 담기는 것은 함수일 수도 있고 다른 변수에 대한 reference일 수도 있다. 

변수에 다른 변수에 대한 reference를 담았을 때 차이가 생긴다. 
```=```으로 할당을 할 경우, 코드를 쭉 따라가다가, 변수 이름이 나오면 그 내용으로 확장(expand)하고, 그제서야 reference를 참조한다.
그러니 ```CC = ${CC}```가 무한루프를 돌 수 밖에....

그런데 이 **simply expanded variable**의 경우는 변수를 선언할 때 reference의 참조값을 담는다. 
따라서 아까 그 코드의 두번째 줄을 ```CC := ${CC}```로 바꾸면 결국 ```CC = gcc```가 되므로 무한루프를 돌지 않는다는 사실.


###### 번외: 변수가 초기화가 되어있지 않을 때만 값을 정하려면 ```=```대신 ```?=```를 사용하면 되고, 이것은 conditional variable assignment operator라고 부른다.


아참, 그래서 아까 그 Makefile은 이렇게 바꿔주면 된다. 
```shell
CC := gcc
CC := ${CC}

all:
    @echo ${CC}
```
### Reference
- [What is a Makefile and how does it work?](https://opensource.com/article/18/8/what-how-makefile)
- [Setting Variables](https://www.gnu.org/software/make/manual/html_node/Setting.html#Setting)
- [The Two Flavors of Variables](https://www.gnu.org/software/make/manual/html_node/Flavors.html)
