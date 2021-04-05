---
  title : "Epoch , Iteration , Dynamic Programming , 에포크 , 이터레션 , 다이나믹 프로그래밍이란?"

  describe : "Epoch , Iteration , Dynamic Programming , 에포크 , 이터레션 , 다이나믹 프로그래밍이란?"

  categories : 
      TECH

  toc : True

  toc_label: "목차"

  tags : 
    AI

  last_modified_at : 2020-08-26

  use_math: true
---
**한번의 계산으로 최적화된 값을 찾는 것은 상당히 힘듭니다. 머신러닝에서 최적화 (Optimization)를 할 때는 일반적으로 여러 번 학습 과정을 거치는데 한 번의 학습 과정 역시 사용하는 데이터를 나누는 방식으로 세분화 시킵니다.**



# Epoch 
**인공신경망에서 데이터 셋에 대해 한 번 학습을 완료한 상태** 즉 전체 데이터 셋에 대해 한 번의 학습 과정 완료되는 단위

> _One Epoch is when an ENTIRE dataset is passed forward and backward through the neural network only ONCE_ <br><br> _에포크 한번은 인공신경망에서 전체 데이터 셋에 대해 forward pass or backward pass 과정을 거친 것을 말합니다._

epochs = 30 는 전체 데이터를 30번 사용해서 학습을 거치는 것 입니다.

* **적절한 epoch값을 설정하면 underfitting 과 overfitting을 방지할 수 있다.**

* **epoch값이 너무 작다면 underfitting , 너무 크다면 overfitting이 발생할 확률이 높아짐**

# batch size
batch size는 한 번의 batch마다 주는 데이터 샘플의 size. 즉 나눠진 데이터 셋을 뜻함.

> _Total number of training examples present in a single batch._

# Iteration 
iteration는 epoch를 나누어서 실행하는 횟수임.

> _The number of passes to complete one epoch._

![]({{ site.url }}/assets/images/Reinforcement/Reonforcement_1.png    )

* 총 데이터가 100개 , batchsize가 20개 이다.

1. 1 iteration 은 5 개 데이터에 대해서 학습
2. 1 Epoch = 100 / batch size = 5 iteration

# Dynamic Programming

벨만이 최초로 적립한 개념이며, 작은 문제가 큰 문제 안에 중첩돼 있는 경우에 작은 문제의 답을 다른 작은 문제에서 이용함으로써 효율적으로 계산하는 방법.

> Dynamic Progoramming : 대상이 시간에 따라 변화(Dynamic) + 계산을 통해 프로세스가 다단계로 이루어지는 것(Programming) <br>
즉 시간에 따라 다른 프로세스들을 풀어나감.