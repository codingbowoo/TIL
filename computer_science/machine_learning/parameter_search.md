# Hyperparameter Tuning / Neural Architecture Search
간단 정리 & 자료 모음


#### 사전지식 반영 X
- grid search
    - scikit-learn GridSearchCV 
- random search
    - scikit-learn RandomizedSearchCV
    
#### 사전지식 반영 O
- Bayesian Optimization
    - 현재까지의 입력값-함숫값 바탕으로 미지의 목적 함수의 형태에 대한 확률적 추정을 수행하는 **surrogate model** (주로 gaussian process 사용)
    - 목적 함수에 대한 현재까지의 확률 추정 결과를 바탕으로 최적 입력 x\*를 찾는데 유용할 만한 다음 입력값 x_(t+1)을 추천하는 **acquisition function** (keyword: exploitation & exploration, Expected Improvement)
    - 정리하자면 surrogate model 확률 추정 결과 바탕으로 acquisition function 최대로 하는 x_(t+1) 추천, x_(t+1)에 대한 objective function값 계산, 기존 입력값-함숫값 set에 추가한 수 surrogate model로 돌아간다. 이후 반복.
    
    - 수아랩 리서치 블로그 [Bayesian Optimization 개요: 딥러닝 모델의 효과적인 hyperparameter 탐색 방법론 (1)](https://research.sualab.com/introduction/practice/2019/02/19/bayesian-optimization-overview-1.html)
    - MLconf [Let’s Talk Bayesian Optimization](https://mlconf.com/blog/lets-talk-bayesian-optimization/) by Meghana Ravikumar
    - bayes_opt https://github.com/fmfn/BayesianOptimization
        - https://gist.github.com/mohit-sinha/be3f2999eb21d1992d03b7590fe2d88b
        - 다시 수아랩 리서치 블로그 [Bayesian Optimization 개요: 딥러닝 모델의 효과적인 hyperparameter 탐색 방법론 (2)](http://research.sualab.com/introduction/practice/2019/04/01/bayesian-optimization-overview-2.html)
        
- 한 단계 더: paper [BOHB: Robust and Efficient Hyperparameter Optimization at Scale](http://proceedings.mlr.press/v80/falkner18a/falkner18a.pdf)
        
#### evolutionary algorithms for NAS
- paper [Large-Scale Evolution of Image Classifiers](https://arxiv.org/abs/1703.01041)
- paper [Regularized Evolution for Image Classifier Architecture Search](https://arxiv.org/abs/1802.01548)
- Google AI Blog [Using Evolutionary AutoML to Discover Neural Network Architectures](https://ai.googleblog.com/2018/03/using-evolutionary-automl-to-discover.html)
- paper [Towards Automated Deep Learning: Efficient Joint Neural Architecture and Hyperparameter Search](https://arxiv.org/abs/1807.06906)


#### ML optimization을 돕는 패키지들 
- hyperopt https://github.com/hyperopt/hyperopt
- studioml http://docs.studio.ml/en/latest/hyperparams.html
- tune https://ray.readthedocs.io/en/latest/tune.html
- DEAP 
