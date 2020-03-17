# Support Vector Regression


일단 regression은 output space가 continuous한 것을 일컫는다(classification은 discrete output space를 가진다).
linear regression은 output을 input의 선형함수로 표현하는 것을 말한다.

또하나 익숙할만한 것이 Support Vector Machine(이하SVM)인데, linear classifier의 일종이다. 
무슨 말이냐면, linear하게 구분지을 수 있는 데이터가 있을 때 decision boundary를 정하고 margin(구분지은 데이터 군과 decision boundary가 떨어져 있는 정도)을 최대화 하는 방법이라는 것!


[Kernel](https://github.com/codingbowoo/codingbowoo-resource/blob/master/computer_science/machine_learning/kernel.md) 문서에 간단히 정리했던 바 있다.


SVR은 임의의 실수값을 예측할 수 있도록 SVM의 회귀 모형에 epsilon-insensitive loss function을 도입해 회귀문제를 해결할 수 있도록 한다.
input이 고차원의 feature space에 map, output value와 연관 선형함수 찾는다.
아래 논문을 확인해보자.

- Parsons, Simon. "Introduction to Machine Learning by Ethem Alpaydin, MIT Press, 0-262-01211-1, 400 pp., $50.00/£ 32.95." The Knowledge Engineering Review 20, no. 4 (2005): 432-433.


    > 으악
    


SVM에는 몇가지 매개변수가 있는데, 선형 SVM의 C, RBF 커널 SVM의 C와 gamma가 그것이다.
- linear SVM의 겨우 데이터를 완벽한 선형으로 분리하는 것은 불가능하다 --> 일부 데이터 샘플이 다른 클래스에 있어도 허용하자! (이상치 허용 정도) : **cost C**
    - 너무 작은 C(많이 놓쳐도 괜찮아) : underfitting 가능성
    - 너무 큰 C(large C 놓치기만 해봐!) : overfitting 가능성
    
- RBF 커널 SVM의 경우 gamma : 하나의 데이터 샘플이 영향을 미치는 거리 (결정 경계의 곡률)
    - 가우시안 표준편차와 관련: gamma가 크면 작은 표준편차를 가진다 --> 데이터 포인터들이 영향 미치는 거리가 짧아진다.
    - gamma가 작으면 underfitting, 너무 크면 overfitting 위험 있다.


## 구현
scikit-learn 패키지에 SVR로 구현되어있다.
SVR에서 가장 중요한 파라미터는 커널함수로, Linear, Polynomial, Gaussian RBF를 모두 적용할 수 있다.
세 종류를 모두 적용해보고 그 중 가장 우수한 성과를 보이는 모형을 최종 선택해도 되겠다.


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

X, y = (SVR의 경우 training data X, y를 필요로 한다. 각자의 data 가공에 맞게...)

# Fit regression model
svr_lin = SVR(kernel='linear', C=100, gamma='auto')
svr_lin.fit(X,y)

y_pred = regressor.predict(y_input)
```

이 때, 결과가 잘 나오지 않는다면 Feature들을 Scaling 할 필요가 있을 가능성이 있다. ```sklearn```의 Scaler 중 하나를 선택하자. 여기서는 StandardScaler를 사용한다.
```python3
from sklearn.preprocessing import StandardScaler

"""
TODO: 
여기에서 X, y를 가공한다.
"""

scaler_X = StandardScaler()
scaler_Y = StandardScaler()

X = scaler_X.fit_transform(X)
y = scaler_Y.fit_transform(y)

"""
TODO: 
여기에 SVR 코드를 적용한다.
"""

y_pred = scaler_y.inverse_transform (\
                                     (svr_lin.predict( scaler_X.transform(y_input) ))
                                    )
```



#### 참고
- Flach, Peter. Machine learning: the art and science of algorithms that make sense of data. Cambridge University Press, 2012.
- Parsons, Simon. "Introduction to Machine Learning by Ethem Alpaydin, MIT Press, 0-262-01211-1, 400 pp., $50.00/£ 32.95." The Knowledge Engineering Review 20, no. 4 (2005): 432-433.
- Goodfellow, Ian, Yoshua Bengio, and Aaron Courville. Deep learning. MIT press, 2016.
- [서포트 벡터 머신(SVM)의 사용자로서 꼭 알아야할 것들 - 매개변수 C와 gamma](https://bskyvision.com/163)
- [Support Vector Regression in 6 Steps with Python](https://medium.com/pursuitnotes/support-vector-regression-in-6-steps-with-python-c4569acd062d)

###### 넋두리
아아.. 나는 인공지능 1학년 아니고 인공지능 한 살쯤 되는 것 같다...
