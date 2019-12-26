# NP

```
A decision problem* is in NP if, whenever the answer for a particular instance is 
"yes", there is a simple proof of this fact.
```
\* decision problem : yes-no로 대답할 수 있는 문제

NP문제는 polynomial time 해법을 모르지만 yes instance가 주어질 때 그것이 맞는지는 간단하게(P time에) 확인할 수 있는 문제이다. 

그래서 일반적으로 *Polynomial time 해법이 없다*고 알려져 있지만, 그걸 증명한 사람은 아무도 없다! (엄밀하게는 P time 해법이 있는지 없는지 모른다는 뜻이다.)

## NP의 공식적인 정의

NP is the class of problems A of the folloing form:
```
x is a yes-instance of A if and only if there exists a w such 
that (x, w) is a yes-instance of B,

where B is a decidion problem in P regarding pairs (x, w),
|w|* = poly(|x|), and |.| is the number of bits to represent.
```
\* w : *witness* or the *certificate* of the fact that x is a yes-instance of A.
