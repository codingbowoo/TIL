# hosts
```
sudo vi /etc/hosts
```

오늘의 대화
> 보우씨, 카프카 뭘로 붙어요? ip? 이번에 설정 바뀌면서 ip로 붙는거 안 될 수도 있대요. host 설정 해줘야 할 수도 있어요!

그리고 보우씨는 겁을 먹었습니다. 

## /etc/hosts
알고 보니 ... `sudo vi /etc/hosts` 해서 host로 등록해주면 되는 거였다.<br>
별 거 없고 `IP주소 Hostname Alias(생략가능)`만 적어주면 된다. 설정 후에는 재시작해야한다. 처음 개발환경 세팅할 때 이미 건드렸던 파일이다!

https://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap9sec95.html 에 의하면 

사연인즉슨(?) DNS를 참조하기 전에(name server가 없으면...) IP주소-host이름 매핑을 알아야 하는 경우가 있고 이 매핑을 저장하는 파일이 `/etc/hosts`다. <br>

우리 서버가 Centos니까 레드햇 계열이라... /etc/hosts 파일을 우선 참고해 네임서버를 ip주소로 바꾸는구나. 


위 링크에 뭔가 중요하다고 써있는 부분을 번역하자면 
- telnet이라 ftp 커넥션에 대한 타임아웃(시간초과)는 client IP를 DNS로 resolve하려고 할 때 발생하는데,
- DNS 구성이 제대로 되어있지 않거나/ client machine이 DNS에 등록이 되어있지 않거나가 그 이유이다. 
- DNS lookup이 timeout될 때 까지 기다려야 해서 로그인 프롬프트가 뜨기까지 몇 분을 공으로 날려먹을 수 있다...  
그러니 telnet이나 ftp 서비스를 실행하고 DNS를 쓰지 않을 때는 꼭 /etc/hosts 를 작성하도록 하자. 


## 이모저모
- 그럼 설정이 바뀌면서 네임서버가 날아가나보다... 
