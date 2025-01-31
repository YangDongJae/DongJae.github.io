---
    title : "[데이터 사이언스] Decesion Tree_결정트리"

    description : "머신러닝 결정트리 러닝 알고리즘 , Decesion Tree , 엔트로피 , Entopy"

    categories : 
        ComputerScience

    toc : True

    tags :
        머신러닝

    last_modified_at : 2020-05-09
---
# Decision Tree Learning Algorithm 

머신러닝 기법에는 수많은 학습알고리즘이 존재한다. 그리고 다양한 러닝 알고리즘은 크게 두가지로 나뉜다. classifier , Regression이다. Decesion Tree는 Classifier 즉 분류를 위한 학습 알고리즘으로, 하나의 선형을 찾아 True, False값을 찾는 학습 알고리즘이다.

## Information Quantification

### Information Theory slogan

>**특정 이벤트가 낮은 빈도로 발생할수록, 이벤트가 갖는 정보의 양은 크다.**<br/>
이는 정보이론의 대표적인 슬로건이다. 이 슬로건에 대해서 한번 생각해보자. 


* 3차세계대전 vs 내친구의 전역

 3차 세계대전이 발발했다고 생각해보자. 세계 3차대전이 발발하는 순간 전세계의 모든 매체가 그 정보에 관하여 보도할 것이며, 유튜브, 뉴스, 기사 등 모든 언론 및 커뮤니티 매체에서 이에관한 정보(기사, 영상 , 뉴스 등)을/를 만들 것 이다.<br/><br/>
하지만 내 동내친구가 4개월뒤 전역한다고 생각해보자. 세계 3차대전에 비해 정보의 량도, 그 정보를 아는사람도 전역하는 친구의 주위 사람에 불과할 것이다. 

> 즉 엄청 극악의 확률로 발생할 3차 세계대전 과 대한민국 대다수의 남자가 경험하는 군 전역은 각각 갖는 정보의 양이 다르며, 이는 특정 이벤트가 발생할 확률과 반비례한다.  

* 특정 이벤트가 발생할 확률을 P(e)라고 해보자. 그렇다면 특정 이벤트가 갖는 정보의 양은 어떻게 찾을 수 있을까?
우리는 -log 함수 그래프를 활용해 찾을 수 있다. -log 함수의 특징은 x값(특정 이벤트가 일어날 확률) 이 적을수록 y값(특정 이벤트가 갖는 정보의량) 이 증가한다. <br/>

**이는 Information Theory slogan 과 동일한 구조임을 알 수 있다.**<br/>
그렇기 때문에 특정 이벤트 e가 갖는 정보의 양은 -log P(e) 이다.

**특정 이벤트 e로부터 기대할 수 있는 정보의 양**
우리는 이제 특정 이벤트 e가 일어날 확률과 그 확률의 정보의 양에 대해서 알고있다. 그렇다면 이 두가지를 곱하면 이벤트 e로부터 기대할 수 있는 정보의 양이 만들어진다.
## Entropy

Entropy란 변수가 갖는 불확실성이다. 우리는 위에서 특정 이벤트 E가 갖는 정보의양이 -log P(e)라는걸 살펴보았다. 이제 특정 이벤트E가 아닌 변수 v 라고 생각해보자.<br/><br/>

![]({{ site.url }}/assets/images/machineLearning/entropy.png)<br/>
Entropy를 구하는 공식이다. **절대 수식이 나왔다고 겁먹지 말고 한번 저 수식을 분해해보자!!**<br/>
자세히 보면 우리가 아까 살펴본 이벤트 e 로부터 기대할 수 있는 정보의 양 **P(e) * -Log P(e)**를 반복하면서 더할 뿐이다.

<br/><br/>
### Entropy의 이해

우리는 엔트로피가 특정 변수가 갖는 불확실성에 대한 식이고, 이는 특정 변수가 갖는 정보의 량의 합이라는걸 위에서 알았다. 그렇다면 예시를 보며 그 이해를 확실히 해보자.<br/>
<br/>
**주사위 던지기 Entropy**<br/>
H(주사위 던지기)  = (주사위가 던졌을때 1이 나올 확률 * 주사위가 던졌을때 1이 나올 확률의 정보의 량) + ... + (주사위가 던졌을때 6이 나올 확률 * 주사위가 던졌을때 6이 나올 확률의 정보의 량)
<br/>
즉 H(주사위 던지기) = (1/6 * -log 1/6 ) 을 6번 반복하면된다. 한가지 경우만 추가로살펴보자
<br/>
<br/>
**이상한 주사위 던지기 Entropy**<br/>
이 주사위는 면이 6개이지만 1개의 면엔는 1이 2개의 면에는 3이 3개의 면에는 5가 그려져있다. 이경우의 Entrophy또한 구해보자.
<br/>
H(이상한 주사위 던지기) = (주사위가 던져졌을때 1이 나올 확률 * 주사위가 던졌을때 1이 나올 확률의 정보의 량) + (주사위가 던져졌을때 3이 나올 확률 * 주사위가 던졌을때 3이 나올 확률의 정보의 량) + (주사위가 던져졌을때 5가 나올 확률 * 주사위가 던졌을때 5가 나올 확률의 정보의 량)
<br/>
즉 H(이상한 주사위 던지기) = (1 / 6 * -log 1/6) + (2 / 6 * -log 2/6) + (3 / 6 * -log 3/6)  이 된다. 

<br/>**결론**<br/>
>즉 Entropy의 값이 0이된다면, 일관적인 답이 또출이 된다. 주사위를 던져도 언제나 1이 나온다는 의미이다. 그런 주사위는의 Entropy는 0이다!

## Entropy를 활용한 Decision Tree 학습 알고리즘
위에서 우리는 결정트리를 활용하기 위해 information theory slogan 을 활용하여  -log 함수 그래프를 도출하고, -log 함수를 통해서 특정 이벤트 E가 갖는 이벤트의 양 -log P (e) 를 도출하고, 이를통해 Entropy를 찾는 방법을 찾았다. 이제 Entropy를 활용하여 결정트리가 어떻게 동작하는지에 대해서 알아보자.

### information gain
information gain(정보의 이득) = H(v0) - H(v1) (초기 상태의 Entropy) - (Feature 기반의 Entropy) 즉 우리각 구하고자 하는 데이터들으 초기상태에 Entropy 와 특정 기준으로 나누어 도출한 Entropy값을 빼주면 Information gain 즉 정보의 이득을 산출할 수 있다.

<br/>**우리는 information gain을 통해서 Decesion Tree를 동작하게 할 수 있다.**

### Information gain을 활용한 Decision Tree의 구동원리
결정트리는 Information gain의 값이 큰 특징들을 순차적으로 트리의 밑으로 붙이는 과정이다. 



