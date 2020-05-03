파이토치 검색 가이드가 있었으면 좋겠다 <br>
도큐먼트에서 찾기도 쉽지 않고.. 
(구글링 너무 힘듦)

# Pytorch
- 여러 언어로 만들어진 라이브러리. 사용자는 Python의 쉬운 UI와 C++의 빠른 속도 모두를 향유할 수 있다.
    - python API를 호출하면 C++이나 CUDA로 구현된 코드가 돌아갈 것! 
    - 비율은 C++ 51.7%	 Python 31.9%	 Cuda 7.4%	 C 4.9%	 CMake 1.7%	 Objective-C++ 0.6%	 Other 1.8%
    - 참고로 Tensorflow의 경우  C++ 60.5%	 Python 30.5%	 HTML 3.6%	 Go 1.4%	 MLIR 1.3%	 Java 0.7%	 Other 2.0% 이다.
- eager mode: immediate execution
    - direct access to the Python objects
    - exceptions can be raised directly
    
- 가장 중요한 것 두 가지
    - Tensor라는 다차원 배열을 기본 자료구조로 가짐
    - ```torch.autograd``` 를 사용해 output의 derivative를 계산, tensor를 track할 수 있음
    
### 구성
- 신경망을 구성할 때 사용하는 핵심 모듈들은 ```torch.nn```
- 데이터를 불러오고 다루는 것은 ```torch.util.data``` (그 중 ```Dataset```, ```DataLoader``` 클래스를 많이 보게 될 것)
- 여러 대의 기기나 GPU를 사용한다면 ```torch.nn.DataParallel```, ```torch.distributed```
- 트레이닝을 마친 모델을 업데이트 할 때는 ```torch.optim```

### 관련 사이트
- PyTorch [Get Started](https://pytorch.org/get-started/locally/)
- PyTorch [Resources](https://pytorch.org/resources/) 
    - 한국어 튜토리얼도 있다. [파이토치(PYTORCH) 튜토리얼](https://tutorials.pytorch.kr/)
- [PyTorch Forum](https://discuss.pytorch.org/)

### Tutorials on GitHub
- [Effective PyTorch](https://github.com/vahidk/EffectivePyTorch)
- [Paperspace/PyTorch-101-Tutorial-Series](https://github.com/Paperspace/PyTorch-101-Tutorial-Series)
- [keon/3-min-pytorch](https://github.com/keon/3-min-pytorch)
- [victoresque/pytorch-template](https://github.com/victoresque/pytorch-template)
    - Python >= 3.5 (3.6 recommended), PyTorch >= 0.4 (1.2 recommended) 
- [GunhoChoi/PyTorch-FastCampus](https://github.com/GunhoChoi/PyTorch-FastCampus)
    - PyTorch로 시작하는 딥러닝 입문 CAMP (2017.7~2017.12) 강의자료
    - Python 3.6, pytorch 0.3.1
- [jcjohnson/pytorch-examples](https://github.com/jcjohnson/pytorch-examples)
    - PyTorch 0.4
###### 참고자료
- [DEEP LEARNING WITH PYTORCH](https://pytorch.org/deep-learning-with-pytorch) Chapter 1
