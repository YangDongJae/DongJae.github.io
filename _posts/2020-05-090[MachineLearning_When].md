---
    title : "[데이터 사이언스] 언제 머신러닝을 사용할까?"

    description : "머신러닝 , Feature Selection, Cross validation , Confusion matrix"

    toc : True

    tags :
        머신러닝
        데이터사이언스

    last_modified_at : 2020-05-09
---

# 머신러닝을 활용하는 경우
1. 패턴을 도출해낼 수 있을 때
2. 수식화 할 수 없을 때
3. 데이터를 갖고 있을 때

# 머신러닝 학습의 구성요소
1. Unknown Target Function
* 정확한 결과값을 도출할 수 있는 함수는 오직 신만이 알고있다. 우리는 100% 맞는 결과값을 도출하는 함수를 절대 알 수 없다.
2. Training Data
* 우리의 데이터는 수많은 벡터와 한가지 스칼라로 이루어져있다.
3. Hypothesis set
* 우리는 무한대에 가까운 가설집합들중 하나를 택일해 학습데이터에 적용시켜 학습 알고리즘으로 활용한다.
4. Learning Algorithm
* 무한대에 가까운 가설집합중 한가지를 학습 데이터에 적용시킨따.
5. Final hypothesis
* 최종가설은 절대 g = f 가 될 수 없다. 근본적인 이유는 unknown target function 에 있다. Final Hypothesis는 오로지 근사한 값만 갖는다. 
