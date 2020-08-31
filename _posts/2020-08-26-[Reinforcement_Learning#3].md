---
  title : "벨만 기대 방정식"

  describe : "벨만 기대 방정식 , 파이썬과 케라스로 배우는 강화학습"

  categories : 
      AI

  toc : True

  toc_label: "목차"

  tags : 
    AI
    강화학습

  last_modified_at : 2020-08-26

  use_math: true
---

# 벨만 방정식
## 벨만 기대방정식
$v_\pi(s) = E_\pi[R_{t + 1} + \gamma v_\pi(S_{t+1})|S_t=s]$<br>

현재 상태의 가치함수와 다음 상태의 가치함수 사이의 관계
> s상태일 때 가치함수는 다음 타임 스텝의 보상과 다음 타임스텝에 할인률을 적용한 가치함수

## 계산가능한 벨만 방정식
$v_\pi(s) = \displaystyle\sum_{a \in A} \pi(a|s)(r(s,a) + \gamma \sum_{s' \in S} P^a_{ss'}v_{\pi}(s'))$

<br>

**모든행동에 대한 정책 * (상태와 행동에 대한 보상 + ( 상태 s에서 행동 a를 통해 상태s'으로 갈 확률 * 다음 행동에 대한 가치함수 ))**

## 최적 정책 

$\pi \ast (s,a) = \left \{ \begin{array}{cc} 1 \space if a = argmax_{a\in A} q\ast(s,a) \\ 0 \space otherwise \end{array} \right \}$<br>

argmax 는 $q\ast$를 최대로 해주는 행동 a를 반환함.

## 최적의 가치함수
$v\ast(s) = \displaystyle\max_a[v_\pi(s)]$

## 최적의 큐함수
$q \ast (s,a) = \displaystyle \max_\pi[q_\pi(s,a)]$

# 벨만의 최적방정식

$v\ast (s) = \max_aE[R_{t+1} + \gamma v \ast (S_{t+1}) \mid S_t = s , A_t = a]$

더 좋은 정책을 찾아가다보면 최적의 정책을 찾을 수 있음. 최적의 정책은 최적의 가치함수를 받게하는 정책이며, 가치함수 사이의 관계식이 벨만 최적 방정식임.