## Covariance matrix

**공분산** 이라는 이름으로 익숙한 covariance <br>

variance 개념만으로는 한 축의 데이터 (2차원으로 예를 들면 x축과 y축 각각)가 흩뿌려져 있는 모양새만 설명할 수 있어서, <br>
서로 다른 변수들 사이의 관계(correlation)를 설명하기 위해 공분산이라는 개념을 도입한다. <br><br>
기존에 알고있던 variance가 퍼짐의 정도(spread)라면, covariance는 방향(orientation)을 나타낸다고 볼 수 있겠다.<br>
이 두가지를 묶어서 확인할 수 있는 것이 covariance matrix이다. (2변량 이상일 때 사용하고, diagonal line이 variance와 같다.)<br><br>


아래는 공분산 행렬에 관련된 이모저모이다.

* (x와 y의 관계) == (y와 x의 관계) 이므로, 공분산 행렬은 언제나 symmetric하다.
* covariance matrix는 eigenvector와 eigenvalue로 표현 가능하다. (eigenv와의 관계를 좀 더 직관적으로 이해하고 싶다...)
* white data는 unit covariance matrix를 가진다. (white data라 함은 unscaled(1) 이고 unrotated인 data를 뜻한다.)
* 엄청난 사실인데, observed data의 covariance matrix는 white, uncorrelated data의 선형 변환 행렬과 엄청난 연관이 있다. (도움이 된 링크 \[1] 의 후반부 예시가 이를 잘 설명해주고 있다.)
   
<br>
<br>

###### 도움이 된 링크
\[1] [A geometric interpretation of the covariance matrix](http://www.visiondummy.com/2014/04/geometric-interpretation-covariance-matrix/)<br>
\[2] [Eigenvectors, Eigenvalues, PCA, Covariance and Entropy 中 Covariance](https://skymind.ai/wiki/eigenvector#covariance)<br>
\[3] [공돌이의 수학정리노트 - 주성분분석 (PCA)](https://wikidocs.net/7646)<br>


###### 공부하다 새롭게 알게 된 것: 이런저런 링크를 타다가 완전히 새롭게 접한 내용들
- [Hermitian Matrix](https://en.wikipedia.org/wiki/Hermitian_matrix)
- [Rayleigh Quotient](https://en.wikipedia.org/wiki/Rayleigh_quotient)

###### 충격 잘 모르고 있는 줄도 몰랐던 사실 
-  "quadratic form" 은 모든 항의 차수가 2인 다항식이었다...

###### 더 공부해야 할 것
- SVD(Singular Value Decomposition, 특이값 분해)
