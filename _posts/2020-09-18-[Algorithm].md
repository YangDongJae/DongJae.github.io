---
  title : "[알고리즘] List에서 중복되지않는 1개의 값 추출하기"

  describe : "Python [알고리즘] List에서 중복되지않는 1개의 값 추출하기"

  categories : 
      Algorithm

  toc : True

  toc_label: "목차"

  tags : 
    python,Algorithm

  last_modified_at : 2020-09-17

  use_math: true
---

상기 문제는 프로그래머스에서 제공한 알고리즘 문제를 푼 소스코드 입니다.

```python
#input value
participant = ['leo', 'kiki', 'eden']
completion = ['eden', 'kiki']

result = []
for i in participant:
    #check loop current element 
    print("[" , i , "]" )
    for j in completion:
        #check loop current elemnt
        print( i , j)
        if i == j:
            result.append(i)
            participant.remove(i)
            completion.remove(i)
            print('reuslt = ' , result)
            print('participant' , participant)
    print('----')
    
print(participant , completion)
```

#### trouble 
로직이 동작하면서 participant 의 마즈막 요소인 eden 에서 동작하지 않음을 확인
* 로직이 동작하면서 리스트를 수정해서 그런것으로 수정

#### trouble shooting

[python Document](https://docs.python.org/ko/3/tutorial/introduction.html)를 참고하여 [Shallow copy](https://docs.python.org/3/library/copy.html#shallow-vs-deep-copy) 방법을 활용, 문제 해결

```python 

def solution(participant, completion):
    """    
    1. 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
    2. completion의 길이는 participant의 길이보다 1 작습니다.
    3. 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
    4. 참가자 중에는 동명이인이 있을 수 있습니다.
    """
    if len(participant) < 1 or len(participant) > 100000:
        print("error! please check your runner list!")
    
    elif len(participant) - len(completion) != 1:
        print("error! please check your runner list!")

    else:
        for i in participant:
            if len(i) < 1 or len(i) > 20:
                print("error! please check your runner list!")
                break
            
            # make shallow copy use by [:]
            for i in participant[:]:
                if i in completion:
                    participant.remove(i)
    
    return participant

#test
participant = ['leo', 'kiki', 'eden']
completion = ['eden', 'kiki']
print(solution(participant , completion))


```

* [algorithm github](https://github.com/YangDongJae/Algorithm)
