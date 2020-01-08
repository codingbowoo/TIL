# Hyperparameters

> Seq2Seq의 경우 영향을 가장 많이 미치는 하이퍼파라미터는 <br>
```batch_size```, ```optimizer_type```, ```learning_rate```, ```num_layers_encoder```, ```num_layers_decoder``` 

이름에 통일성이 있어야 할 것 같아서 공통으로 많이 쓰는 파라미터들을 표로 정리해본다. 
(이 때 많이 쓰는 초기값의 기준은 Amazon SageMaker에서 따왔다.)

| 이름	| 설명 | 초기값 | 
|---|---|:---:|
| batch_size | 경사 하강에 대한 미니 배치 크기 | 64 |
| checkpoint_frequency_num_batches | x회의 배치마다 체크포인트 및 검증 | 1000 |
| clip_gradient	| 경사 하강 최솟값 고정 (음수일 경우 비활성화)| 1 |
| cnn_activation_type	| 사용할 cnn 활성화 유형: glu, relu, softrelu, sigmoid, tanh | glu |
| cnn_hidden_dropout	| 컨볼루션 계층 사이의 dropout 정도 | 0 [0, 1]|
| cnn_kernel_width_decoder | cnn 디코더에 대한 커널 너비 | 5 |
| cnn_kernel_width_encoder | cnn 인코더에 대한 커널 너비 | 3 |
| cnn_num_hidden | 인코더 및 디코더에 대한 cnn 숨겨진 유닛 수 | 512|
| decoder_type | 디코더 유형: rnn 또는 cnn | rnn |
| embed_dropout_source | source 임베딩에 대한 dropout 정도 | 0 |
| embed_dropout_target | target 임베딩에 대한 dropout 정도 | 0 |
| learning_rate	| 초기 학습률 | 0.0003 |
| loss_type	| training에 대한 loss function : cross-entropy | cross-entropy |
| max_num_batches	| 처리할 업데이트/배치의 최대 수, -1일 때 무제한 | -1 |
| max_num_epochs | training 데이터 epoch의 최대 수( < max_num_epochs ) | none |
| max_seq_len_source | 소스 시퀀스의 최대 길이(더 긴 시퀀스는 길이에 맞게 cut | 100 |
| min_num_epochs | early_stopping 사용 전의 최소 training epoch 수 | 0 |
| momentum | sgd 모멘텀 상수(adam/rmsprop 사용 시 none) | none |
| num_embed_source | source token의 임베딩 size | 512 |
| num_layers_decoder | 디코더 rnn 또는 cnn 의 layer 수 | 1 |
| optimized_metric | 최적화에 사용하는 지표: perplexity, accuracy, bleu | perplexity |
| optimizer_type | adam, sgd, rmsprop | adam |
| rnn_attention_in_upper_layers	| 2개 이상 layer일 때 rnn 상위 계층으로 attention 전달 여부 | true |
| rnn_attention_num_hidden | attention layer의 hidden unit 수 | rnn_num_hidden |
| rnn_attention_type | 인코더의 어텐션 모델: dot, fixed, mlp, bilinear | mlp |
| rnn_cell_type	| 특정 유형의 rnn 아키텍처: lstm, gru | lstm |
| rnn_decoder_state_init | last, avg,  zero | last |
| rnn_first_residual_layer | 첫 번째 rnn residual layer(num_layers_decoder>=2 일 때만) | 2 |
| rnn_num_hidden | 인코더 및 디코더 rnn의 hidden unit 수(2의 배수 because of Bidirectional LSTM) | 1024 |
| rnn_residual_connections | rnn 의 residual connection 여부 | false |
| rnn_decoder_hidden_dropout | context- decoder rnn hidden state 사이의 dropout rate | 0 |
| training_metric | validation data의 평가: perplexity, accuracy | perplexity |
| weight_decay | weight decay 상수 | 0 |
| weight_init_scale	| 가중치 초기화 scale(uniform, xavier) | 2.34 |
| weight_init_type | 가중치 초기화 유형: uniform, xavier | xavier |

###### references
뭔가 convention이 있을 것 같아서 찾아봤다.
- https://docs.aws.amazon.com/ko_kr/sagemaker/latest/dg/seq-2-seq-hyperparameters.html
    - 더 다양한 모델에 해당하는 내용은 [Amazon SageMaker - 개발자 안내서](https://docs.aws.amazon.com/ko_kr/sagemaker/latest/dg/sagemaker-dg.pdf)
