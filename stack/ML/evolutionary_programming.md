# EP
- Evolutionary Programming [위키피디아](https://en.wikipedia.org/wiki/Evolutionary_programming)<br>
- Genetic Algorithm [지난 TIL: Genetic Algorithm](https://github.com/codingbowoo/codingbowoo-resource/blob/master/stack/ML/genetic_algorithm.md)

유전자 알고리즘을 사용하는 일련의 프로그래밍 기법(?)이다. 다음과 같은 순서로 이루어진다.<br>
출처 : [Genetic Algorithms + Data Structures = Evolution Programs](https://www.springer.com/gp/book/9783540606765)의 한국어판
1. 문제의 해를 위한 유전적 표현을 선택한다(본질적이고 문제의 의미를 잘 반영해야 하는데, 이건 온전히 프로그래머의 몫이다.).
    - *어떤 표현이 적합한지에 대한 가이드라인이나, 이것도 하나의 변수로 넣고 GA를 돌리면 안되나?*
2. 초기 개체individual을 생성한다. 이 때 랜덤하게 생성함을 기본으로 하지만 제약 조건이 있을 시 반영한다. 
이 개체들에 기반한 해집단population이 진화 프로그램Evolutionary Programming의 시작이다.
3. 적합도fitness에 의해 해집단을 평가evaluate하는 평가함수를 선택한다.
4. 유전 연산자(crossover, swap, mutate 등)를 설계한다. 이 역시 프로그래머의 몫이며, 문제의 본질과 구속조건들을 고려해야 한다.
5. 프로그램에 필요한 다양한 매개변수들은 
    1. 프로그래머가 제공(아니! 또 내 몫이잖아!)
    2. 감독 유전자 과정에 의한 통제를 거칠 수 있다.
        - 감독 유전자 과정: 
