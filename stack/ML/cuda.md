# CUDA

## CUDA with PyTorch

#### CUDA 사용 가능한지 확인하기
```python3
import torch
torch.cuda.is_available()
```

#### CUDA 사용 가능한 현재 디바이스 확인하기
```python3
import torch

# 디바이스 id
d_id = torch.cuda.current_device()

# 디바이스 확인
torch.cuda.get_device_name(d_id)
```

#### 현재 GPU 메모리 상태 관련 명령어
```python3
import torch

torch.cuda.memory_allocated()
torch.cuda.memory_cached()
torch.cuda.empty_cache()
```
