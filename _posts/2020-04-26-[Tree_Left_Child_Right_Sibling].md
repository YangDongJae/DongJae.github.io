---
    title : "[자료구조,Python] 파이썬으로 만들어보는 Tree(Left Child- right Sibling) "
    
    categories : 
        자료구조
        
    description : "[자료구조,Python] 파이썬으로 구현하는 트리(Tree_Left Child- right Sibling) 자료구조"
    
    toc : True
    
    toc_label : "목차"
    
    tags :
        python 
        자료구조
        Tree
        
    last_modified_at: 2020-04-26    
---
# Tree 의 문제점
이전시간에 만들어본 [Tree](https://yangdongjae.github.io/자료구조/Tree/)는 python의 리스트를 활용해서 만들었다. 하지만 파이썬 (뿐만아니라 대다수의 프로그래밍 언어)에서는 List에 추가될 데이터 값을 미리 확보하기위하여 리스트의 데이터 용량보다 더 큰 값들을 할당한다.  

```python
list1 = []


for i in range(0,20):
    list1.append(i)
        print("List :" , list1)
        print("Length :", len(list1))
        print("Size: ", list1.__sizeof__())
        print("----------------")
```
위 코드예제를 실행해보면 쉽게 알 수 있다. 자 결과값을 확인해보자. 

```
List : [0]
Length : 1
Size:  72
----------------
List : [0, 1]
Length : 2
Size:  72
----------------
List : [0, 1, 2]
Length : 3
Size:  72
----------------
List : [0, 1, 2, 3]
Length : 4
Size:  72
----------------
List : [0, 1, 2, 3, 4]
Length : 5
Size:  104
----------------
List : [0, 1, 2, 3, 4, 5]
Length : 6
Size:  104
----------------
List : [0, 1, 2, 3, 4, 5, 6]
Length : 7
Size:  104
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7]
Length : 8
Size:  104
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8]
Length : 9
Size:  168
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
Length : 10
Size:  168
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
Length : 11
Size:  168
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]
Length : 12
Size:  168
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
Length : 13
Size:  168
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]
Length : 14
Size:  168
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14]
Length : 15
Size:  168
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
Length : 16
Size:  168
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16]
Length : 17
Size:  240
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17]
Length : 18
Size:  240
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18]
Length : 19
Size:  240
----------------
List : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
Length : 20
Size:  240
----------------
```
위 결과값에서 볼 수 있듯이, 저장된 값에 비해 리스트의 크기가 기하급수적으로 증가하는 것을 확인할 수 있다.  즉 우리가 만들었던 original Tree에서는 parents 노드들의 child 노드들을 각각의 리스트를 만들어 저장했다. 그만큼 리스트의 size는 불필요하게 많이 만들어졌다는 의미이다. 
<br/>
리스트가 작을땐 얼마 안되는 메모리의 양일지 몰라도, 리시트의 크기가 커질수록 데이터의 낭비는 기하급수적으로 증가된다.
<br/>
우리는 이러한 비효율적인 트리 구조를 해결하기위하여 Left Child - Right Sibling 구조로 노드를 수정할 것이다.

# Tree (Left Child - Right Sibling)

![]({{ site.url }}/assets/images/dataStructure/Tree/Tree_1.png )
우리는 데이터의 낭비를 막기위해 위와같은 구조로 노드를 수정할 필요가 있다고 위에서 설명했다. Left Child - Right Sibling 구조로 수정하면 원래 3개의 리스트로 구성되어있던 A의 child 노드를 1개로 바꿀 수 있다. 

우리는 특정 노드 A 에 제일 왼쪽의 child 노드만을 연결하고 연결된 child 노드가 sibling 노드와 child 노드를 가리키게 했다. 이 방법을 통해 우리는 리스트를 활용하지 않고도 트리를 만들 었고, 데이터의 낭비를 막았다.

## Node class
```python
class Node:

    def __init__(self, data):
      self.data = data
      self.left = None
      self.right = None
  
    def get_data(self):
      return self.data

    def set_left(self,left):
      self.left = left
        
    def set_right(self,right):
      self.right = right
        
      
    def get_left(self):
      return self.left
        
    def get_right(self):
      return self.right
```
**코드설명**
 __init__ 함수를 통하여 노드의 왼쪽 데이터와 오른쪽 데이터가 저장될 leaft(child)와 rigth(sibling) 객체를 생성했다.
 
 * get_left 함수를 통하여 현재 left가 갖는 값을 확인할 수 있게 self.left를 리턴해준다.
 
 * get_right 함수를 통하여 현재 right가 갖는 값을 확인할 수 있게 self.right를 리턴해준다.
 
 * set_left 함수를 통하여 현재 left가 갖는 값을 설정할 수 있게 파라미터 left 값을 self.left가 참조하게 한다.
 
 * set_right 함수를 통하여 현재 right가 갖는 값을 설정할 수 있게 파라미터 right 값을 self.right가 참조하게 한다.
 
 
## 노드생성
 자 이제 바뀐 노드클래스의 함수에 따라서 새롭게 노드들을 연결해보자.
 ```python
 tree.set_root(node_a)

 node_a.set_left(node_b)

 node_b.set_left(node_e)
 node_b.set_right(node_c)

 node_c.set_left(node_h)
 node_c.set_right(node_d)

 node_d.set_left(node_j)

 node_e.set_left(node_k)
 node_e.set_right(node_f)

 node_f.set_right(node_g)

 node_g.set_left(node_m)

 node_h.set_left(node_n)
 node_h.set_right(node_i)

 node_j.set_left(node_o)

 node_k.set_right(node_l)

 node_o.set_right(node_p)
 ```
 
## print 메소드
 
 ```python
 def print_node(self, node, depth):
 msg = ""
 if node is not None:
   for i in range(0, depth):
     msg += "  "
   msg += node.get_data()
   print(msg)
   
   self.print_node(node.get_left(), depth + 1)
   self.print_node(node.get_right(), depth ) 
```
우리는 바뀐 노드클래스에 맞는 print메소드를  재귀함수를 통하여 구현해보았다. 그 결과값을 확인해보자.
```
A
B
  E
    K
    L
  F
  G
    M
C
  H
    N
  I
D
  J
    O
    P
```
위와같이 띄어쓰기로 Depth를 구분하여 노드들이 출력됬다면 성공이다. 단 **original Tree 보다 훨씬 적은 size를 갖는 Tree 구조를 만든 것 이다.** 
