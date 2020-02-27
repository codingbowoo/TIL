## linear regression

#### 간단한 용어 정리
- intercept : linear regression에 사용할 상수 부분을 의미한다.


#### 용례
```python3
frames= [df_monthly.iloc[:, 0:5], df_monthly.iloc[:, 5+1]]
X = pd.concat(frames, axis=1) # dataframe of X
y = df_monthly.iloc[:, 5+2] # series of dependent variable
X = sm.add_constant(X)

# Note the difference in argument order
model = sm.OLS(y, X)
results = model.fit()

# Print out the statistics
results.summary()
```

#### various linear regression packages
- Wolfram [Linear Regression Package](https://reference.wolfram.com/language/LinearRegression/tutorial/LinearRegression.html)
- R [Multiple (Linear) Regression](https://www.statmethods.net/stats/regression.html)
- Python [sklearn.linear_model.LinearRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)
    - [Linear Regression Example](https://scikit-learn.org/stable/auto_examples/linear_model/plot_ols.html)
- [statsmodels.regression.linear_model.OLS](https://www.statsmodels.org/dev/generated/statsmodels.regression.linear_model.OLS.html)
