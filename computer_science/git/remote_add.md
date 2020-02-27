## git remote add

맨날 찾기 귀찮아서 정리하면 외울까 싶어서 정리해본다.

```git init```하고 나면 clone을 해오지 않는 이상 remote repository를 지정해주어야 한다.

그래서 그 command가 뭐냐면

```
git remote add (remote name) (remote URL)
```

이거다. 흑흑 몇 번 더 찾아보겠지만,,
- remote name은 보통 branch를 따온게 아니면 origin을 사용했다.
- remote URL은 그거다. github에서 clone 버튼 누르면 나오는 ```http://github.com/(username)/뫄뫄.git```

그리고 나면 config를 하는데, 이것의 코드는 다음과 같다..
```
$ git config --global user.name "(username)"
$ git config --global user.email example@example.com

```

손이 먼저 움직이는 그날까지!

###### 참고 링크
- [Getting Started - First-Time Git Setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)
