# How to speed up my project

## pandas DataFrame
1. 단순 반복문 + loc, iloc으로 접근하면 매우 느리다.
2. ```iterrows()``` 메소드를 사용하면 조금 낫다.
    - 누군가는 ```itertuples()```메소드를 사용하는 것이 더 빠르다고 한다. ```iterrows()```의 경우 pandas Series를 return하기 때문에 상대적으로 속도가 느리단다.
3. pandas단에서의 vectorize를 하면 더 빠르다
4. numpy단에서의 vectorize를 하는 것이 가장 빠르다

## 각종 packages
- Pandarallel https://github.com/nalepae/pandarallel
    - [Pandarallel — A simple and efficient tool to parallelize your pandas computation on all your CPUs](https://towardsdatascience.com/pandaral-lel-a-simple-and-efficient-tool-to-parallelize-your-pandas-operations-on-all-your-cpus-bb5ff2a409ae) by Manu NALEPA    
- Numba http://numba.pydata.org/
    - numpy array로만 사용가능 (pandas DataFrame 안됨)
- Multiprocessing https://docs.python.org/3.7/library/multiprocessing.html
- https://github.com/PuneetGrov3r/MediumPosts/tree/master/SpeedUpYourAlgorithms

