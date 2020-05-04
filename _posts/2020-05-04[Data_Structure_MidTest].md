---
    title : "[자료구조] 중간고사 기록용"

    categories : 
        자료구조
    
    description : "리스트 , 스택 , 큐 , 트리 , 이진트리 , 이진검색트리

    toc : True

    toc_label : "목차"

    tags : 
        중간고사
        자료구조


    last_modified_at : 2020-05-04
 
---

# 중간고사 기록용 한눈에 보는 기본 자료구조

개강하고 난 시점부터 지금까지 자료구조 수업을 통해 **List, Stack, Queue, Tree, Binary Tree, Binary Search Tree**에 대해서 배워보았다. 중간고사가 다가오는 시점에서 지금까지 학습한 내용을 간략하게 요약할 필요가 있다고 생각해서 작성한다.
<br/>
<br/>

## List

우리 컴퓨터는 메모리에 딱딱 정렬된 상태로 저장하지않는다. 그래서 테트리스할때 처럼 데이터와 데이터사이에 빈 공간이 생긴다. 그 공간에 다른 데이터를 저장하고, 이를 연결하여 데이터를 효율적으로 저장하는 형태가 List 형태이다.

### [Singly Linked List](https://yangdongjae.github.io/자료구조/Linked_list/)

**특징** <br/>

1. 노드가 현재값과 다음값을 가리키는 두가지 값으로 구성되어있다.<br/>
2. Tree는 제일 처음에 추가된 노드(리스트의 첫번째 데이터) 의 값을 가리키는 **'Header'** 와 현재 리시트의 제일 끝 데이터를 가리키는 **'Tail'** 그리고 노드의 크기를 나타내는 **'Size'** 로 구성되어있다.

### [Doubly Linked List](https://yangdongjae.github.io/자료구조/Doubly-Linked-List/)

**특징** <br/>

1. 노드가 현재값과 다음값 이전값을 가리키는 **세가지 값**으로 구성되어있다.<br/>
2. Tree는 제일 처음에 추가된 노드(리스트의 첫번째 데이터) 의 값을 가리키는 **'Header'** 와 현재 리시트의 제일 끝 데이터를 가리키는 **'Tail'** 그리고 노드의 크기를 나타내는 **'Size'** 로 구성되어있다.

일상생활에서 흔히 사용하는 뒤로가기 , 앞으로가기 기능이 Doubly Linked List를 사용하는 대표적인 예시이다.

### Circuly linked list

**특징** <br/>

1. 노드가 현재값과 다음값을 가리키는 두가지 값으로 구성되어있다.<br/>
2. 리스트의 마즈막 노드 Tail 이 Header를 가리키며 순환하는 구조이다.
3. Tree는 제일 처음에 추가된 노드(리스트의 첫번째 데이터) 의 값을 가리키는 **'Header'** 와 현재 리시트의 제일 끝 데이터를 가리키는 **'Tail'** 그리고 노드의 크기를 나타내는 **'Size'** 로 구성되어있다.

포커 , 섯다 등에 활용된다. 포커 혹은 섯다와 같은 유형의 게임들은 패를 모두 사용하거나 게임이 종료되면 다시 온전한 패의 상태로 돌아가야되기 때문이다.

## [Stack](https://yangdongjae.github.io/자료구조/Stack/)

**First In Last Out** 으로 먼저들어온 데이터를  제일 마즈막에 처리한다.

**특징**

1. Firt In Last Out 으로 노드가 데이터의 크기를 가리키는 **size**와 데이터 처리가 이루어질 **top**으로 이루어져있다.
2. 모든 데이터의 처리는 **top** 에서만 이루어진다.
3. Stack 데이터 구조에서 데이터를 추가하는 행위를 **push** 라고하고 데이터를 처리하는 행위를 **pop**이라고 한다.

재귀함수의 동작원리를 설명하는 자료구조이다.

## [Queue](https://yangdongjae.github.io/자료구조/Queue/)

**First In First Out**으로 가장먼저 들어온 데이터가 가장 먼저 나간다.

**특징**

1. First In First Out으로 노드의 데이터가 데이터의 앞을 가리키는 **fron** 와 데이터의 마즈막인 **rear**, 데이터의 크기를 나타내는 **size**로 구성되어있다.
2. Queue 데이터구조에서 데이터를 추가하는 행위를 **enqueue** 라고하며, 데이터를 처리하는 행위를 **dequeue** 라고한다.


## [Tree](https://yangdongjae.github.io/자료구조/Tree/)

검색에 최적화된 자료구조 형태로, 비선형 구조를 하고있다. 

### Tree 용어
child - 현재 노드에 직접적으로 연결된 밑에 있는 노드들<br/>
Leaf - 제일 밑에 있는 노드들<br/>
terminal - 제일 밑에 있는 노드이면서 Level이 제일 높은 노드<br/>
Non-terminal - 제일 밑에 있는 노드이지만 Level이 제일 높지 않은 노드<br/>
Root - 제일 위에 있는 노드 <br/>
degree - 특정 노드에 Child 노드의 갯수<br/>
parent - 특정 노드에 위에 직속으로 연결되어있는 노드<br/> 
sibiling - 같은 level에 있는 노드 <br/>
Ancestor - Root부터 특정 노드까지  직속으로 연결되어있는 노드<br/>
desencdant - 특정 노드에서 아래방향으로 뻗어져있는 모든 노드 <br/>
subtree - parent 노드가 Root 노드인 트리<br/>
level - Root노드를 1로 했을때 특정노드까지 도달하는데 걸리는 거리<br/>
height -  Root노드를 1로했을때 Max Level

### left child rigth sibiling 
리스트 형태로 트리를 구현하면 쓸대없는 메모리 낭비가 많이 일어남(파이썬 기준). 이유는 파이썬에서 리스트를 만들 때 다음에 들어올 데이터의 량을 미리 확보해 놓기때문. 이 낭비를 막기위해 우리는 노드를 left , rigth 로 나누어 left 에는 child 노드를 right 에는 sibiling 노드를 취함.

## [Binary Tree](https://yangdongjae.github.io/자료구조/Binary_Tree/)

### Full Binary Tree
child 노드의 갯수가 0 or 2 인 트리

### Complete Binary Tree
child 노드의 갯수가 최대 2개이면서 왼쪽으로 정렬되어있는 트리

### 순회방법

#### Deptth First Search
1. inorder
특정 노드에 도착하면 그 노드 방문핳지 않고 왼쪽 subTree 로 이동, 왼쪽 subTree 모든 노드 방문(left_child가 없을때) 후 오른쪽 subTree로 이동 같은방식으로 방문 마지막에 특정노드(left_child , rigth_child 모두 방문 후) 방문
2. preorder
특정 노드에 도착하면 그 노드를 방문하고 왼쪽 child 노드로 이동 -> 특정 노드의 subTree 를 모두 방문했으면 특정노드의 오른쪽 subTree 로 이동
3. postorder
특정 노드에 도착하면 바로 왼쪽 subTree 로 이동, 특정노드의 left subTree를 의 모든 노드 방문 한 후 n을 방문 (즉 left_child가 없으면 방문) -> 오른쪽 subTree 로 이동 후 같은 방식으로 진행

#### Breadth Fist Search

1. level-order
각 leve의 노드를 좌 -> 우 순서대로 방문.

## [Binary Search Tree](https://yangdongjae.github.io/자료구조/binary_search_Tree/)

검색속도와 다른 자료구조에 비해 상당히 빠른편. 한번의 이동으로 검색 횟수가 1/2가 됨.
**특징**
1. 각 노드의 왼쪽 subtree에는 해당 노드의 값보다 작은 값을 지닌 노드들로 이루어져 있다.
2. 각 노드의 오른쪽 subtree에는 해당 노드의 값보다 큰 값을 지닌 노드들로 이루어져 있다.
3. 중복된 노드가 없어야 한다.
4. 왼쪽 subtree, 오른쪽 subtree 또한 이진탐색트리이다.
