# Install nvidia driver in Ubuntu
세상에.. 연구실 서버 중 하나에 nvidia driver조차 깔려있지 않음을 발견해버렸다. 어디 한 번 설치해볼까! 

#### 0. 우분투 버전 확인부터 한다.
```
$ lsb_release -a

# Out:
# No LSB modules are available.
# Distributor ID: Ubuntu
# Description:    Ubuntu 18.04.2 LTS
# Release:        18.04
# Codename:       bionic
```

또는

```
$ cat /etc/issue

# Out:
# Ubuntu 18.04.2 LTS \n \l
```

#### 1. nvidia driver가 깔려있나 확인 해보자.
```
$nvidia-smi

# Out:
# Command 'nvidia-smi' not found, but can be installed with:
#
# sudo apt install nvidia-340
# sudo apt install nvidia-utils-390
```

#### 2. 없다! 그렇다면 그래픽카드가 PCI bus에 연결되어 있는지 확인하자.
```
$ lspci | grep -i nvidia

# Out:
# 01:00.0 VGA compatible controller: NVIDIA Corporation GP102 [GeForce GTX 1080 Ti] (rev a1)
# 01:00.1 Audio device: NVIDIA Corporation GP102 HDMI Audio Controller (rev a1)
```
밑에 뭐라뭐라 나오면 연결 상태 걱정은 안해도 된다.

#### 3. 내 컴퓨터에 맞는 nvidia driver 버전을 확인한다.
- [NVIDIA Driver Downloads](https://www.nvidia.com/Download/index.aspx?lang=en-us) 에서 확인하자! 내 경우는 다음과 같다.
```
LINUX X64 (AMD64/EM64T) DISPLAY DRIVER
 
Version:	440.82
Release Date:	2020.4.7
Operating System:	Linux 64-bit
Language:	English (US)
File Size:	136.25 MB
```
 
#### 4. 내 컴퓨터에 깔려 있는 NVIDIA driver가 있는지 확인한다.
```
$ dpkg -l | grep -E “nvidia-[0-9]{3}"

# Out:
```
이번엔 없었지만, 만약 뭔가 있을 경우 ```sudo apt-get purge nvidia-*``` 명령어로 정리해준다. 


#### 5. 좋다! 이제 Nvidia graphic card PPA를 추가해주자. 
```
$ sudo add-apt-repository ppa:graphics-drivers/ppa
```
sudo password 입력 및 continue를 위한 Enter를 해줘야 한다.

#### 6. install 준비
```
$ sudo apt-get update

$ sudo apt-get install screen
$ screen
```
**screen**은 설치 과정이 network fluctuation에 의해 중간에 끊기지 않나(그럼 ssh가 끊기니까) 확인하는 과정이다. ```screen``` command를 통해 login한다.


#### 7. 드라이버 설치
```
$ sudo apt install nvidia-440
$ sudo apt install nvidia-driver-440
```
드디어! 드라이버를 설치한다. 마지막 숫자는 앞서 확인한 버전과 같다. 
위의 명령이 말을 듣지 않는다면(```Unable to locate nvidia-440```) 아래 명령으로 해보자. 그래도 안되면 구글에 물어보자!

#### 8. secure boot이 disable상태인지 확인하고, system reboot! 
```
$ mokutil --sb-state

# Out:
# SecureBoot disabled
# Platform is in Setup Mode

$ sudo reboot
```
확인해보니 secureboot이 disabled이므로, system을 reboot한다. 



#### 9. 껐다 켰다면 잘 다운로드 받았는지 확인해보자
```
$ nvidia-smi

# Out:
# Wed May  6 16:58:52 2020
# +-----------------------------------------------------------------------------+
# | NVIDIA-SMI 440.82       Driver Version: 440.82       CUDA Version: 10.2     |
# |-------------------------------+----------------------+----------------------+
# | GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
# | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
# |===============================+======================+======================|
# |   0  GeForce GTX 108...  Off  | 00000000:01:00.0 Off |                  N/A |
# |  0%   32C    P8    11W / 275W |     40MiB / 11176MiB |      0%      Default |
# +-------------------------------+----------------------+----------------------+
# 
# +-----------------------------------------------------------------------------+
# | Processes:                                                       GPU Memory |
# |  GPU       PID   Type   Process name                             Usage      |
# |=============================================================================|
# |    0      1960      G   /usr/lib/xorg/Xorg                            30MiB |
# |    0      2490      G   /usr/bin/gnome-shell                           7MiB |
# +-----------------------------------------------------------------------------+
```
잘 나온다.. 기뻐.. 짜릿해.. 

10. Bonus: additional help
```
$ dpkg -L nvidia-driver-440

# Out:
# /.
# /usr
# /usr/share
# /usr/share/doc
# /usr/share/doc/nvidia-driver-440
# /usr/share/doc/nvidia-driver-440/LICENSE.gz
# /usr/share/doc/nvidia-driver-440/NVIDIA_Changelog.gz
# /usr/share/doc/nvidia-driver-440/README.txt.gz
# ...
# /usr/share/doc/nvidia-driver-440/nvidia-resume.service
# /usr/share/doc/nvidia-driver-440/nvidia-sleep.sh
# /usr/share/doc/nvidia-driver-440/nvidia-suspend.service
```


###### resources
- [How to Properly Install NVIDIA Graphics Driver on Ubuntu 16.04](https://tech.amikelive.com/node-731/how-to-properly-install-nvidia-graphics-driver-on-ubuntu-16-04/)
- [How to install NVIDIA drivers on Ubuntu 18.04 LTS Bionic Beaver Linux](https://www.mvps.net/docs/install-nvidia-drivers-ubuntu-18-04-lts-bionic-beaver-linux/)
