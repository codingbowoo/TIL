# random

reproducible 한 모델을 만들기 위해 신경써야할 random seed들이 많다.


1. sklearn.model_selection.train_test_split
    - random_state option
2. keras random seed
    - global random seed
    - operation-level seed
3. numpy random seed, random random seed
    - numpy.random.seed(), random.seed()


random의 구동 방식(?)을 정리하고 싶었는데! 
