# 키워드 추출 
가장 간단한 방식의 키워드 추출은 전처리 -> 형태소 분석 -> 빈도 분석의 3단계로 나뉜다. 
- 키워드 추출은 NLP Task라고 하기도 조금 애매한 면이 있는 것 같다. 키워드를 뽑는 것 그 자체보다는 그 이후의 활용이 중요한 느낌... summarization이라든지... 
- 2021년에는 key-phrase의 추출을 연구한 논문들이 좀 있다. 
  - ELSKE: Efficient Large-Scale Keyphrase Extraction
  - Phraseformer: Multimodal Key-phrase Extraction using Transformer and Graph Embedding

## 전처리
- 특수문자
- 대소문자 통합
- 띄어쓰기 및 맞춤법
- 불용어 제거
- 정규화: ㅋㅋㅋㅋㅋㅋ -> ㅋㅋ 등으로 정리하는 것
- 한국어에는 해당 없는: 빈도가 적은 단어, 짧은 길이의 단어 제거


## 형태소 분석
- KoNLPy와 Mecab을 사용
- [사용자 정의 사전도 추가](https://bitbucket.org/eunjeon/mecab-ko-dic/src/df15a487444d88565ea18f8250330276497cc9b9/final/user-dic/README.md)해준다. 
- 불용어 처리가 번거로워서 N으로 시작하는 품사(체언)를 다 살렸다. 
  - NNG: 일반 명사, NNP:고유 명사, NNB:의존 명사, NR:수사, NP:대명사
  -  [품사태그표](https://docs.google.com/spreadsheet/ccc?key=0ApcJghR6UMXxdEdURGY2YzIwb3dSZ290RFpSaUkzZ0E&usp=sharing#gid=4)


## 빈도 분석 
- 대표적인 방식: TF-IDF
- 골머리 앓는 중...


## 그 외 
- Task로써의 Keyword Extraction이 궁금하면 [Keyword Extraction: papaerswithcode](https://paperswithcode.com/task/keyword-extraction)를 참고할 수 있다. 
Phraseformer 라는 Phraseformer: Multimodal Key-phrase Extraction using Transformer and Graph Embedding
