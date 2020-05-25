# Exceptions

- 윈도우에서는 에러가 다르게 난다. 예를 들어, linux 환경에서 
```python3
try:
    pass
except FileExistsError:
    pass
```
이렇게 예외처리할 수 있었던 에러가 

```FileExistsError: [WinError 183] 파일이 이미 있으므로 만들 수 없습니다```
라고 나오면서 예외처리가 되지 않는다...

[python3 documentation exception OSError](https://docs.python.org/3/library/exceptions.html#OSError)를 참고해서 예외처리를 해보자.
