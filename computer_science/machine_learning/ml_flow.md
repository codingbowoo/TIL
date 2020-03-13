# ML-flow

문제를 정의하고, 데이터를 준비하고, 알고리즘을 평가하고 결과를 개선하고 모델을 저장하고 예측을 하고 결과를 저장하고... 하는 과정,
같은 모델을 사용하지만 다른 데이터를 다룰 때 재사용 가능한 코드 만들기.... 이런 일련의, 머신러닝 실험 전체에 걸친 프로세스와 관련한 고민을 정리하는 문서.

미디엄 Towards Data Science에 올라온 아래 글을 처음 접하고 본 이미지에 실소를 터뜨렸다. 내 컴퓨터인가 ^^;<br>
해당 글에서는 GNU make를 사용해 전체 workflow를 관리한다. 적용해보려면 조금 시간을 두고 읽어야겠는걸.

- [Structure and automated workflow for a machine learning project](https://towardsdatascience.com/structure-and-automated-workflow-for-a-machine-learning-project-2fa30d661c1e)
- [Structure and automated workflow for a machine learning project — part 2](https://towardsdatascience.com/structure-and-automated-workflow-for-a-machine-learning-project-part-2-b5b420625102)


그 외에도, 여러 회사들에서도 이런 workflow에 대한 고민을 가지고 있다.
대표적으로 Facebook의 FBLearner Flow - 재사용성과 유연성, 완전한 자동화에 대해 고민한다! 
- [Introducing FBLearner Flow: Facebook’s AI backbone](https://engineering.fb.com/ml-applications/introducing-fblearner-flow-facebook-s-ai-backbone/)
  : 2016년 글


### ML flow를 도와주는 도구들
- [Weights&Biases](https://docs.wandb.com/)
- [Sacred](https://github.com/IDSIA/sacred)
  - 함께 써요 [Omniboard](https://github.com/vivekratnavel/omniboard)
- [Tensorboard in Pytorch](https://pytorch.org/docs/stable/tensorboard.html)
- 시각화 도구 [Visdom](https://github.com/facebookresearch/visdom)
