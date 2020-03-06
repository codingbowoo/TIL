# cache

python 하는 사람이라면 standard library에 lru_cache를 알아야한다는 내용을 듣고 이름이 익숙한데... 싶어서 찾아본 내용 


- Cache hit: CPU가 원하는 데이터가 캐시에 있다!
- Cache miss: CPU가 원하는 데이터가 캐시에 없다ㅜ
- Hit ratio: (# of cache hit) / (# of total access)



재밌는건 python에서는 데코레이터로 lru cache를 쓸 수 있다는 것이다! 
```python3
from functools import lru_cache

@lru_cache(maxsize=None)
def fibonacci_cache(n):
    if n < 2:
        return n
    return fibonacci_cache(n-2) + fibonacci_cache(n-1)

```

- cache memory?
- database cache?





###### resources
- [컴퓨터 구조 - LRU 알고리즘](https://silentcargo.tistory.com/118)
- [Every Python Programmer Should Know Lru_cache From the Standard Library](https://medium.com/better-programming/every-python-programmer-should-know-lru-cache-from-the-standard-library-8e6c20c6bc49)by Fabian Bosler
