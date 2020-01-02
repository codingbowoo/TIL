# genetic algorithm

parameter를 정할 때 genetic algorithm을 사용할 것을 권유 받았다.
그렇지만.. 내가 아는 것은 이름 뿐.... [Genetic Algorithm Essentials](https://link.springer.com/book/10.1007%2F978-3-319-52156-5) 를 읽으며 정리해보려 한다.

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

2.1 Introduction 
2.2 Basic Genetic Algorithm
2.3 Crossover
2.4 Mutation
2.5 Genotype-Phenotype Mapping 
2.6 Fitness 
2.7 Selection
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
