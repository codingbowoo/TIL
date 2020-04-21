 # Markdown 수식
 Github markdown 수식 입력하는 방법
 
 - 간단한 수식 (알파벳)은 https://www.htmlhelp.com/reference/html40/entities/symbols.html 에서 찾는다.
 - 복잡한 수식은 https://latex.codecogs.com/eqneditor/editor.php 에 입력하고, 렌더링을 마치면 (시간이 조금 걸린다)
     1. 이미지를 마우스 우클릭, ```이미지 주소 복사```  OR
     2. 다운로드 링크의 우클릭,  ```링크 주소 복사```한 주소 내용 중 download를 latex로 바꿔준다.
     
     그리고 마크다운 문서에 아래처럼 넣는다. 
     
         ![캡션(설명)](복사한 링크 붙여넣기)
         
         # 예시
         ![sum a_i](https://latex.codecogs.com/gif.latex?%5Cinline%20%5CLARGE%20%5Csum%20a_i)
 
     하면 아래처럼 보인다. (안보일 수도 있다... )
     
     ![sum a_i](https://latex.codecogs.com/gif.latex?%5Cinline%20%5CLARGE%20%5Csum%20a_i)
     
- 복잡한 수식의 경우 http://www.sciweavers.org/free-online-latex-equation-editor를 사용해도 된다. 사용 방법은 codecogs와 비슷하다. 
아래처럼 수식을 확인할 수 있다. 

     ![sum a_i](http://www.sciweavers.org/upload/Tex2Img_1587471184/render.png)

 
- sciweavers나 codecogs나 비슷한데, sciweavers가 더 빠르지만 에러가 잦은 듯 하다.
