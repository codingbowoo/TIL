# Chapter 1: Computer Architecture Review

## Contents
- [Metrics: 좋은 컴퓨터 아키텍처란?](#metrics)
    - [Performance](#metrics-performance)
    - [Power consumption](#metrics-power-consumption)
- [What to Improve?](#what-to-improve)
    - [Common case](#common-case)
    - [Amdahl's law](#amdahl-s-law)

* * *

## Metrics
컴퓨터가 좋다 나쁘다 판단하는 일반적인 평가 기준, performance와 power consumption <br>
컴퓨터 구조는 크게 3가지 종류로 나뉜다: Desktop(일반), Server(고성능), Embedded(내장;제한적)

### Performance<a id="metrics-performance"></a>
무엇을 세냐면...
- [level 0] number of **operations** (알고리즘 레벨, big-O notation)
    - 그런데, operation마다 걸리는 시간이 다 다를 수도 있잖아.
- [level 1] number of **machine instructions**(CPU가 single cycle에 실행시킬 수 있는 program의 unit) **per operations** (PL, Compiler 레벨)
    - 그런데, 일반적으로는 machine instruction이 single cycle이 걸린다고야 하지만- 사실은 2 cycles가 걸릴 수도 있고 3 cycles가 걸릴 수도 있잖아.
    cache missing이라도 나면 memory IO는 수십~수백 사이클이잖아. 
- **[level 2] 어떤 Instruction이 실제로 얼마나 빨리 수행되는가? (CPU, architecture 레벨)**
- [bonus] I/O device access가 얼마나 빠른가? (운영체제 레벨)

#### CPU Time (= Execution time) 
computation time을 잴 때 가장 많이 사용하는 metric, ```실행 시간```
- 어떤 프로그램을 실행시킬 때 얼마나 많은 clock cycle을 필요로 하는가? (= **CPU Clock Cycles**)
- 한 clock cycle을 실행하는데 얼마나 많은 Wall clock time(the actual amount of time taken to perform a job)이 소모되는가 (= **Clock Cycle Time**)
```
(CPU Time) = (CPU Clock Cycles) * (Clock Cycle Time) 
           = (CPU Clock Cycles) / (Clock Rate)
```
그래서 우리는 
1. CPU Clock Cycle을 줄이거나
2. Clock Rate(CCT의 역수)를 늘리거나 한다.
    - 이 말이 곧 Clock Cycle Time(이하 CCT)를 줄인다는 뜻이다. <br>
    참고로 1GHz CPU의 CCT는 1ns, 3Ghz CPU의 CCT는 0.33ns이다.
    

### Power consumption<a id="metrics-power-consumption"></a>
- list

* * *

## What to improve
어떤 방법으로 성능을 향상시킬 것인가? 
### Common case<a id="common-case"></a>
- list

### Amdahl's law<a id="amdahl-s-law"></a>
- list
