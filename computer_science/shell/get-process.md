# get-process
: 실행 중인 프로세스 목록을 보여준다.
- 별도 매개변수 없이 실행하면 전체 프로세스 목록을 보여준다.
- 실행 시 나오는 항목은 다음과 같다. 
    -  Handles: 프로세스가 연 윈도우 핸들의 수
    - NPM(K): 프로세스가 사용하는 Non-Paged Memory의 크기. 단위는 KB.
    - PM(K): 프로세스가 사용하는 Pageable Memory의 크기. 단위는 KB.
    - WS(K): 프로세스의 Working Set의 크기. 단위는 KB. Working Set은 최근에 참조한 메모리 페이지로 구성된다. 
    - VM(M): 프로세스가 사용하는 Virtual Memory 크기. 단위는 MB. Virtual memory 는 디스크 페이징 파일 저장소를 포함한다.  
    - CPU(s): 모든 프로세서에 대해 프로세스가 사용한 시간. 단위는 초(sec).
    - ID: 프로세스 ID (PID) 
    - ProcessName: 프로세스 이름

- ```get-process [문자열]``` 을 실행하면 해당 문자열을 포함하는 이름의 프로세스만 보여준다.
- ```ps```, ```gps```로도 get-process를 참조할 수 있다.


###### 관련 개념
- **Paging**
: 가상메모리를 최소 단위로 쪼갠 일정한 크기의 블럭을 Page라 한다. Paged Memory는 가상 메모리 공간 중 Page-In/Out이 가능한 공간이고 Non-Paged Memory는 Page 운영체제를 구성하기 위한 코드 등 Paging이 발생하지 않는 공간을 의미한다. 메모리 파편화(fragmentation) 문제를 해결하기 위해 Paging을 사용한다. paging file은 swap file이라고도 부른다. 
(참고: [가상 메모리 (Virtual memory)](http://egloos.zum.com/sweeper/v/2988689))
- **Handle**: 윈도우 커널이 관리하는 리소스들의 토큰. 커널의 오브젝트를 사용하기 위해 필요한 일종의 장치
(참고: [윈도우 핸들이란? 프로세스 Windows Handle 설명](https://codingcoding.tistory.com/201))

###### resource
- [Process Cmdlet으로 프로세스 관리](https://docs.microsoft.com/ko-kr/powershell/scripting/samples/managing-processes-with-process-cmdlets?view=powershell-6#getting-processes-get-process)
- Microsoft Docs [Get-Process](https://docs.microsoft.com/en-us/previous-versions//dd347630(v=technet.10)?redirectedfrom=MSDN)

###### 트리비아 
- 2019/10/05 특정 프로세스의 CPU 사용량이 알고 싶었는데 그 내용이 아니었다,, 
- 2019/10/06 그냥 `작업 관리자`를 확인할 일이었나 싶다 :cry: , <br> 
Linux에서의 관리는 [리눅스(Linux) 프로세스 관리](https://aonenetworks.tistory.com/644), 
리눅스 제타위키[리눅스 메모리 사용량순 프로세스 보기](https://zetawiki.com/wiki/%EB%A6%AC%EB%88%85%EC%8A%A4_%EB%A9%94%EB%AA%A8%EB%A6%AC_%EC%82%AC%EC%9A%A9%EB%9F%89%EC%88%9C_%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4_%EB%B3%B4%EA%B8%B0)
를 참고하자!
