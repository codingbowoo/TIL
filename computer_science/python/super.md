## super()

2019/01/17 의 기록 <br>
파이썬으로 코드를 짜면서 이런저런 의문이 들기 시작했다. 어제는 self란 무엇인가에 대한 짧은 탐구를 했고, 
오늘은 super()에 대한 탐구이다. 부모자식 Class 간의 상속과 관련이 있다는 점 이상으로 아는 것이 없는 상황.<br>


###### 도움이 된 링크


(video) [Raymond Hettinger - Super considered super! - PyCon 2015](https://www.youtube.com/watch?v=EiOglTERPEo)
>"Then why are you here?"
> 1. Inheritance is for code reuse
> 2. The problem is The diamond diagram(non-trivial multiple inheritance)- need linearization algorithm
> 3. Inheritance == calling your parents(usually), but not in Python(This is the problem I guess.). It calls not MY ancestors but your CHILDREN(youngest in the tree)'s ancestors.(?!) 
<br>

> inheritance injection
<br>


그래서 읽은 글 두 편<br>
[Python's Super is nifty, but you can't use it (Previously: Python's Super Considered Harmful)](https://fuhm.net/super-harmful/)

> One big problem with 'super' is that it sounds like it will cause the superclass's copy of the method to be called. This is simply not the case, it causes the next method in the MRO to be called.

[Python’s super() considered super!](https://rhettinger.wordpress.com/2011/05/26/super-considered-super/)<br><br>

미리 알고있다면 좋을 것이고 아니더라도 자연스레 찾아보게 될 내용 <br>
- [C3 linearization](https://en.wikipedia.org/wiki/C3_linearization)
- [Multiple inheritance](https://en.wikipedia.org/wiki/Multiple_inheritance)
    - [The diamond problem](https://en.wikipedia.org/wiki/Multiple_inheritance#The_diamond_problem)
<br>
그리고 
<br>
[The Python 2.3 Method Resolution Order](https://www.python.org/download/releases/2.3/mro/#id1)<br>
