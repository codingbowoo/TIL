## sys

[BOJ 그대로 출력하기 2](http://icpc.me/11719)를 몇 날 며칠 고민했는데, 
```sys.stdin.read()```, ```sys.stdin.readline()```, ```sys.stdin.readlines()``` 를 사용하는 것이 손에 익으면서 구글링을 하다가 
어물쩡 해결해버렸다.

처음 짠 코드는 이렇다. (메모리 29160KB, 시간 64MS, 코드 길이 120B)
```
import sys

try:
    a = sys.stdin.readlines()
except EOFError:
    pass

for line in a:
    print(line, end="")
```


그래서 슥슥 try except 구문을 지워보았다. (메모리 29160KB, 시간 **68MS**, 코드 길이 82B)
```
import sys

a = sys.stdin.readlines()

for line in a:
    print(line, end="")
```
try except 구문을 지웠는데 시간이 더 오래 걸렸다.
