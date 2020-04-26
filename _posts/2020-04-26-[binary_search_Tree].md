---
    title : "[자료구조,Python] 파이썬으로 만들어보는 이진 검색 트리 Binary Search Tree"
    
    categories : 
        자료구조
        
    description : "[자료구조,Python] 파이썬으로 구현하는 이진 검색 트리 Binary Search Tree 자료구조"
    
    toc : True
    
    toc_label : "목차"
    
    tags :
        python 
        자료구조
        Search Tree
        
    last_modified_at: 2020-04-26    
---
# Binary Search Tree
Binary search Tree 는 ordered binary Tree 혹은 sorted binary Tree라고 부르기도 합니다.<br/>

Binary Tree는 Search 속도가 다른 자료구조에 비해 빠른편이다. 하지만 Binary Tree 는 자료를 입력할수도 삭제할수도 없습니다.
<br/>
하지만 Linked List 는 검색 속도가 느리지만, 데이터를 입력, 삭제할 수 있습니다.
<br/>
<br/>
**Binary Search Tree** 는 Binary search(검색속도) 와 linked list(데이터 입력 ,삭제)의 장점을 결합한 자료구조 입니다.

## Binary Search Tree 의 속성
Binary Search Tree는 아래와 같은 요소를 충족해야합니다. 즉 아래의 요소에 부합하지 않은 내용이 있다면 그것은 Binary Tree 가 아닙니다.

* 각 노드의 왼쪽 subtree에는 해당 노드의 값보다 작은 값을 지닌 노드들로 이루어져 있다.
* 각 노드의 오른쪽 subtree에는 해당 노드의 값보다 큰 값을 지닌 노드들로 이루어져 있다.
* 중복된 노드가 없어야 한다.
* 왼쪽 subtree, 오른쪽 subtree 또한 이진탐색트리이다.

그리고 Binary Search Tree는 inorder Traversal 방식을 사용합니다. inorder Traversal방식을 사용하면 Binary Search Tree 내 모든 값들을 정렬된 순서대로 읽을 수 있기 때문입니다.

### Binary Tree 와 Linked List의 결합.
위의 내용에서 Binary Search Tree는 Binary Tree 와 Linked List의 장점들을 결합한 구조라고 이야기했습니다. 그렇다면 어떤 방식으로 Linked List 와 Binary Tree를 결합했는지 확인해 보겠습니다.


#### 정렬된 리스트로부터 특정 값 찾기
![]({{ site.url }}/assets/images/dataStructure/SearchTree/SearchTree_1.png    )
위의 리스트에서 우리가 Linked List에서 구현했던 Search 메소드를 사용한다면, header부터 우리가 찾고자하는 노드의 내용까지 순차적으로 모두 확인해봐야할 것 입니다. 지금이야 데이터의 크기가 적으니 큰 부담은 되지 않지만 만약에 10,000개의 데이터 중에 9,999번째 데이터를 찾고자 하면 우리는 9,998개의 데이터를 모두 확인한 후에야 우리가 원하는 데이터 값을 찾을 수 있을것입니다. 그리고 이는 상당히 비 효율적인 검색 방법입니다.
<br/>
우리가 List L에서 12번째 인덱스에 있는 80이라는 값을 찾고자 한다고 가정해 봅시다. Liked List의 Search 메소드였으면 제일처음 **인덱스 0부터 12까지의 데이터를 모두 확인해본 후**에야 80의 데이터가 어디에 있는지 알 수 있을것 입니다. 
<br/>
<br/>
하지만 Binary Search Tree는 Search의 시작이 첫번째 인덱스가 아닌 가운데 인덱스부터 시작합니다. 즉  13//2를 한 값인 6번째 인덱스에서부터 시작하여 6번째 인덱스에 저장된 52라는 값과 찾고자하는 80의 값을 비교합니다. **6번 인덱스에 저장된 52는 80보다 작습니다.** 그렇다면 이제 **Search는 7번 인덱스부터 13번 인덱스까지만 살펴봅니다.** 그이유는 어차피 6보다 작은 인덱스에 저장된 값은 내가 찾고자 하는 80보다 작다는것을 알기 때문입니다.
<br/>
<br/>
**그렇다면 수색범위가 7~ 13번 인덱스 까지로 좁혀졌습니다.** 그렇다면 7과 13의 가운데 값인 인덱스번호 10의 데이터와 찾고자하는 값의데이터를 다시 비교해봅니다. 이번에도 마찬가지로 **10번 인덱스에 저장된 73은 80보다 작습니다.** 그렇다면 **Search는 이제 11번 인덱스부터 13번 인덱스까지만 살펴봅니다.**
<br/>
<br/>
자 이제 **수색범위는 11~13번 인덱스 까지로 좁혀졌습니다.** 다시 위의 과정처럼 11번째와 13번째의 인덱스의 가운데 인덱스인 12번 인덱스와 비교를 합니다.
**12번 인덱스에 저장된 값은 80과 동일합니다.** 이제 끝일까요? 아직 끝난게 아닙니다.
<br/>
<br/>
마즈막으로 **12번째 인덱스와 12번째 인덱스의 가운데값인(?) 12번째 인덱스를 비교합니다.** 자 드디어 원하는 값을 찾았습니다.
> LinkedList 의 Search였으면 13번의 비교가 필요한 것을 우리는 고작 4번의 비교만으로 찾아냈습니다.

### find 메소드
**코드설명** <br/>
```python
def find(L, target, start, end):
    if L[(start + end) // 2] < target:
        return find(L,target,(start + end) // 2 +1, end)
    elif L[(start + end) // 2] > target:
        return find(L,target,start,(start + end) // 2 -1)
    else:
        return L[(start + end) // 2]
```
* parameter 
1. 오름차순으로 정렬된 List : L
2. 찾고자 하는 데이터의 값 : target
3. 검색을 시작할 인덱스 : start
4. 검색을 끝낼 엔드 인덱스 : end

항상 검색은 중간 인덱스 부터 시작된다. 그렇기 때문에 start 와 end 를 더한후 정수값만을 리턴하는 // 연산자를 활용하여 나누어준다.

이때 나올 수 있는 조건이 3가지가 있다. 
* target 데이터가 큰경우
위에 설명했던바와 같이 현재 start 인덱스에 +1 인덱스부터  end 인덱스까지의 중간값을 파라미터로 받아 다시 검색하면된다. 
* target 데이터가 작은경우
위에 설명했던바와 같이 현재 start 인덱스부터  현재 확인해본 인덱스 - 1 까지의 중간값을 찾아서 다시 검색하면된다. 
* target 데이터와 같은경우
현재 확인해본 인덱스의 값을 리턴해주면 된다.

### find 메소드 문제점!

```python
def find(L, target, start, end):
    if L[(start + end) // 2] < target:
        return find(L,target,(start + end) // 2 +1, end)
    elif L[(start + end) // 2] > target:
        return find(L,target,start,(start + end) // 2 -1)
    else:
        return L[(start + end) // 2]
```
위 코드를 동작할 때 우리는 **start > end 인 상황**을 고려하지 않았다. 만약에 start > end의 상황이 계속 재귀함수가 동작할것이고, 파이썬은 자체적으로 이 문제를 막기위해 최대 재귀 호출 횟수를 100회로 제한하여 , 오류가 발생할 것이다. 이와같은 현상을 막기위해 start > end 일시 특정값을 리턴하는 형식으로 코드를 변경하였다.
```python
def find(L, target, start, end):
    if start > end:
        return -1
    if L[(start + end) // 2] < target:
        return find(L,target,(start + end) // 2 +1, end)
    elif L[(start + end) // 2] > target:
        return find(L,target,start,(start + end) // 2 -1)
    else:
```       
## Linked List 와 Binary Tree 의 합체!
자 이제 Binary Search Tree가 어떤방법으로 동작하는지 살펴보았다. 그리고 이걸 Linked List에 적용하여 구현해 보았다.
![]({{ site.url }}/assets/images/dataStructure/SearchTree/SearchTree_1.png    )
<br/>
의 리스트에 Binary Search Tree 의 Search 방식을 적용시키면
<br/>
![]({{ site.url }}/assets/images/dataStructure/SearchTree/SearchTree_2.png    )
<br/>
처럼 되고 리스트의 중심 (52) 의 선을 잡고 쭉 뽑아보면?
<br/>
![]({{ site.url }}/assets/images/dataStructure/SearchTree/SearchTree_3.png    )
<br/>
처럼 Binary Search Tree 의 속성을 충족하는 Binary Tree가 된다.
