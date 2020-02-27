# rm
> 랩몬스터 아니고 linux command "rm" 맞습니다. 

#### 오늘의 검색어
```restore file after rm * ``` 

(보기만 해도 안타깝다...)

```rm (파일이름)``` 명령어는 파일에 해당하는 데이터와 파일 이름 사이의 연결을 끊고, 해당 메모리 공간을 쓰기 작업에서 사용 가능한 것으로 표시한다.
따라서 **```rm``` 하자마자**는, 엄밀하게 말하면, 데이터는 살아 있지만 더이상 파일 이름으로 해당 메모리에 접근할 수 없는 것이다. 
```rm``` 자체를 되돌릴 수는 없다! [Linux rm command](https://www.computerhope.com/unix/urm.htm)를 참고하자.

혹시 ext3 또는 ext4 파티션에 위치한 파일을 삭제했다면 아래 링크와 유틸리티들을 확인해보자.
- [Can files/directories deleted with rm be restored?](https://askubuntu.com/questions/6698/can-files-directories-deleted-with-rm-be-restored)
- [extundelete](http://extundelete.sourceforge.net/)
- [TestDisk](https://www.cgsecurity.org/wiki/TestDisk)

메모리에 내용이 덧씌워지지 않았다면, 내용검색을 통해 되살릴 수도 있겠다.
- [Recovering accidentally deleted files](https://unix.stackexchange.com/questions/2677/recovering-accidentally-deleted-files)
- [The Perl Script That May Save Your Life](https://etherealbits.com/2012/06/the-perl-script-that-may-save-your-life/)

그러나... 높은 확률로 복구가 불가능하므로...

    1. 심호흡을 하고
    2. 괜찮다고 스스로를 달래 진정시키고
    3. 새롭게 코드를 짜는 것이 가장 빠른 복구 방법이다.

#### 소 잃기 전에...
1.  ```rm``` 명령어는 

    - ```rm -i``` : *정말 지우시겠습니까?* 확인창이 한번 더 뜸
    -  ```mv (휴지통경로)``` : 영영 삭제하지 않고 옮겨두기

    에 alias 해두자..!
2. 백업, version control을 일상화 합니다.
