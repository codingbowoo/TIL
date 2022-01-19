# IPython: Jupyter notebook
[IPython](https://ipython.org/)이라 함은 이 jupyter notebook을 일컫는다. interactive computing의 I인가보다.

##### Contents
- [Built-in Magic](#magic)
- [Config 찾기](#config-path)
- [HTML 추출 시 코드 숨기기](#no-code-html)
- [InteractiveShell](#interactiveshell)
- [Kernel](#kernel)
- [Keyboard Shortcuts](#shortcut)
- [Markdown](#markdown)
- [Markdown 표 정렬](#markdown-table-align)
- [두 개 이상의 Out\[\]:을 원해](#interactiveshell)
- [이모저모](#useful)

* * *
#### HTML 추출 시 코드 숨기기 <a id="no-code-html"></a>
아래 내용을 추가하면 Out[#]: 를 여러 개 확인할 수 있다. 
html 파일 생성 시 code를 삭제하려면 (고객 공유용이라든지)...
1. terminal 열기
2. `jupyter_contrib_nbextensions` 깔려있는 kernel 활성화(conda activate 가상환경이름)
3. `jupyter nbconvert 노트북파일명.ipynb --to=html --no-input`
    - 여기서 --no-input 옵션이 코드를 숨기는 부분! print 결과나 Out[]: 결과만 남는다.
    - `--to=html` 옵션의 경우 `--to=pdf` 등으로 변경할 수 있다. 

* * *
#### InteractiveShell <a id="interactiveshell"></a>
아래 내용을 추가하면 Out[#]: 를 여러 개 확인할 수 있다. 

```python3
from IPython.core.interactiveshell import InteractiveShell
InteractiveShell.ast_node_interactivity = "all"
```


* * *
#### Keyboard Shortcuts <a id="shortcut"></a>
1. 내장 shortcut 확인: **Help** 탭의 **Keyboard Shortcuts**<br>
예) run current cell (```Shift```+```Enter```)<br>

2. [Keyboard Shortcut customization](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Custom%20Keyboard%20Shortcuts.html#Keyboard-Shortcut-Customization)
: **Help** 탭의 **Edit Keyboard Shortcuts**<br>
새로운 단축키를 등록할 수 있다. 등록하는 방법은 Edit Keyboard Shortcuts 화면의 하단에 있다.<br>
개인적으로 등록하고 쓰는 것들은 아래와 같다.
    - ```9```,```9``` : restart kernel and run all cells 
    - ```9```,```8``` : restart kernel and clear output 


* * *
#### Config 찾기 <a id="config-path"></a>
```shell
$ jupyter --paths

config:
    C:\Users\jangbowoo\.jupyter
    C:\ProgramData\Anaconda3\etc\jupyter
    C:\ProgramData\jupyter
data:
    C:\Users\jangbowoo\AppData\Roaming\jupyter
    C:\ProgramData\Anaconda3\share\jupyter
    C:\ProgramData\jupyter
runtime:
    C:\Users\jangbowoo\AppData\Roaming\jupyter\runtime
```
```shell
$ jupyter --config-dir

C:\Users\jangbowoo\.jupyter
```
related to
- [Jupyter Documentation Configuration files](https://jupyter.readthedocs.io/en/latest/projects/jupyter-directories.html#configuration-files)

* * *
#### Built-in Magic <a id="magic"></a>

언젠가 ```%%capture``` 라는 것을 검색하여 사용할 일이 있었는데, 주피터 노트북에서 사용할 수 있는 특별한 명령어들이다. <br> ```%lsmagic``` 명령어를 통해 사용 가능한 line 및 cell magic 목록을 확인할 수 있다. 머신러닝 공부하는 사람이라면 익숙할 ```%matplotlib inline``` 은 대표적인 line magic의 예.
- ```%run [notebook 파일이름]``` 하면 notebook파일을 실행할 수 있다.

related to 
- /Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/site-packages/IPython/core/magics/basic.py
- [Built-in magic commands](https://ipython.readthedocs.io/en/stable/interactive/magics.html)

* * *
#### Kernel<a id="kernel"></a>
- jupyter kernel을 가장 간단하게 눈으로 확인해볼 수 있는 명령어는 ```jupyter kernelspec list```이다. <br> 주피터 노트북  Files 탭 화면의 우측 상단에, 새로운 file을 생성할 수 있는 *New ▼* 드롭다운 메뉴 안의 **Notebook:** 선택지가 바로 kernel 선택을 의미함을 확인할 수 있다. 현재로는 **독립적인 개발환경** 쯤으로 이해하고 있다.
- 독립적인 개발환경이라 함은 가상환경의 존재 이유가 아닐까... 역시나 특정 가상환경에서 ipython 사용하는 방법을 찾아보니 [Installing the IPython kernel](https://ipython.readthedocs.io/en/stable/install/kernel_install.html#installing-the-ipython-kernel) 이라는 문서가 있었고, 나는 그 중 [Kernels for different environments](https://ipython.readthedocs.io/en/stable/install/kernel_install.html#kernels-for-different-environments) 항목의 도움을 받았다. <br>
우선 ```ipykernel``` 패키지를 설치(`conda install ipykernel`)하고, 원하는 가상환경을 activate 한 상태의 prompt에
    ```shell
    ipython kernel install --user --name (내 가상환경 이름) --display-name "(주피터 노트북에서 확인할 이름)" 
    ```
    명령어를 입력해주면 짜잔. 앞서 언급한 *New ▼* 드롭다운 메뉴 안의 **Notebook:** 선택지에서 내 가상환경 kernel을 확인할 수 있다.
- prompt에  ```jupyter kernelspec remove (없애고 싶은 커널 이름)``` 또는 ```jupyter kernelspec uninstall (없애고 싶은 커널 이름)``` 명령어를 사용해서 kernel을 없앨 수도 있다. 
- 위 내용이 통하지 않을 때 직접 만드는 방법은 https://yahwang.github.io/posts/42 를 참고하자
    
* * *
#### Markdown<a id="markdown"></a>
주피터 노트북 마크다운의 좋은 점은 LaTeX 을 지원한다는 점이다. ([링크](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Working%20With%20Markdown%20Cells.html#LaTeX-equations))
 [MathJax](https://www.mathjax.org/)를 통한 지원이다.
 
related to
- [jupyter notebook markdown](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Working%20With%20Markdown%20Cells.html)
 
* * *
#### Markdown 표 정렬<a id="markdown-table-align"></a>
- 셀 안의 텍스트 정렬 말고, 표 전체를 정렬하고 싶을 때는 div elements와 inline HTML을 활용해 버리는 수도 있다. 
- 주피터 파이썬 코드 셀에 아래와 같이 입력해주고
```python
from IPython.display import HTML

style="""
<style>
.tbalign table {
  width:75%; 
  margin-left:0%;
  margin-right:25%;
}
</style>
"""

HTML(style)
```

- 마크댜운 셀에 div element를 쓰면 완성! 
```markdown
<div class="tbalign">
    
|ID|이름|
|:------:|:-----:|
|1|어쩌구|
|2|저쩌구|
</div>
```

- [Set table column width via Markdown](https://stackoverflow.com/questions/36121672/set-table-column-width-via-markdown/51701842)

* * * 

#### 이모저모 <a id="useful"></a>
  - 모듈이나 함수 이름 뒤에 ? 또는 ??를 붙여주면 세부 정보를 확인할 수 있다. ```help(명령어)```와 비슷한데, help의 경우 output이 나온다면 ?들은 별도의 팝업창에 내용을 보여준다. 
      - **?** : Type(ex.module), String form, Docstring, File(경로) 등의 정보를 보여준다.
      - **??** : Source를 보여준다. File위치도 알려줌.
* * *


###### 트리비아
- 2019-01-08 장보우 anaconda 설치하여 jupyter notebook 사용을 시작했다.
- python 3.7을 두려워한 나머지 최신판 anaconda 설치 후 관리자 모드로 conda 프롬프트를 실행,  ```conda install=3.6``` 명령어를 통해 롤백해버렸다.
- built-in-magic command 들에는 ```%```가 붙는데, 에이핑크의 신곡 ```%%``` 가 떠올라서 흡족하다.
- 2019-09-17 2019년이 다 가기 전에 이 문서를 수정하게 됨에 기뻐하다. 이번 기회에 python2 kernel을 없애버렸다.
