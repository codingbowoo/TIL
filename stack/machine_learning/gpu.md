# gpu


## monitoring gpu 
리눅스에서 아래 command를 사용할 수 있다.
```shell
nvidia-smi
```
smi는 사실 NVIDIA System Management Interface의 줄임말이다. 실행하면 다음과 같은 화면을 볼 수 있다.

    +-----------------------------------------------------------------------------+
    | NVIDIA-SMI 411.31                 Driver Version: 411.31                    |
    |-------------------------------+----------------------+----------------------+
    | GPU  Name            TCC/WDDM | Bus-Id        Disp.A | Volatile Uncorr. ECC |
    | Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
    |===============================+======================+======================|
    |   0  GeForce GTX 1070   WDDM  | 00000000:01:00.0  On |                  N/A |
    |  0%   63C    P2    63W / 151W |   5448MiB /  8192MiB |     67%      Default |
    +-------------------------------+----------------------+----------------------+

    +-----------------------------------------------------------------------------+
    | Processes:                                                       GPU Memory |
    |  GPU       PID   Type   Process name                             Usage      |
    |=============================================================================|
    |    0      1148    C+G   Insufficient Permissions                   N/A      |
    |    0      7344    C+G   C:\Windows\explorer.exe                    N/A      |
    |    0      7836    C+G   ...osoft.LockApp_cw5n1h2txyewy\LockApp.exe N/A      |
    |    0      8284    C+G   ...5n1h2txyewy\StartMenuExperienceHost.exe N/A      |
    |    0      9128    C+G   ...hell.Experiences.TextInput.InputApp.exe N/A      |
    |    0      9720    C+G   ...10711.0_x64__8wekyb3d8bbwe\Video.UI.exe N/A      |
    |    0      9944    C+G   ...dows.Cortana_cw5n1h2txyewy\SearchUI.exe N/A      |
    |    0     12636    C+G   ...54.85.0_x64__kzf8qxf38zg5c\SkypeApp.exe N/A      |
    |    0     12716    C+G   ....469.0_x64__8wekyb3d8bbwe\YourPhone.exe N/A      |
    |    0     13740    C+G   ...t_cw5n1h2txyewy\ShellExperienceHost.exe N/A      |
    |    0     49220    C+G   ....15002.0_x64__8wekyb3d8bbwe\GameBar.exe N/A      |
    |    0    117452      C   C:\ProgramData\Anaconda3\python.exe        N/A      |
    |    0    121720      C   C:\ProgramData\Anaconda3\python.exe        N/A      |
    |    0    137392      C   C:\ProgramData\Anaconda3\python.exe        N/A      |
    |    0    154064    C+G   ...6)\Google\Chrome\Application\chrome.exe N/A      |
    |    0    159840    C+G   ...oftEdge_8wekyb3d8bbwe\MicrosoftEdge.exe N/A      |
    +-----------------------------------------------------------------------------+

근데! 나의 개발환경은 윈도우란 말이다! 윈도우 prompt에서는 아무리 ```nvidia-smi```를 입력해도 <br>
``` 'nvidia-smi'은(는) 내부 또는 외부 명령, 실행할 수 있는 프로그램, 또는 배치 파일이 아닙니다. ``` 를 마주할 것이다.<br>

그러면 어떻게 해야 하냐구?
C:\Program Files\NVIDIA Corporation\NVSMI 경로에 들어가서 ```nvidia-smi.exe``` 하면 된다.

```shell
> cd C:\Program Files\NVIDIA Corporation\NVSMI
C:\Program Files\NVIDIA Corporation\NVSMI> nvidia-smi.exe
```

또, 10초마다 새로운 화면 보여주고 싶으면 아래 명령을 실행한다. 
```shell
nvidia-smi.exe -l 10
```
l은 loop의 줄임말이고, 10 대신 *초 단위의 원하는 간격*을 넣어주면 자동으로 반복한다. <br>
다른 옵션들도 많은데, 
자세한 설명은 [nvidia-smi documentation](http://developer.download.nvidia.com/compute/DCGM/docs/nvidia-smi-367.38.pdf)를 참고. <br>
