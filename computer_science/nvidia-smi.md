GPU 사용과 관련해서 혼란이 많다- 관련 링크 정리.

- [Inconsistency between GPU memory usage in torch.cuda.memory_summary and nvidia-smi](https://github.com/pytorch/pytorch/issues/37250)
    - nvidia-smi 결과로 보이는 것과 달리 실제로는 CUDA가 잡아먹는 메모리 있음
    - PyTorch 자체가 caching mechanism 있음. [Pytorch documentation-Memory management](https://pytorch.org/docs/stable/notes/cuda.html#memory-management) 참고.
- [nvidia-smi query 도움!](https://nvidia.custhelp.com/app/answers/detail/a_id/3751/~/useful-nvidia-smi-queries)
