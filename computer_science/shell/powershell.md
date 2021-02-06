# Windows Powershell

##### Contents
- [Powershell에서 zip파일 관리하기](#unzip-powershell)

* * *
#### Powershell에서 zip파일 관리하기 <a id="unzip-powershell"></a>
- 출처 [How to Zip (and Unzip) Files Using PowerShell](https://www.howtogeek.com/670314/how-to-zip-and-unzip-files-using-powershell/)

- 사건 경위

Windows+conda 환경에서 jupyter notebook을 실행시켜 놓은 코딩보우는 서버에 올린 zip파일을 unzip 하고 싶다! <br>
어찌저찌 ```conda install -c conda-forge unzip``` 했으나 사용 방법을 알 길이 없었는데...<br>
찬찬히 현재 상황을 살펴 봅시다.
1. jupyter 기본 화면에서 우측 상단의 ```new```를 누르고 ```Other:``` 아래의 **Terminal**을 눌러 터미널 하나를 열었습니다.
2. 앗! 리눅스 커맨드라인이 아니군요! 그럼 뭔가요?
```
Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.
```
그렇습니다. 파워쉘이었던 것입니다.<br>
그럼 검색해야죠! 뭐라고? **How to unzip Powershell**이라고! 

- 핵심만 추려볼까요?

**Powershell에서 zip하기**
```
Compress-Archive -LiteralPath zip할파일들경로 -DestinationPath zip결과파일경로
```

**Powershell에서 unzip하기**
```
Expand-Archive -LiteralPath zip파일경로 -DestinationPath unzip할경로
```
