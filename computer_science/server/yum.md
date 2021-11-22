# Package Management YUM

## Yum 이 뭐냐면 
Yellow dog Updater여서 원래 YU 였는데 Modified가 붙어서 YUM 인가보다.

CentOS의 기본 패키지 매니저다. 
- Yum Home page : http://yum.baseurl.org/ 

## 기본 사용 
```
$ yum -h  # 도움말 
$ yum list installed # yum 으로 다운받은 패키지 목록 보기
$ yum search 패키지이름
```

## 왜 찾아봤쟈면
centos에 python 설치할 건데... 설치 전에 yum update 하라구요...
```
$ sudo yum -y update
$ sudo yum -y groupinstall "Development Tools"
$ sudo yum -y install wget make gcc openssl-devel bzip2-devel libffi-devel
```
상용 서비스가 돌아가는 서버라서 yum update 해도 되는지도 모르겠다구요(주륵)


그래서 일단 미리 해봤는데요... 
```
$ sudo yum update
[sudo] password for 사용자:
Failed to set locale, defaulting to C
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
Resolving Dependencies
--> Running transaction check
---> Package 패키지명 구버전정보 will be updated
---> Package 패키지명 신버전정보 will be an update

--> Finished Dependency Resolution

Dependencies Resolved

================================================================================================================================================================
 Package                                          Arch                      Version                                            Repository                  Size
================================================================================================================================================================
Installing:
 패키지명                                           arch 버전(e.g.x86_64)       버전 정보                                           updates                     사이즈
Updating:
 패키지명                                           arch 버전(e.g.x86_64)       버전 정보                                           base/updates 등              사이즈
(중략)
Transaction Summary
================================================================================================================================================================
Install    1 Package
Upgrade  139 Packages
```
- 네. 지금은 아닌 것 같아요. 죄송합니다. ㅠㅠ 


## 혹시 yum update 등을 했는데 롤백해야한다면... ?
- `yum history` `yum history rollback 숫자(transaction ID)` 해주면 된다고 한다
    - http://yum.baseurl.org/wiki/YumHistory.html 
    - http://nojinho.blogspot.com/2012/11/yum-history.html 참고
    - CentOS 5 이상, 패키지 따라 의존성 문제로 롤백 안되는 경우도 많고



## 이모저모 
- `yum list installed | grep python` 및 그 pre-requisites 를 확인하고 없는 것만 yum으로 설치해봐야겠다. 
