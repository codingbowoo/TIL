> 5개의 데이터셋에 대해 병렬적으로 실행 가능한 내용이 있다. 
현재는 5개의 주피터 노트북 파일을 사용해 실행 중인데, 여러 탭을 켜두려니까 상당히 번거롭다.
이에 multiprocessing이 도움이 될까 싶어 정리할 예정이다.

### [multiprocessing](https://docs.python.org/3.7/library/multiprocessing.html) in python 3.7
```python3
import multiprocessing
```

   - ```multiprocessing.cpu_count()``` : core의 개수와 컴퓨터가 실행할 수 있는 job의 개수를 알려준다.<br> >>> sample output: ```12```

   - starting method: **spawn**(Unix and Windows), **fork**(Unix only), **forkserver**


### [Joblib: running Python functions as pipeline jobs](https://joblib.readthedocs.io/en/latest/)
```python3
from joblib import Parallel, delayed
```  

- **```Memory```**```([location, backend, cachedir, …])```:	A context object for caching a function’s return value each time it is called with the same input arguments.
- **```Parallel```**```([n_jobs, backend, verbose, …])```:	Helper class for readable parallel mapping.<br> >>> sample code: 
  ```python3
  Parallel(n_jobs=multiprocessing.cpu_count())
  ```
- **```dump```**```(value, filename[, compress, protocol, …])```:	Persist an arbitrary Python object into one file.
- **```load```**```(filename[, mmap_mode])```:	Reconstruct a Python object from a file persisted with joblib.dump.
- **```hash```**```(obj[, hash_name, coerce_mmap])```:	Quick calculation of a hash to identify uniquely Python objects containing numpy arrays.
- **```register_compressor```**```(compressor_name, compressor)```:	Register a new compressor.


참고자료 
- [Quick and Easy Parallelization in Python](https://medium.com/@mjschillawski/quick-and-easy-parallelization-in-python-32cb9027e490)
