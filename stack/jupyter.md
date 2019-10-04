## jupyter notebook

#### IPython?
Ipython이라 함은 이 jupyter notebook을 일컫는다. interactive computing의 I인가보다.


#### Built-in Magic
> /Library/Frameworks/Python.framework/Versions/3.7/lib/python3.7/site-packages/IPython/core/magics/basic.py

언젠가 ```%%capture``` 라는 것을 검색하여 사용할 일이 있었는데, 주피터 노트북에서 사용할 수 있는 특별한 명령어들이다. <br> ```%lsmagic``` 명령어를 통해 사용 가능한 line 및 cell magic 목록을 확인할 수 있다. 머신러닝 공부하는 사람이라면 익숙할 ```%matplotlib inline``` 은 대표적인 line magic의 예.
- ```%run [notebook 파일이름]``` 하면 notebook파일을 실행할 수 있다.


#### Kernel
- jupyter kernel을 가장 간단하게 눈으로 확인해볼 수 있는 명령어는 ```jupyter kernelspec list```이다. <br> 주피터 노트북  Files 탭 화면의 우측 상단에, 새로운 file을 생성할 수 있는 *New ▼* 드롭다운 메뉴 안의 **Notebook:** 선택지가 바로 kernel 선택을 의미함을 확인할 수 있다. 현재로는 **독립적인 개발환경** 쯤으로 이해하고 있다.
- 독립적인 개발환경이라 함은 가상환경의 존재 이유가 아닐까... 역시나 특정 가상환경에서 ipython 사용하는 방법을 찾아보니 [Installing the IPython kernel](https://ipython.readthedocs.io/en/stable/install/kernel_install.html#installing-the-ipython-kernel) 이라는 문서가 있었고, 나는 그 중 [Kernels for different environments](https://ipython.readthedocs.io/en/stable/install/kernel_install.html#kernels-for-different-environments) 항목의 도움을 받았다. <br>
우선 ```ipythonkernel``` 패키지를 설치하고, 원하는 가상환경을 activate 한 상태의 prompt에
    ```shell
    python -m ipykernel install --user --name (내 가상환경 이름) --display-name "(주피터 노트북에서 확인할 이름)" 
    ```
    명령어를 입력해주면 짜잔. 앞서 언급한 *New ▼* 드롭다운 메뉴 안의 **Notebook:** 선택지에서 내 가상환경 kernel을 확인할 수 있다.
    
    
#### Markdown
주피터 노트북 마크다운의 좋은 점은 LaTeX 을 지원한다는 점이다. ([링크](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Working%20With%20Markdown%20Cells.html#LaTeX-equations))
 [MathJax](https://www.mathjax.org/)를 통한 지원이다.
 
 
 #### Useful facts
  - 모듈이나 함수 이름 뒤에 ? 또는 ??를 붙여주면 세부 정보를 확인할 수 있다. ```help(명령어)```와 비슷한데, help의 경우 output이 나온다면 ?들은 별도의 팝업창에 내용을 보여준다. 
      - **?** : Type(ex.module), String form, Docstring, File(경로) 등의 정보를 보여준다.
      - **??** : Source를 보여준다. File위치도 알려줌.

* * *

###### 도움이 된 링크
- [IPython?](https://ipython.org/)
- [jupyter notebook markdown](https://jupyter-notebook.readthedocs.io/en/stable/examples/Notebook/Working%20With%20Markdown%20Cells.html)
- [Built-in magic commands](https://ipython.readthedocs.io/en/stable/interactive/magics.html)

###### 공부하다 새롭게 알게 된 것- 이런저런 링크를 타다가 완전히 새롭게 접한 내용들

###### 충격 잘 모르고 있는 줄도 몰랐던 사실

###### 트리비아
- 2019-01-08 장보우 anaconda 설치하여 jupyter notebook 사용을 시작했다.
- python 3.7을 두려워한 나머지 최신판 anaconda 설치 후 관리자 모드로 conda 프롬프트를 실행,  ```conda install=3.6``` 명령어를 통해 롤백해버렸다.
- built-in-magic command 들에는 ```%```가 붙는데, 에이핑크의 신곡 ```%%``` 가 떠올라서 흡족하다.
- 2019-09-17 2019년이 다 가기 전에 이 문서를 수정하게 됨에 기뻐하다. 이번 기회에 python2 kernel을 없애버렸다.
