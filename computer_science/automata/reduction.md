자동장치이론 공부를 해본 사람이라면 책에서 ```(문제A) <= (문제B)```라는 표현을 본 적 있을 것이다. <br>
저 표현을 읽는 방법은 놀랍게도, **A can be reduced to B** 이다.
* * *
reduction은 computational complexity를 결정할 때 중요한 역할을 한다. <br>
```(문제A) <= (문제B)``` 는 *'A가 최대 B만큼 어렵다*(A의 상한선이 B이다)' 혹은 *'B가 최소 A만큼 쉽다.*(B의 하한선이 A다)' 로 읽어낼 수 있다. 


다시 말해, <br>
B가 P(Polynomial)라면 A도 P이고,  A가 NP라면 B도 NP여야 한다는 말이다. <br>
그런데 **A can be reduced to B**라니, 더 쉬운 것을 어려운 쪽으로 줄인다(reduce)구?
<br><br>
...는, 사실 반대의 의미이다. ```(문제A) <= (문제B)``` 에서 **A는 B의 특수한 경우**라고 볼 수 있다. <br>
문제 B가 더 일반적인 문제이므로 풀기는 어렵다. (수학에서도 일반해를 찾는 것이 더 어렵듯 말이다.)
<br>
다른 말로는 문제 B가 expressive enough 라고 한다. 무엇에 대해? 문제 A의 목표와 제한 조건에 대해! 