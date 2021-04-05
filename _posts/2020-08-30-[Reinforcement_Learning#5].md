---
  title : "강화학습 정책 이터레이션이란?"

  describe : "강화학습 정책 이터레이션이란? Policy iteration , Policy Evaluation , Policty Improvement"

  categories : 
      TECH

  toc : True

  toc_label: "목차"

  tags : 
    AI

  last_modified_at : 2020-08-30

  use_math: true
---
# 정책이란?

> 정책(policy)는 에이전트가 모든 상태에서 어떻게 행동할지에 대한 정보

우리의 목적은 최적 정책을 찾는 것. 그러기 위해서 현재 정책을 **평가** 하고, 더 나은 정책으로 **발전** 해야함.<br>

# 정책 이터레이션 

* 위에서 이야기한 **평가**를 정책 이터레이션(Policy iteration)에서는 **_정책평가 (Policy Evaluation)_**이라고 함

* 위에서 이야기한 **발전**을 정책 이터레이션(Policy iteration)에서는 **_정책 발전(Policy Improvement)_**이라고 함.

> Quation Point <br> 그렇다면 언제까지 정책을 평가하고 발전시키는가?

## 정책평가(Polict Evaluation)

* [가치함수](https://yangdongjae.github.io/ai/Reinforcement_Learning-2/)는 정책이 얼마나 좋은지 판단하는 근거가 됨

> 가치함수는 현재의 정책 $\pi$를 따라갔을 때 받을 보상에 대한 기대값

* 현재 정책에 따라 받을 보상에 대한 정보가 **정책의 가치가 됨**

> 정책에 대한 평가의 기준이 되는 가치함수 <br> $v_\pi(s) = E_\pi[R_{t + 1} + \gamma R_{t + 2} + \gamma^2 R_{t + 3} ... \mid S_t = s]$

위 수식은 t가 늘어날수록 일어날 수 있는 경우의 수가 기하급수적으로 늘어나기 때문에, 가치함수를 계산하기 어려움 ➡️ Dynamic Programming을 통해 벨만 기대방정식을 사용

> Dynamic Programming을 적용한 가치함수의 계산 <br>
$v_\pi(s) = E_\pi[R_{t+1} + \gamma v_\pi(S_{t + 1}) \mid S_t = s]$
 <br> <br> 
 컴퓨터가 게산할 수 있게 확률(대문자 알파벳)을 합의 형태로 변경 <br> 
 $v_\pi (s) = \displaystyle \sum_{a \in A} \pi(a \mid s)(r_{(s,a)} + \gamma v_\pi(s'))$

## 정책평가 과정

1. $k$번째 가치함수 행렬에서 현재 상태 $s$에서 갈 수 있는 다음 상태 $s'$ 에 저장돼 있는 가치함수 $v_k(s')$를 불러온다

2. $v_k(s')$에 할인율 $\gamma$를 곱하고 그 상태로 가는 행동에 대한 보상 $R^a_s$를 더한다
<br>
$r(s,a) + \gamma v_k(s')${:align}

3. 2번에서 구한 값에 그 행동을 할 확률, 즉 정책 값을 곱한다<br>
$ \pi (a \mid s) (r(s,a) + \gamma v_k(s'))$

4. 3번에 모든 선택 가능한 행동에 대해 반복하고 그 값들을 더한다<br>
$\displaystyle \sum_{a \in A} \pi (a \mid s) (r_{(s , a)} + \gamma v_k(s'))$
5. 4번 과정을 통해 더한 값을 $k + 1$번째 가치함수 행렬에 상태 $s$ 자리에 저장한다.

6. 1-5 과정을 모든 $s \in S $에 대해 반복한다.

**⚠️ 위 방법을 통해 제데로 정책에 대한 평가를 할 수 없음. 그래서 위 과정을 여러번 박복하는데, $v_1$로 시작해서 무한히 반복하면 참 $v_\pi$가 될 수 있음**

## 탐욕 정책 발전(Greedy Policy Improvement)
정책 발전(Policy improvement)의 방법은 정해져 있는것이 아님

> 탐욕 정책 발전 (Greedy Policy Improvement) <br> 상태 $s$에서 선택 가능한 행동의 $q_\pi(s,a)$를 비교하고 그중에서 가장 큰 큐함슈를 가지는 행동을 선택

Q함수를 통해 어떤 행동이 좋은지를 확인 함
> Q 함수<br> $q_\pi(s,a) = E_\pi[R_{t + 1} + \gamma v_\pi (S_t + 1) \mid S_t = s , A_t = a]$<br> **$s'$는 행동$a$를 통해 도달하게 되는 상태를 의미함** <br><br> 컴퓨터가 게산할 수 있게 확률(대문자 알파벳)을 합의 형태로 변경<br> $q_\pi(s,a) = r_(s,a) + \gamma v_\pi(s')$ <br><br> 탐욕 정책 발전(Greedy Policy Improvement)으로 얻은 새로운 정책<br>$\pi'(s) = argmax_{a \in A}q_\pi(s,a)$

> Question point <br> 만약에 $argmax$를 통해 나온 가치함수가 2개 이상이면 학습은 어떤 방식으로 이루워지는가?
<br>

[정책 이터레이션 코드 해석](https://yangdongjae.github.io/ai/Reinforcement_Learning-6/)
