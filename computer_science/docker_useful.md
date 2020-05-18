나도 이제 도커 사람! 동료들이 도커 이렇게 쓰면 돼! 하고 알려준 명령어들 모아두고 무슨 말인지 알아들어보자..!

- [container 생성](#container)
- [jupyter notebook 만들기](#make-jupyter)
- [실행 중 container에 포트 추가하기](#add-port-to-running-container)
- [포트 포워딩](#port-forward)

## 실행 중 container에 포트 추가하기 <a id="add-port-to-running-container"></a>
1. 실행중인 컨테이너를 종료 
    - ```docker stop (컨테이너 이름)```
2. 현재 상태를 이미지로 만든다/ commit으로 수정사항 반영 
    - ```docker commit (컨테이너 이름) (이미지 이름)```
    - ```docker rm (컨테이너 이름)```
    
3. 해당 이미지 실행 시 포트 추가하기
- [image에 수정사항이 있는 경우](https://medium.com/sjk5766/%EC%8B%A4%ED%96%89%EC%A4%91%EC%9D%B8-container%EC%97%90-port-or-volume-%EC%B6%94%EA%B0%80-ae8889344c68)



## container 생성 <a id="container"></a>
```bash
# version 1
$ nvidia-docker run -ti --rm --ipc=host -p 8888:8888 --name ex -v ~/exDir:/mnt/data example:0.1

# version2
$ docker run -it --name (container 이름) -v (host의 폴더):(container 안에서의 폴더) -p (포트):(포트) (도커 이미지) /bin/bash 

# 정리하자면 
$ docker run [옵션] 이미지[:태그] [커맨드] [인자]
```

## jupyter notebook 만들기 <a id="make-jupyter"></a>
```bash
# version 1
$ jupyter notebook --ip=0.0.0.0 --no-browser --allow-root&

# version 2
$ docker attach (container 이름)
$ nohup jupyter notebook --ip 0.0.0.0 --no-browser --allow-root --port=(포트) & 
```

## 학교 밖에서 쓰고 싶어... 포트 포워딩 <a id="port-forward"></a>
```bash
$ ssh -N -L (로컬에서_실행할_port):(서버_ip):(서버_port) (경유_컴퓨터_ip) 
```
내 경우 서버ip는 fml2, 경유하는 컴퓨터 ip는 fml1 이다. 
