# iperf
최근 특정 서버의 카프카 전송 속도가 떨어지는 현상이 있었다.

네트워크 성능테스트를 했다면서 내역을 보내 왔는데 처음 보는 명령어가 있는 것이다! <br>
그래서 찾아본 오늘의 프로그램 `iperf`

메일 내용으로만 봐서는 시간 및 용량 단위로 속도 측정이 가능한 프로그램인 듯 하다. 

## 개요
### iPerf3
공식 홈페이지는 https://software.es.net/iperf/ <br>
깃허브 레포는 https://github.com/esnet/iperf 다. 신기해! 

- iperf를 통해 IP 네트워크의 최대 달성 대역폭을 측정할 수 있다. 
- timing, protocol, buffer 등의 다양한 파라미터를 조절할 수 있고, throughput/bitrate, loss 등을 측정할 수 있다. 
- NLANR/DAST를 재설계한 것이며 iperf3이라고도 불린다. 
  - 엄밀하게는 다른 프로그램에서도 사용할 수 있도록 라이브러리를 완전히 새롭게 구현한거다. 
  - 기존 iperf에는 빠져 있지만 nettcp나 netperf에서 제공하는 다양한 기능(a zero-copy mode and optional JSON output)도 제공한다. 
  - 원본 iperf랑은 호환 불가 
- CentOS Linux, FreeBSD, and macOS 환경에서 개발했으며, 
OpenBSD, NetBSD, Android, Solaris 및 기타 Linux 배포판에서도 작동한다. 
- three-clause BSD 라이선스를 따르며 ESnet / Lawrence Berkeley National Laboratory에서 개발했다. 

### iPerf2
위 내용을 기껏 찾아놓고 우리 서버의 iPerf 버전을 확인해봤더니 글쎄 `iperf version 2.0.13 (21 Jan 2019) pthreads` 랜다 쳇... 
- iPerf2는 https://sourceforge.net/projects/iperf2/ 에서 확인 가능하다. 
- 한마디 설명은 `TCP/UDP의 latency를 포함하는 네트워크 성능 측정 도구`다.
- 기본 동작은 반복적으로 **len** bytes의 array를 **time** seconds만큼 전송하는 것
  - len의 default는 128 KB for TCP, 8 KB for UDP
  - time의 default는 10seconds
- [iPerf user docs](https://iperf.fr/iperf-doc.php) 참고

## 용례
### 버전 확인
```
# iperf -v
iperf version 2.0.13 (21 Jan 2019) pthreads
```
### 기본형
```
iperf -s [ 옵션 ] # 내가 서버다
iperf -c 호스트 [ 옵션 ] # 내가 클라이언트다, 호스트에 연결해줘라!
```

### 시간 단위 속도 측정
- `-t n`,  `--time n` 옵션: 시간 지정(default 10 seconds)
- `-f M`, `--format M` 옵션: bandwidth 보여주는 포맷 설정. M은 Mbytes/sec (default: 'a', adaptive bits/sec)
```
(client에 로그인한 상태)# iperf -c [host ip] -f M -t [숫자(초 단위)]
# iperf -c 10.000.000.000 -f M -t 5
```

### 용량 단위 속도 측정
- `-n n`,  `--num n` 옵션: 일반적으로 iPerf의 동작은 반복적으로 **len** bytes의 array를 **time** seconds만큼 전송하는 것인데,
이 옵션을 주면 time만큼 전송하는 대신 array of len bytes를 num times만큼 전송한다. (The number of buffers to transmit)
- `-f M`, `--format M` 옵션: bandwidth 보여주는 포맷 설정. M은 Mbytes/sec (default: 'a', adaptive bits/sec)
```
(client에 로그인한 상태)$ iperf -c [host ip] -f -M -n [전송 사이즈]
# iperf -c 10.000.000.000 -f -M -n 1500M
```

## 참고(client 모드 관련 옵션들)
```
Client specific:
  -c, --client    <host>   run in client mode, connecting to <host>
  -d, --dualtest           Do a bidirectional test simultaneously
      --ipg                set the the interpacket gap (milliseconds) for packets within an isochronous frame
      --isochronous <frames-per-second>:<mean>,<stddev> send traffic in bursts (frames - emulate video traffic)
  -n, --num       #[kmgKMG]    number of bytes to transmit (instead of -t)
  -r, --tradeoff           Do a bidirectional test individually
  -t, --time      #        time in seconds to transmit for (default 10 secs)
  -B, --bind [<ip> | <ip:port>] bind ip (and optional port) from which to source traffic
  -F, --fileinput <name>   input the data to be transmitted from a file
  -I, --stdin              input the data to be transmitted from stdin
  -L, --listenport #       port to receive bidirectional tests back on
  -P, --parallel  #        number of parallel client threads to run
  -R, --reverse            reverse the test (client receives, server sends)
  -T, --ttl       #        time-to-live, for multicast (default 1)
  -V, --ipv6_domain        Set the domain to IPv6 (send packets over IPv6)
  -X, --peer-detect        perform server version detection and version exchange
  -Z, --linux-congestion <algo>  set TCP congestion control algorithm (Linux only)
```

## 그 외 물음표 
- 근데 카프카는 디폴트 9092 포트 쓰는데 왜 5001(TCP) 포트를 실험하셨지? -> 디폴트 값이 5001이네... 
  - `-p 9092`로 실험해봐야지! 
  - iPerf3은 client-side port 지정하는 `--cport n` 옵션도 있네 

- 엥 나는 왜 iperf 실행이 안되지? 
  - 1. root 계정에서 실행해야 하네  
  - 2. 아니 그래도 안되네... connect failed: Connection refused 
    - 카프카 쪽 5001포트가 닫혀있나보다... 9092포트는 실험 가능(근데 해도 되는건가?)
  - 3. 근데 `write failed: connection reset by peer`가 뜨네 -> 여기부턴 내일 보자! 
