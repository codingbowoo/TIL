# genetic algorithm

parameter를 정할 때 genetic algorithm을 사용할 것을 권유 받았다.
그렇지만.. 내가 아는 것은 이름 뿐.... **[Genetic Algorithm Essentials](https://link.springer.com/book/10.1007%2F978-3-319-52156-5) 를 읽으며 정리해보려 한다.** ( 빠르게 내용을 훑고 싶은 사람은 무려 1997년도에 쓰인(...) 
[최적화기법으로서의 유전알고리즘과 그 응용](http://www.ndsl.kr/ndsl/commons/util/ndslOriginalView.do?dbt=JAKO&cn=JAKO199711919927852&oCn=JAKO199711919927852&pageCode=PG11&journal=NJOU00290606)이라는 한국어 논문이 있으니 가볍게 읽어보면 좋다 )

## Part I Foundations
#### 1 Introduction
> Q. 근데 genetic algorithm 왜 쓰는 거예요? <br>
A. 최적화 문제Optimization 풀려구요!

- 유전 알고리즘은 heuristic의 대표적인 예다. 외판원 문제traveling salesman problem와 같은 P-time 해법이 없는 문제의 경우 [heuristic](https://github.com/codingbowoo/codingbowoo-resource/blob/master/stack/heuristic.md)을 통해 최적을 찾는다. (기존 최적화 방법들이 제약 조건이나 가변성, 노이즈 등으로 인해 효과가 떨어질 때 사용한다)
- 유전 알고리즘은 아래 진행을 반복한다.<br>
**```초기화initialization```-```교차crossover```-```변이mutation```-```적합성 판단fitness```-```선택selection```-```종료termination```**
- 교차와 변이에 관련된 다양한 변주가 있다.
- 유전 알고리즘과 비슷한 heuristic의 예로는 swarm intelligence(explorative),  ant colony optimization(exploitation), fireworks algorithms(balanced), firefly algorithm 등이 있다. 
- keywords: ```genetic algorithms```, ```selection```, ```mutation rates```, ```multi-objective```, ```fitness-based partitions```, ```multimodal```, ```evolution strategies```, ```1/5th success rule```, ```recombination```, ```mutation```, ```constraint handling```

#### 2 Genetic Algorithms 
> KEYWORDS> populations, the generational scheme, crossover, mutation, selection, genotype-phenotype mapping, termination conditions

- 유전 알고리즘은 넓은 범주의 최적화 문제에 적용 가능하다. 이 때, 가장 핵심이 되는 것은 **진화evolution**(점진적 발전)이다.
- 고전적인 유전 알고리즘에서 그 해solution는 최적화 문제의 '최적', 이 때의 초기 해 집합이 population이다.
    - 유전 알고리즘에서는 해를 encode하는데, 이 encode 한 것을 표현representation이라고 부른다. (혹은 유전형genotype, 염색체chromosome이라고도 한다.)
    - 표현은 이산적일 경우 string, 연속적인 경우 vector라고 부른다.
- 기본이 되는 유전 알고리즘의 구조는 아래와 같다.
    ```pseudocode
    initialize population : 초기화 할 때는 전체 해 공간solution space을 아우르는 것이 좋다. 
    repeat
        repeat
            crossover
            mutation
            phenotype mapping
            fitness computtion
        until population complete
        selection of parental population
    until termination condition
    ```
- **교차crossover**는 부모 유전자를 쪼개서 맞교환 하는 방식이다. vector인 경우 부모의 중간값을 취하는 arithmetic crossover(intermediate)를 사용하기도 한다.
    - 그 외에도 Dominant crossover, Uniform crossover등 여러 방식이 있지만 많은 유전 알고리즘이 단순히 부모로부터 일정한 확률로 유전자를 가지고 온다.
- 한편 임의로 변화를 주는 **변이mutation**라고 한다. 일정한 확률mutation rate에 따라 교란disturbance을 일으킨다.
- 변이 연산자mutation operator를 정하는 데는 세 가지 원칙이 있다. reachability, unbiasedness, scalability가 그것이다.
    - ```도달 가능성reachability```: 변이를 줄 때도 전체 해 공간을 아울러야 한다.
    - ```비편향성unbiasedness```: 편향을 지양하되, 제약조건이 있을 경우 bias를 두는 것이 효과적일 수 있다.
    - ```확장성scalability```: 각 변이 연산자는 degree of freedom을 보장해야 한다. 일례로 Gaussian mutation은 Gaussian 분포를 기반으로 전체 해공간에서 임의의 표본을 뽑는다.

2.5 Genotype-Phenotype Mapping 
2.6 Fitness 
**2.7 Selection**

2.8 Termination 
2.9 Experiments 
2.10 Summary 

#### 3 Parameters
> KEYWORDS> tuning and control of genetic algorithms parameters, dynamic control, Rechenberg's mutation rate control, self-adaptation

3.1 Introduction 
3.2 Parameter Tuning 
3.3 Meta-Genetic Algorithm 
3.4 Deterministic Control 
3.5 Rechenberg
3.6 Self-adaptation 
3.7 Summary 

## Part II Solution Spaces
#### 4 Multimodality 
> KEYWORDS> overcoming local optima, restarts, niching, fitness sharing, novelty search

4.1 Introduction 
4.2 Restarts
4.3 Fitness Sharing 
4.4 Novelty Search 
4.5 Niching
4.6 Summary 

#### 5 Constraints
> KEYWORDS> constaint handling, penalty functions

5.1 Introduction 
5.2 Constraints 
5.3 Death Penalty 
5.4 Penalty Functions 
5.5 Repair
5.6 Decoders
5.7 Premature Stagnation 
5.8 Summary 

#### 6 Multiple Objectives 
> KEYWORDS> multi-objective optimization approaches, non-dominating sorting, rake selection, selection based on the hypervolume indicator

6.1 Introduction 
6.2 Multi-objective Optimization 
6.3 Non-dominated Sorting
6.4 Crowding Distance 
6.5 Rakes 
6.6 Hypervolume Indicator 
6.7 Summary 

## Part III Advanced Concepts
#### 7 Theory 
> KEYWORDS> theoretical research, runtime analysis

7.1 Introduction 
7.2 Runtime Analysis 
7.3 Markov Chains
7.4 Progress Rates 
7.5 No Free Lunch 
7.6 Schema Theorem 
7.7 Building Block Hypothesis
7.8 Summary 

#### 8 Machine Learning 
> KEYWORDS> machine learning, covariance matrix estimation, meta-modeling, visualization

8.1 Introduction 
8.2 Covariance Matrix Estimation
8.3 Fitness Surrogates
8.4 Constraint Surrogates 
8.5 Dimensionality Reduction for Visualization 
8.6 Summary 

#### 9 Applications
9.1 Introduction 
9.2 Unsupervised Regression 
9.3 Balancing Ensembles 
9.4 Feature Tuning 
9.5 Wind Turbine Placement 
9.6 Virtual Power Plants
9.7 Summary 

## Part IV Ending
#### 10 Summary and Outlook 
10.1 Summary 
10.2 Outlook
