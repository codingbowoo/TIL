## apache error log

결론부터 말하자면 
```
/var/log/apache2/error.log
```

**500 Internal Server Error**가 뜨면 일단 막막하다. 마치 C 프로그래밍하다가 segmentation error 가 뜨던 것과 느낌이 비슷했다. (물론 segmentation error가 메모리 접근에서 틀려먹어서 나오는 에러임을 알고 나서는 적당히 눈버깅이 가능해졌다..)

Internal Server Error 화면에서 이렇게 말한다. 
"The server encountered an internal error or misconfiguration and was unable to complete your request."

만약 환경설정 중이었다면 높은 확률로 configuration에서 문제가 생겼을 것이라고 생각한다. 나는 venv상태에서 django와 apache 설정 중이었고, 

    - settings.py
    - wsgi.py
    - /etc/apache2/apache2.conf
    - /etc/apache2/sites-enabled/000-default.conf

네 개의 파일을 수정중이었다. 그런데 어디서 틀렸는지 도통 모르겠는데, 접때 나의 환경설정을 도와주던 후배가 apache error log를 찾아보던 기억이 나서 'apache error log location'이라고 구글링해서 알게 된 것이 바로 다음과 같다. 

```
/var/log/apache2/error.log
```

후기: 그래서 에디터에, ```cat /var/log/apache2/error.log``` 해보니 어디서 틀렸는지 찾기가 수월해졌다. 


<br/>

###### 참고 링크들
- (슥 훑어본) MDN [Internal Server Error](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/500)
- [Django 및 WSGI 설정하기](http://tronzebk.tistory.com/5)
