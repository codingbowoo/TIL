# DEEP LEARNING WITH PYTORCH

[DEEP LEARNING WITH PYTORCH](https://pytorch.org/deep-learning-with-pytorch) 책을 통해 정리하는 파이토치 **딥러닝** 기초 <br>
https://github.com/deep-learning-with-pytorch/dlwpt-code 도 참고하자.

## 1 Introducing deep learning and the PyTorch library
- Pytorch의 핵심 자료구조는 **Tensor** : numpy array와 비슷한 다차원 배열
    - 거의 비슷하지만 GPU 가속, autograd 등의 추가적인 기능 제공
- 책에서 주로 다루는 예제는 2D, 3D 데이터에 대한 이미지 프로세싱 (이런)
- DEEP LEARNING: NO MORE HANDCRAFTED FEATURES
    - but operating on a mathematical entity so that it discovers representations from the training dta autonomously
- 너무 당당하게 내가 처음으로 배워야 할 딥러닝 라이브러리가 PyTorch라고 쓰여 있음. 매력적인걸?
- 자세한 내용은 앞서 정리한 [pytorch 문서](https://github.com/codingbowoo/codingbowoo-resource/blob/master/stack/ML/pytorch.md) 참고

## 2 It starts with a tensor
2.1 Tensor fundamentals 18
2.2 Tensors and storages 22
2.3 Size, storage offset, and strides 24
2.4 Numeric types 30
2.5 Indexing tensors 31
2.6 NumPy interoperability 31
2.7 Serializing tensors 32
2.8 Moving tensors to the GPU 34
2.9 The tensor API 35

## 3 Real-world data representation with tensors
3.1 Tabular data 40
3.2 Time series 49
3.3 Text 54
3.4 Images 60
3.5 Volumetric data 63

## 4 The mechanics of learning
4.1 Learning is parameter estimation 70
4.2 PyTorch’s autograd: Backpropagate all things 83
5 Using a neural network to fit your data 101
5.1 Artificial neurons 102
5.2 The PyTorch nn module 110
5.3 Subclassing nn.Module 120
