# Feature Scaling

머신러닝을 할 때, loss로 주로 MSE(Mean Squared Error)를 사용한다. MSE의 범위가 너무 커지면 학습에 어려움이 생길 것이다.
따라서 범위를 줄이기 위해 feature들을 적절히 scale하여 비슷한 크기를 가지게 해야 한다. 

### Feature Scaling의 여러 방법

대표적인 것 몇 가지만 적는다.

**Standardization**
- mean=0이고 std=1인 분포로 바꿔준다.
- 값들을 Z score로 바꾼다.
- 평균을 기준으로 각 value가 떨어진 정도에 해당한다. 


**Min-Max Scaling**
- 데이터를 [0,1] 범위로 변환하는 것이다. 
- (값-최솟값) / (최댓값-최솟값)
- Standardization과 다른 점: outlier에 영향을 많이 받는다.


**Mean Normalization**
- -1과 1 사이의 값으로 바꿔준다. (mean=0)



### 어떻게 쓰는데요? 

주로 scikit-learn 패키지에서 제공하는 함수들을 사용한다.

```python3
#from sklearn.preprocessing import scale
from sklearn.preprocessing import MinMaxScaler, Standartdcaler

data = []

std_scaler = StandardScaler()
data_scaled = std_scaler.fit_transform(data)

minmax_scaler = MinMaxScaler()
data_scaled = minmax_scaler.fit_transform(data)
```


###### resources
- [Why, How and When to Scale your Features](https://medium.com/greyatom/why-how-and-when-to-scale-your-features-4b30ab09db5e)

###### 이모저모
- 2020.03.17 모델 개선의 여지를 찾다가 Feature Scaling으로 흘러들어왔다. 그리고 갑자기 standardize랑 normalize가 헷갈려서 쓰기 시작한거 맞다 
