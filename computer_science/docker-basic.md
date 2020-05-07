용어 정리
- docker
- image
- container
- host


이미지 관련 명령어: 목록 확인, 다운로드, 삭제
```
$ docker images
$ docker pull 이미지_이름:버전(태그)
$ docker rmi 이미지_이름
```


컨테이너 실행 / 나가기
```
$ docker run [옵션] 이미지[:태그] [커맨드] [인자]
$ exit
```

컨테이너 목록 확인, 다시 실행, 중지, 삭제
```
$ docker ps -a
$ docker attach 컨테이너_이름_ID
$ docker stop 컨테이너_이름_ID
$ docker rm 컨테이너_이름_ID1 컨테이너_이름_ID2(여러 개 가능)
```

컨테이너 로그 보기/ 실시간 컨테이너 로그 보기
```
$ docker logs --tail 로그_몇_개_볼지 컨테이너_이름_ID
$ docker logs -f 컨테이너_이름_ID
```

실행 중 컨테이너에 명령 실행
```
$ docker exec [옵션] 컨테이너_이름_ID 커맨드 [인자]
```
