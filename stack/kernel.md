## Kernel

> 머신러닝 공부를 하다 보면 필연적으로 kernel이라는 단어를 마주치게 된다. 
아마 SVM(support Vector Machine)에 대한 고찰을 하다 마주칠 가능성이 높고, 
언젠가는 Gaussian Kernel, RBF(Radial Basis Function) Kernel 따위를 마주쳤을지도 모르겠다. 
나 역시 Kernel의 마수에서 자유롭지 못했고, 이 토막글은 무려 작년부터 제대로 알지 못하면서 넘어가곤 했던 ```**kernel이란 무엇인가**``` ~~[추석이란 무엇인가](http://news.khan.co.kr/kh_news/khan_art_view.html?art_id=201809211922005)~~ 숙원사업의 해결 과정이다.

<br>

#### Kernel에 대한 일반적인 사실 
1. ```kernel method```라 함은 패턴 분석에 쓰이는 알고리즘의 집합이다.
    1. 각 알고리즘의 이름은 각각의 알고리즘이 사용하는 kernel function의 이름에 따라 달라진다.
    2. ```kernel method``` 의 예: kernel perceptron, SVM(support vector machine), Gaussian processes, PCA(Principal Components analysis) 등
2. ```kernel trick```이라 함은 원본 데이터를 다른 차원의 데이터로 변환하는 것인데, 이 때 다른 차원의 데이터에는 클래스 간의 명백한 구분이 존재한다.
    1. 이 때 explicit mapping을 피하는 것이 핵심인 듯 하다. 이 말을 떠올리게 된다. "Machine Learning is the field of study that gives computers the ability to learn without being explicitly programmed" (Arthur Samuel, 1959)
    2. ```kernel trick```을 다른 말로 설명하자면 비선형 문제를 선형 분류자를 통해 풀어내는 것이다.
3. 수학에서 쓰이는 ```kernel``` 이라는 말은 weighted sum 혹은 적분을 할 때의 weighting function을 칭한다. 


#### 수학적인(?) 

<br>

###### 도움을 받은 곳들  
- Wikipedia [Kernel Method](https://en.wikipedia.org/wiki/Kernel_method)
- dataFlair [Kernel Functions-Introduction to SVM Kernel & Examples](https://data-flair.training/blogs/svm-kernel-functions/)
- Medium Post [Kernel Functions](https://towardsdatascience.com/kernel-function-6f1d2be6091)
- [What are kernels in machine learning and SVM and why do we need them?](https://www.quora.com/What-are-kernels-in-machine-learning-and-SVM-and-why-do-we-need-them/answer/Lili-Jiang?srid=oOgT)
- Caltech on Youtube [Lecture 14 - Support Vector Machines](https://youtu.be/eHsErlPJWUU)
- Caltech on Youtube [Lecture 15 - Kernel Methods](https://youtu.be/XUj5JbQihlU)
- 책 (Adaptive Computation and Machine Learning series) Ethem Alpaydin-Introduction to Machine Learning-The MIT Press (2009)  
