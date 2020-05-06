나도 이제 도커 사람! 동료들이 도커 이렇게 쓰면 돼! 하고 알려준 명령어들 모아두고 무슨 말인지 알아들어보자..!

- [container 생성](#container)
- [jupyter notebook 만들기](#make-jupyter)
- [포트 포워딩](#port-forward)

## container 생성 <a id="container"></a>
```bash
# version 1
$ nvidia-docker run -ti --rm --ipc=host -p 8888:8888 --name ex -v ~/exDir:/mnt/data example:0.1

# version2
$ docker run -it --name (container 이름) -v (host의 폴더):(container 안에서의 폴더) -p (포트):(포트) (도커 이미지) /bin/bash 

```

## jupyter notebook 만들기 <a id="make-jupyter"></a>
```bash
# version 1
$ jupyter notebook --ip=0.0.0.0 --no-browser --allow-root&

# version 2
$ docker attach (container 이름)
$ nohup jupyter notebook --ip 0.0.0.0 --no-browser --allow-root --port=(포트) & 
```

## 포트 포워딩 <a id="port-forward"></a>
```bash
$ ssh -N -L 8888:163.239.25.120:8181 (내 컴퓨터 아이피) 
$ (Local port):(server ip):(server port) (중간 server)

```
