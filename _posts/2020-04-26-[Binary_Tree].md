---
    title : "[자료구조,Python] 파이썬으로 만들어보는 이진트리 Binary Tree와 순회"
    
    categories : 
        ComputerScience
        
    description : "[자료구조,Python] 파이썬으로 구현하는 이진트리 Binary Tree 자료구조 , 순회 (전위 , 중위 , 후위 )"
    
    toc : True
    
    toc_label : "목차"
    
    tags :
        자료구조
        
    last_modified_at: 2020-04-26    
---
# Binary Tree

Binary 트리는 각 노드가 child를 최대 2명 가지는 트리를 의미한다. 즉 **child 노드가 없을수도 있고 , 한가지일 수도있으며 최대 2개까지 취하는 트리**를 이진트리 Binary Tree 라고 이야기한다.
<br/>
Binary트리에서 최대 child 노드의 수는 Depth/Level 당 2의 (Level/Depth -1)승  입니다.  예를들면 Level 4에 있는 노드가 갖을 수 있는 child 노드의 최대 갯수는 2의 4-1승 입니다.
<br/>
Binary 트리의 최대 노드 수는 2 의 height승 -1 입니다. 예를들어 height가 5인 Binary 트리가 있다고 가정해보면, 이 트리의 최대 노드 갯수는 2의 5승에 루트 노드는 언제나 1개임으로 -1 한 값인 31 개 입니다.

<br/>
Binary 트리는 **Full Binary Tree** 와 **Complete Binarry Tree**가 있다.



## Full Binary Tree
Full Binary Tree는 아래의 그림처럼 **child노드가 없거나 2개인 경우**를 이야기합니다. 제일 이상적인 Binary Tree의 모습이며 

![]({{ site.url }}/assets/images/dataStructure/Tree/Tree_2.png    )
<br/>
## Complete Binary Tree
Complete Binary Tree 는 아래의 그림처럼 **child의 갯수가 최대 2개이면서 노드들이 왼쪽으로 정렬되어있는 Tree** 를 이야기합니다.<br/>
![]({{ site.url }}/assets/images/dataStructure/Tree/Tree_3.png    )
<br/>
<br/>
만약 아래의 그림처럼 **왼쪽정렬이 되지 않은 트리는 Complete Binary Tree가 아닙니다.**
![]({{ site.url }}/assets/images/dataStructure/Tree/Tree_4.png    )

>  N개의 노드를 갖는 Complete Binary Tree의 height 는  ⌈log (2) * (N + 1)⌉입니다.
N이 13개의 노드를 갖는 Complete Binary Tree 가 있다고 가정하면, 위 공식에 의해서 ⌈log(2) * (13 +1)⌉이 될것입니다.
계산을 해보죠 ⌈log(2) * (13)⌉이 될것이고, 값은 ⌈5.117⌉정도가 됩니다. 하지만 천장함수에의해서 4가 되죠.
</br>
즉 13개의 노드를 갖는 Complete Binary Treed의 Height 는 4가 됩니다.

## Binary Tree 구현

### Python List
Binary Tree는 리스트로도 구현할 수 있습니다. 왜냐하면 아래의 Binary Tree가 아래의 특징들로 정의될 수 있기 때문입니다.
<br/>
* list[i]의 left child의 위치 = list [2 X i]
* list[i]의 right child의 위치 = list [2 X i + 1]
* list[i]의 parent node 의 위치 = list [⌊i / 2⌋]
<br/>
![]({{ site.url }}/assets/images/dataStructure/Tree/Tree_6.png    )
<br/>
우리는 위와같은 노드를 left child노드를 먼져 리시트에 담으면서 아래와 같이 정의해 보았다.
<br/>
![]({{ site.url }}/assets/images/dataStructure/Tree/Tree_5.png    )
<br/>
자 이제 확인해보자

* list[2]의 left child의 위치는 list[4]이다. 실제로도 맞다.
* list[2]의 right child의 위치는 list[5]이다. 실제로도 맞다.
* list[2]의 parent node 의 위치는 = list [1]이다 .실제로도 맞다.
<br/>
하지만 위와같은 방법은 실제로 사용하지 않는다. 왜냐하면 **비효율적** 이기 때문이다. 만약 데이터의 구조가 아래와 같다면?
![]({{ site.url }}/assets/images/dataStructure/Tree/Tree_7.png    )
<br/>
우리는 리스트를 아래처럼 만들어야 할 것이다.
![]({{ site.url }}/assets/images/dataStructure/Tree/Tree_8.png    )
<br/>

우리는 위와같은 낭비를 막기위해서 left child 와 right child로 노드를 구성함으로 조금더 **효율적으로** Binary Tree를 구현할 것이다.

### Node 클래스
```python
class Node:
    def __init__(self,data):
        self.data = data
        self.left_child = None
        self.right_child = None
        
    def get_left_child(self):
        return self.left_child

    def get_right_child(self):
        return self.right_child

    def get_data(self):
        return self.data

    def set_left_child(self, left_child):
        self.left_child = left_child
        
    def set_right_child(self, right_child):
        self.right_child = right_child
```
**코드설명**

node에 필요한 left_child와 Right_child 그리고 data 를 __init__  함수를 사용하여 객체로 생성한다.
get_left_child 와 get_right_child를 사용해서 각각의 값을 리턴하여 확인할 수 있게한다.

set_left_child 와 set_right_child를 사용해서 메소드 내부에서 사용할 left_child, right_child값을 파라미터로 받은 후 그 값을 참조시킨다.

```python
b_tree = Binary_tree()

node_a = Node("A")
node_b = Node("B")
node_c = Node("C")
node_d = Node("D")
node_e = Node("E")
node_f = Node("F")
node_g = Node("G")
node_h = Node("H")

node_a.set_left_child(node_b)
node_a.set_right_child(node_c)

node_b.set_left_child(node_d)
node_b.set_right_child(node_e)

node_c.set_right_child(node_f)

node_d.set_right_child(node_g)

node_e.set_left_child(node_h)
```
**코드설명**

Node class 의 __init__함수에 Data를 전달함으로 A ~ H 까지의 데이터를 취하는 노드를 생성한 후 , Node클래스의 set_left_child 와 set_right_child를 사용해서 각각의 노드를 연결했다.

###  Binary Tree 클래스
```python
class Binary_tree:
    def __init__ (self):
        self.root = None
        
    def get_root(self):
        return self.root

    def set_root(self, root):
        self.root = root
```
**코드설명**
Binary Tree의 Root node 를 설정하기 위하여 __init__함수에서 root 객체를 생성하고, get_root를 통해 현재 Root의 값을 확인할 수 있게 Root를 리턴하도록 하였다. set_root 메소드는 파라미터 root 로 통해 전달된 값을 self.root가 참조하여 root를 재 설정하는 함수로 정의하였다.

## Binary Tree 의 연산 (순회)
Binary Tree는 총 4가지 순회방식이 있다.
* Pre-order traversal - 전위 순회
* In-order Traversal - 중위 순회
* Post-order Traversal - 후위 순회
* Level-order Traversal - 레벨 순회

### Pre-order traversal - 전위 순회
1. 노드n 에 도착하면 먼저 방문한 후 left child로 순회.
2. 노드n 의 left child 노드를 모두 방문 했다면, 노드 n 의 right_subtree의 모든 Desencdant(후손) 노드 방문

![]({{ site.url }}/assets/images/dataStructure/Tree/Tree_9.png    )
<br/>

```python
def pre_order(self, node):
    if node != None:
        print(node.get_data(), end = " ")
        self.pre_order(node.get_left_child())
        self.pre_order(node.get_right_child())
```


### In-order Traversal - 중위 순회
1. 노드 n에 도착했을 때 n의 왼쪽 subtree로 순회
2. 노드 n의 왼쪽subtree의 모든 노드 방문 후, n을 방문
3. n방문 후 n의 오른쪽 subtree로 순회
![]({{ site.url }}/assets/images/dataStructure/Tree/Tree_10.png    )
<br/>

#### 이동 과정
1. 왼쪽에 subtree가 없을때 까지 이동  
2. 왼쪽에 subtree가 없으니 **현재노드(D)방문** 후  오른쪽 subtree로(G) 이동 
3. 현재 노드(G)에 왼쪽에 subtree가 없으니 **현재 노드(G)방문**
4. 오른쪽 subtree가 없기때문에 parent 노드 (D)로 이동 
5. 현재노드(D)의 왼쪽과 오른쪽 subtree모드 순회했기 때문에 parent 노드(B)로 이동 
6. 현재노드(B)의 왼쪽 subtree를 모두 방문했기 때문에 **현재노드(B)방문** 오른쪽 subtree (E)로 이동 
<br/>
...
<br/>

7. 현재 노드(C)의 왼쪽 subtree 가 없기 때문에 **현재 노드 (C)방문** 후 오른쪽 서브트리 (F) 로 이동 
8. 현재 노드(F)에 왼쪽에 subtree가 없으니 **현재 노드(F) 방문** 
9. 오른쪽 subtree가 없기때문에 parent 노드 (C)로 이동 
10. 오른쪽 subtree를 모두 순회했기 때문에 Root Node(A)로 이동 후 종료
<br/>

```python
def in_order(self, node):
    if node != None:
        self.in_order(node.get_left_child())
        print(node.get_data(), end = " ")            
        self.in_order(node.get_right_child())
```

### Post-order Traversal - 후위 순회
1. 노드 n에 도착했을 때 n을 방문하지 않은채로 왼쪽 subtree로 순회
2. 노드 n의 왼쪽 subtree의 모든 노드 방문 후, 노드 n의 오른쪽 subtree의 모든 노드 방문
3. 노드 n의 오른쪽 subtree의 모든 노드 방문 후 n 방문
![]({{ site.url }}/assets/images/dataStructure/Tree/Tree_11.png    )
<br/>

#### 이동 과정
1. 왼쪽에 subtree가 없을때 까지 이동 
2. 왼쪽에 subtree가 없으니 오른쪽 subtree로(G) 이동 
3. 현재 노드(G)에 왼쪽,오른쪽에 subtree가 없으니 **현재 노드(G) 방문**
4. 왼쪽, 오른쪽 subtree가 없기때문에 parent 노드 (D)로 이동 
5. 현재노드(D)의 왼쪽과 오른쪽 subtree모드 순회했기 때문에 **현재노드(D) 방문**
6. 현재노드(D)의 왼쪽,오른쪽 subtree를 모두 방문했기 때문에 Parent 노드(B)로 이동 
7. 왼쪽에 subtree모두 방문 했으니 오른쪽 subtree로(E) 이동 
<br/>
...
<br/>

7. 현재 노드(C)의 왼쪽 subtree 가 없고 오른쪽 subtree 모두 방문, **현재노드 (C) 방문** 
8. 현재노드(C)의 왼쪽 subtree 는 없고, 오른쪽 subtree를 모두 방문했기 때문에 Parent 노드(A)로 이동 
9. 현재노드 (A)의 왼쪽subtree 와 오른쪽 subtree 모두 방문했기 때문에 **Root Node (A) 방문**
<br/>

```python
def in_order(self, node):
    if node != None:
        self.in_order(node.get_left_child())         
        self.in_order(node.get_right_child())
        print(node.get_data(), end = " ")           
```
### Level-order Traversal - 레벨 순회
각 Level의 노드를 좌 -> 우 순서로 순차 방문한다.
