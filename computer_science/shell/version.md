# version 확인

```shell
$lsb_release -a
```
그러나

> /bin/sh: 1: lsb_release: not found

를 마주하게 되었다. 그렇다면 다른 방법으로...

```shell
$cat /etc/issue
# Out:
# Ubuntu 16.04.3 LTS \n \l
```
