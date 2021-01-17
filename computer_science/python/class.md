# Python class에 대한 사실 몇가지

##### Contents
- [런타임에 클래스 수정하기](#runtime-class-patch)

* * *
#### 런타임에 클래스 수정하기 <a id="runtime-class-patch"></a>
- [Run-time method patching in Python](https://tryolabs.com/blog/2013/07/05/run-time-method-patching-python/)
- 위 글에서는 override 하는 것만 보여줬는데 충격적이게도 이런 것도 된다! 
```python3
class Student:
    def study(self, name):
        print(f"A student {name} is studying how to code")
 
 
def rest(self, minute):
    print(f"... and is going to take {minute} minutes break!")

Student.rest = rest
```
하면 아래처럼 사용할 수 있다. 
```python3
s = Student()
s.study("codingbowoo")
s.rest(15)

"""
A student codingbowoo is studying how to code
... and is going to take 15 minutes break!
"""
```
- 메소드 뿐만 아니라 오브젝트도 이렇게 할 수 있다.
- 코드를 짜다 보면 클래스가 거대해질 때도 있고, 그럼 문제가 생기거나 기능을 추가하는 식의 일이 생길 때 코드를 읽기? 관리하기? 어려워질 수도 있는데 이 방법을 쓰면 보다 쉬울거 같다. 
