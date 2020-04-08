재미있게 읽은 아티클과 한(!)줄 덧글 집합소입니다.

##### Table of Contents  
- [Career](#career)
- [Diversity](#diversity)
- [Finance](#finance)  
- [Portfolio](#portfolio)
- Machine Learning - [basics](#ml-basics) | [examples](#ml-examples) | [tools](#ml-tools)
- [Natural Language Processing](#nlp)
- [Python](#python)
- [Reinforcement Learning](#reinforcement-learning)
- [RNN](#rnn)

* * *
## Career
- [I had no idea how to write code two years ago. Now I’m an AI engineer.](https://towardsdatascience.com/i-had-no-idea-how-to-write-code-two-years-ago-now-im-an-ai-engineer-13c530ab8227) by David Chong
    > If you’re feeling lost, remember what Elsa said and “do the next right thing”.
    
    경제금융을 전공한 David Chong씨가 AI엔지니어가 되기까지의 이야기이다. MOOC으로 수강을 하면 생각보다 섬세하게 배울 수 없다는 것을 깨달았다는 부분이 와닿았고, 스스로 프로젝트를 하고 대학원에 진학하는 등의 과정이 담겨 있다. (do the next right thing은 사실 안나가 부른 노래다)

## Diversity
- [A Nude ‘Playboy’ Photo Has Been a Mainstay in Testing Tech for Decades](https://onezero.medium.com/a-nude-playboy-photo-has-been-a-mainstay-in-testing-tech-for-decades-b8cdb434dce1) by [Corinne Purtill](https://onezero.medium.com/@corinnepurtill)
    - Lena Söderberg씨의 플레이보이 사진이 이미지 프로세싱할 때 많이 쓰이는 것과 관련한 이야기. CODE LIKE A GIRL에서 시작한 [Losing Lena](https://vimeo.com/372265771)영상도 보자. 아티클에서는 해당 이미지에 국한된 이야기가 아닌 업계 전반의 다양성 부재-의도치 않은 배제의 문화를 지적한다. 번역해볼까 싶은 글.  
- [There Is a Racial Divide in Speech-Recognition Systems, Researchers Say](https://www.nytimes.com/2020/03/23/technology/speech-recognition-bias-apple-amazon-google.html?action=click&module=News&pgtype=Homepage) By [Cade Metz](https://www.nytimes.com/by/cade-metz)
    - 새로운 기술이 나왔을 때 편향bias과 차별discrimination에 대해 좀 더 고려할 필요가 있다고 생각하고, 이를 연구하는 사람들이 있다. 안녕 난 인공지능 서비스야! 하고 세상에 나왔는데(많은 이들이 기술은 객관적이라고 생각할 것이다), 사실은 예를 들어 사투리, 여성, 백인이 아닌 다른 인종을 구분하는 등에 있어 정확도가 떨어지는 상황에 대한 연구다. 
    - GAN으로 만든 이미지가 여자는 긴머리에 여리여리한(여리여리하다: 단단하지 못하며 무르고 약하다.) 느낌이고 남자는 선도 굵고 느낌이 확 다르다. 역시 여자남자는 다르게 생긴게 분명하다(...) 라고 말하는 사람을 본 적 있다. 과연 그 GAN의 training data에 안 여리한 여자, 여리한 남자가 있었을까? 학습 데이터는 충분히 diverse한가? 모든 집단을 아우르는가? 애초에 편향된 데이터를 사용한 것은 아닌가? **We Teach A.I. Systems Everything, Including Our Biases**. 반면, 세상에 이미 편향이 존재하는데 기술이 그것을 반영하지 않는 것이 옳은 것인가? 당연히 case by case겠지만, 이야기를 나눠볼 필요가 있다. 

## Finance
- [Python for finance tutorial](https://github.com/datacamp/datacamp-community-tutorials/blob/master/Python%20Finance%20Tutorial%20For%20Beginners/Python%20For%20Finance%20Beginners%20Tutorial.ipynb)
- [Fama-French Research Portfolios and Factors](https://wrds-www.wharton.upenn.edu/pages/support/research-wrds/research-guides/fama-french-research-portfolios-and-factors/#beme-book-to-market)
- [FACTOR ALLOCATION 101: EQUAL VS VOLATILITY-WEIGHTED](https://www.factorresearch.com/research-factor-allocation-101-equal-vs-volatility-weighted)

#### Naver D2 Talk
- 2018.01.16 [금융의 역사를 통해 본 딥러닝의 함정](https://tv.naver.com/v/2557902), 이태영
- 2018.05.21 [초단타매매 전략 소개 및 트렌드](https://tv.naver.com/v/3255292), 권용진
- 2018.07.25 [NFL, DL, and Financial Sector](https://tv.naver.com/v/3679080), 이원종
- 2018.11.21 [금융과 Technology 의 만남 - 로보 어드바이저의 가능성과 한계](https://tv.naver.com/v/4480881), 이주원
- 2019.03.27 [금융과 딥러닝 - 금융 영역에서의 딥러닝은 어떻게 다른가?](https://tv.naver.com/v/5832425), 문효준

## ML-basics
- 수아랩 리서치 블로그 [머신러닝이란 무엇인가?](https://research.sualab.com/introduction/2017/09/04/what-is-machine-learning.html)
- 수아랩 리서치 블로그 딥러닝이란 무엇인가? [(1)](http://research.sualab.com/introduction/2017/10/10/what-is-deep-learning-1.html) [(2)](https://research.sualab.com/introduction/2017/10/10/what-is-deep-learning-2.html)
    - 머신러닝, 딥러닝 개념을 설명하는 글 중 가장 이해하기 쉬웠다.

## ML-examples
- [Profiling my Favourite Songs on Spotify through Clustering](https://towardsdatascience.com/profiling-my-favorite-songs-on-spotify-through-clustering-33fee591783d) by John Koh

## ML-tools
- [Best Python Libraries/Packages for Finance and Financial Data Scientists](https://financetrain.com/best-python-librariespackages-finance-financial-data-scientists/) from FinanceTrain
- Keras
- Pytorch
- Tensorflow
- [Uber ludwig](https://github.com/uber/ludwig)
  - [Introduction to Uber’s Ludwig](https://towardsdatascience.com/introduction-to-ubers-ludwig-cdaa67245cfa) by Gilbert Tanner

## NLP
- [The Illustrated Word2vec](https://jalammar.github.io/illustrated-word2vec/) by Jay Alammar

## Portfolio
- [포트폴리오 이론](https://flyinglightly.tistory.com/category/%EC%9E%AC%EC%A0%95%ED%95%99)
- [Skewness and Kurtosis](https://www.evestment.com/resources/investment-statistics-guide/assessing-skewness-and-kurtosis-in-the-returns-distribution/)
- [Are the Skewness and Kurtosis Useful Statistics?](https://www.spcforexcel.com/knowledge/basic-statistics/are-skewness-and-kurtosis-useful-statistics)
- [Measuring portfolio skewness](https://core.ac.uk/download/pdf/4834498.pdf)

## Python
- [Minimally Sufficient Pandas](https://medium.com/dunder-data/minimally-sufficient-pandas-a8e67f2a2428) <br>
: 여러 topic 중 ```Builtin Python functions vs Pandas methods with the same name```에 문제의식을 가진 것 만으로도 흥미로왔다..


## Reinforcement Learning
- [An intro to Advantage Actor Critic methods: let’s play Sonic the Hedgehog!](https://medium.freecodecamp.org/an-intro-to-advantage-actor-critic-methods-lets-play-sonic-the-hedgehog-86d6240171d) by Thomas Simonini

## RNN
- [Taming LSTMs: Variable-sized mini-batches and why PyTorch is good for your health](https://towardsdatascience.com/taming-lstms-variable-sized-mini-batches-and-why-pytorch-is-good-for-your-health-61d35642972e) by William Falcon
- [Stock Market Prediction by Recurrent Neural Network on LSTM Model](https://blog.usejournal.com/stock-market-prediction-by-recurrent-neural-network-on-lstm-model-56de700bff68) , using Keras by Aniruddha Choudhury
