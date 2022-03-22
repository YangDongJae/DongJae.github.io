---
title : [백준 9020] 파이썬으로 처음부터 이해하는 알고리즘

categories : Algorithm

description : 백준 9020에 대한 오류 흔적

toc : True

toc_label : "목차"

tags : 

last_modified_at : 2022-03-21
---

# 문제 

2보다 큰 짝수 n이 주어지면, n의 골드바흐 파티션을 출력하라

➥ 두 소수의 합이 n이 되는 소수들을 찾되, 합이 n이 되는 두 소수가 여러가지일 시 차이가 가장 작은 두 소수를 출력하라

# 조심해야할 점

* 시간 제한이 2초이다.

---

# 1차 시도

```python
def test(n):
    check_list = [True] * (n + 1)
    return_list = []

    for i in range (2, n):
        if check_list[i] == True:
            for j in range (i + i, n, i):
                check_list[j] = False

    prime_num = [i for i in range(2,len(check_list)) if check_list[i] == True]

    for k in prime_num:
        digit = n - k

        if digit in prime_num:
            return_list.append([k, digit])

    if len(return_list) % 2 == 0:
        return return_list[len(return_list)//2 - 1]
    else:
        return return_list[len(return_list)//2]

for i in range(int(input())):
    num = int(input())

    print(test(num)[0],test(num)[1])
```
## 흐름
1. 에라토스테네스의 체 구현을 통해 입력받은 숫자 n 까지의 소수들을 구해 리스트에 담는다.

2. 입력받은 n에서 위 1에서 구한 소수를 뺀 나머지 숫자 **digit** 를 구한다.

3. 만약에 **digit**이 첫번째 순서에서 구한 소수 리스트에 있다면 그 값을 리스트에 담는다.

4. 세번째 순서에서 구한 소수 리스트에서 차이가 가장 적은 값을 출력한다.(리스트 길이의 가운데 값)

## 오류
* 시간초과 : 이유는 잘 모르겠으나, 시간초과 발생

# 2차 시도

```python
sieve = [False, False] + [True] * 9999
count = int(10000 ** 0.5)

for i in range (2, count + 1):
    if sieve[i] == True:
        for j in range (i + i , 10000, i):
            sieve[j] = False

prime_number = [i for i in range (len(sieve)) if sieve[i] == True]

for _ in range (int(input())):
    number = int(input())

    a , b = number //2 , number //2

    while True:
        if a in prime_number and b in prime_number:
            print(a,b)
            break

        else:
            a -= 1
            b += 1
```

## 흐름
1. 에라토스테네스의 체 구현을 통해 입력받은 숫자 n 까지의 소수들을 구해 리스트에 담는다.

2. 입력받은 숫자를 2로 나눈다.

3. 입력받은 숫자에 대해 2로 나눈 값(중앙값) a,b가 소수 리스트에 있는지 확인한다.

4. 만약 리스트 안에 없다면, a는 -1을, b는 +1을 수행하여 반복한다.