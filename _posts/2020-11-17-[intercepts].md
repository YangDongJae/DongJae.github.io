---
    title : "python intercepts,파이썬 intercepts"
    describe : "데이터 분석에 필요한 지식 python intercept" 
    categories : 
        빅데이터   

    tags :
        빅데이터

    toc : True

    toc_label : "목차"        

    last_modified_at : 2020-07-12

---
**python 에서는 intercepts를 사용하여 함수호출을 가로 채서 원하는 방식으로 처리할 수 있다.** 

# intercepts
```python
def print_exam(print_func, message):
    return print_func(''.join(reversed(message)))
print("hello world")

>>> hello world
```
print 를 진행했을 시 정상적으로 hello world가 출력되는 것을 확인할 수 있다.

```python
intercepts.register(print,print_handler)
print("hello world")

>>> dlrow olleh
```

위와같이 intercept.register를 활용하면 print라는 함수를 print_handler라는 함수로 가로채서 hello world가 아닌 dlrow olleh가 output으로 나온다.