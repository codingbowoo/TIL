# 슬기로운 bashrc 생활

터미널을 쓰다 보면 언젠가는 만나게 되는 ```bashrc``` ! 

**bash** 는 GNU OS의 shell, 혹은 command language interpreter이다. 
자세한 설명은 링크로 대체한다. [GNU bash manual 1.1 What is Bash?](https://www.gnu.org/software/bash/manual/html_node/What-is-Bash_003f.html)

**rc**는 무려 run command의 줄임말이다. 그래서 우리는 ```.vimrc```, ```.zshrc``` 등 많은 rc파일들을 마주한다.

bashrc를 수정하려고 보면 비슷한 이름의 파일들이 많다. 
```.bash_history```, ```.baxh_logout```, ```.bash_profile```, ```.bashrc```...
그 중 헷갈리는 두 개의 차이를 살펴보자면 아래와 같다.

- ```.bashrc``` **for non-login** shell (reload every time I start a new copy of bash)
- ```.bash_profile``` **for login** shell. 보통 PATH와 같은 environment variable을 넣는다.

.bashrc 파일을 수정한 후에는 새로운 bash 창을 열거나, 아래 명령어를 입력해야 수정한 내용을 적용할 수 있다.

```shell
source ~/.bashrc
````

```~/.bash_profile```에는 아래 코드를 추가해주었다. 
```shell
if [ -f $HOME/.bashrc ]; then
        source $HOME/.bashrc
fi
```

## alias
.bashrc 파일을 수정하는 경우 가장 쉽게, 많이 접하는 명령어는 alias일 듯 하다!
```shell
# 기본 용례
alias rm='rm -i'

# 2개 이상의 명령어를 한번에 실행하고 싶을 땐 ;로 구분한다
alias cclear='clear;clear'
```


그 외 다양한 alias를 확인할 수 있는 https://stuff.lhunath.com/.bashrc : [여기](https://stackoverflow.com/questions/902946/about-bash-profile-bashrc-and-where-should-alias-be-written-in) 답변에서 찾았따.

