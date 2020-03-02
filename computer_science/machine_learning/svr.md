# Support Vector Regression


일단 regression은 output space가 continuous한 것을 일컫는다(classification은 discrete output space를 가진다).
linear regression은 output을 input의 선형함수로 표현하는 것을 말한다.

또하나 익숙할만한 것이 Support Vector Machine(이하SVM)인데, linear classifier의 일종이다. 
무슨 말이냐면, linear하게 구분지을 수 있는 데이터가 있을 때 decision boundary를 정하고 margin을 최대화 하는 방법이라는 것!


[Kernel](https://github.com/codingbowoo/codingbowoo-resource/blob/master/computer_science/machine_learning/kernel.md) 문서에 간단히 정리했던 바 있다.


SVR은 임의의 실수값을 예측할 수 있도록 SVM의 회귀 모형에 epsilon-insensitive loss function을 도입해 회귀문제를 해결할 수 있도록 한다
input이 고차원의 feature space에 map, output value와 연관 선형함수 찾는다.
아래 논문을 확인해보자.

- Parsons, Simon. "Introduction to Machine Learning by Ethem Alpaydin, MIT Press, 0-262-01211-1, 400 pp., $50.00/£ 32.95." The Knowledge Engineering Review 20, no. 4 (2005): 432-433.


    > 으악
    




## 구현
scikit-learn 패키지에 SVR로 구현되어있다.
SVR의 커널함수로 Linear, Polynomial, Gaussian RBF를 모두 적용할 수 있다.
보통 세 종류를 모두 적용해보고 그 중 가장 우수한 성과를 보이는 모형을 최종 선택한다. 


```python3
from sklearn.svm import SVR

"""
# To ignore SVR warning
import warnings
warnings.filterwarnings('ignore', 'Solver terminated early*')

# Often-used parameter values
std = [1, 25, 50, 75, 100]
C = [1, 10, 33, 55, 78, 100]
eps = [0.05, 0.1, 0.5]
"""

# Fit regression model
svr_lin = SVR(kernel='linear', C=100, gamma='auto')
```

#### 참고
- Flach, Peter. Machine learning: the art and science of algorithms that make sense of data. Cambridge University Press, 2012.
- Parsons, Simon. "Introduction to Machine Learning by Ethem Alpaydin, MIT Press, 0-262-01211-1, 400 pp., $50.00/£ 32.95." The Knowledge Engineering Review 20, no. 4 (2005): 432-433.
- Goodfellow, Ian, Yoshua Bengio, and Aaron Courville. Deep learning. MIT press, 2016.
- [서포트 벡터 머신(SVM)의 사용자로서 꼭 알아야할 것들 - 매개변수 C와 gamma](https://bskyvision.com/163)
