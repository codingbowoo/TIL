# Python dictionary
##### Contents
[How to merge 2+ dictionaries](#merge-dicts)

<br/>

* * *

##### How to merge 2 dictionaries <a id="merge-dicts"></a>

```python3
>>> d1 = {'a': 1, 'b': 2}
>>> d2 = {'c': 3, 'd': 4}

>>> d3 = {**d1, **d2}

>>> d3
{'d': 4, 'c': 3, 'b': 2, 'a': 1}
```

related to 
- [PEP448 (원문)](https://www.python.org/dev/peps/pep-0448/) 
- 정리노트 [pep448.md](https://github.com/codingbowoo/codingbowoo.github.io/blob/master/stack/pythonpractice/pep448.md)
