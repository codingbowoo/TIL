## 무슨 일이 있었냐면

프로젝트를 하는데 머신러닝 리더 오빠가 AWS 서버의 Mysql을 연결하려는데 에러메시지가 뜬다고 연락이 왔다.

에러 메시지는 다음과 같다.
```
"Can't connect to MySQL server on '(ip)' ([WinError 10061] 대상 컴퓨터에서 연결을 거부했으므로 연결하지 못했습니다)"
```

원인은 방화벽이 막혀 있었기 때문! 

<br/>



#### 1. AWS inbound rule 추가
> 처음 django 할 때 수도 없이 헤맸던 HTTP 포트 열어주는거랑 같은거 맞다.

- Type에서 MYSQL/Aurora를 골라준다
- Port range의 Default 값인 3306이 뜬다.
- Source를 꼭 설정해주어야 한다. 오늘은 Anywhere로 해버렸다.

#### 2. mysql configuration 파일(/etc/mysql/my.cnf)을 수정했어
``` 
bind-address=0.0.0.0 
```
을 추가.  내 경우에는 /etc/mysql/my.cnf 가 read-only인 바로가기였다. 포인터가 가리키는 파일을 열어 수정했다.

#### 3. 그 다음에 mysql 재시작!
```
sudo systemctl restart mysql.service
```


참고 링크 
- https://help.ubuntu.com/lts/serverguide/mysql.html
- 티스토리 블로그 자바월드 [AWS에 설치된 MySQL DB를 외부 접속이 가능 하도록 설정](http://javaworld.co.kr/69)
