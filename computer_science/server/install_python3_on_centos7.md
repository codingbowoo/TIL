# 서버에 python3 설치하기 

우선 OS를 확인해보자

```
$ cat /etc/system-release
CentOS Linux release 7.x (Core)
```

어디선가 `yum install python3`만 하면 된다고!! 헐!! <br>
...은 내 yum은 python3 중에 3.6.8이 기본이네요... 소스에서 설치해야겠다...! 


## Prerequisites
```
$ sudo yum -y install openssl-devel **bzip2-devel**

$ sudo yum -y update
$ sudo yum -y groupinstall "Development Tools"
$ sudo yum -y install gcc openssl-devel bzip2-devel libffi-devel # 여러 곳에서 공통으로 명시한 패키지
$ sudo yum -y install zlib-devel, xz-devel # 일부 레퍼런스에서 명시한 패키지

$ sudo yum install wget make -y # 없으면 추가적으로 설치해야 하는 것
```
제법 많은 블로그에서 말하는 pre-requisites인데, 저것들이 뭔지 알아야 말이지...
(상용 서비스가 돌아가는 서버라서 마음대로 yum update 해도 되는지도 모르겠다구요 주륵)
- [참고] [\[Linux\] 리눅스 -dev, -devel 패키지란?](https://mentha2.tistory.com/214)


**(풀리지 않은 의문)conda로 설치했을 때는 저 prerequisite들이 어디에 어떻게 깔리는거지?**

확인 결과 서버에 python 3.7이 존재하는건 conda를 설치해서일 공산이 크지만 
찾아본 내용이 아까우니 yum을 이용해서 소스코드로 python3 설치하는 내용은 마저 정리해둔다. 



## 소스코드 다운로드
나는 3.7.6 버전 받을거니까... 
https://www.python.org/downloads/source/ 에서 원하는 버전의 
Gzipped source tarball의 마우스 오른쪽 버튼 누르고 Copy Link Address 해주자
```
$ wget https://www.python.org/ftp/python/3.7.6/Python-3.7.6.tgz
```

## 시스템 준비
```
$ sudo apt-get update
$ sudo apt-get upgrade
```
- 이것도 해도 되냔 말이지! 이미 다운받아둔 것들이 업데이트 되는 건 아니지만... 

다음으로 빌드 requirements 를 확인하는데, 우리는 위에서 이미 확인했으니 pass! 
- 위에 적은 내용은 CentOS 한정(yum으로 패키지 관리하는 경우)이고, apt를 기반으로 하는 경우는 아래 코드 스니펫 참고.
```
# For apt-based systems (like Debian, Ubuntu, and Mint)
$ sudo apt-get install -y make build-essential libssl-dev zlib1g-dev \
       libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm \
       libncurses5-dev libncursesw5-dev xz-utils tk-dev
```

## 파이썬 빌드
```
# 다운받은 파일 압축 해제 및 페이지로 들어가기
$ tar xvf Python-3.7.6.tgz
$ cd Python-3.7.6

$ ./configure --enable-optimizations (--with-ensurepip=install 옵션을 추가한 경우도 있다)
$ make -j 8 # -j 8: compile 빠르게 하기 위해 병렬 빌드를 가능하게 하는 옵션
$ sudo make altinstall

# ln: 리눅스 파일시스템 상에서 링크 파일을 만들어준다. 
$ sudo ln -sfn /usr/local/bin/python3.7 /usr/bin/python3.7
$ sudo ln -sfn /usr/local/bin/pip3.7 /usr/bin/pip3.7
$ rm /usr/src/Python-3.7.6.tgz 

$ python3.7 --version # 최종 버전 확인 
```
make -j 8을 진행하는데, 

## Reference 
- [Python 3 Installation & Setup Guide by Real Python](https://realpython.com/installing-python/#how-to-build-python-from-source-code)
- https://vinodpandey.com/how-to-install-python3-on-centos-7/

## 이모저모
- 각 옵션, pre-requisite 패키지에 대한 내용도 곧 정리해야지! 
