## reinforcement_learning

강화학습과 관련된 간단한 용어 정리 쯤으로 봐두자.

#### 기본 용어   
- Agent & Environment
- Observation, Action, Reward
- Policy, Value function and Model

#### Problems with RL
1. Learning vs. Planning
2. Exploration vs. Exploitation
3. Prediction vs. Control

#### Markov 어쩌구저쩌구
1. Markov Property(Markov Chain)
    - State & State transition probability
2. Markov **Reward** Process
    - Markov Chain + Reward function & discounting factor 
    - Return; Value function (Expectation of the Returns; the env is stochastic)
    - Bellman Equation
        - iterative expectation
3. Markoc **Decision** Process
    - MRP + Action
    - Policy; a mapping from state to action. a distribution over actions given states.
    - Bellman Equation for (1) State Value function (2) Action Value function
        - Bellman **Expectation** Equation
        - Bellman **Optimality** Equation

#### Policy gradient
- [Policy Based Reinforcement Learning, the Easy Way](https://towardsdatascience.com/policy-based-reinforcement-learning-the-easy-way-8de9a3356083) by Ziad SALLOUM
    - [Score function with Softmax policy](https://math.stackexchange.com/questions/2013050/log-of-softmax-function-derivative)

###### 도움이 된 링크
- [Reinforcement Learning: An Introduction 2nd edition](http://incompleteideas.net/book/the-book-2nd.html) : 강화학습 교과서
- [UCL Course on RL](http://www0.cs.ucl.ac.uk/staff/d.silver/web/Teaching.html) by David Silver(Google DeepMind)
- [An intro to Advantage Actor Critic methods: let’s play Sonic the Hedgehog!](https://medium.freecodecamp.org/an-intro-to-advantage-actor-critic-methods-lets-play-sonic-the-hedgehog-86d6240171d)
by Thomas Simonini
