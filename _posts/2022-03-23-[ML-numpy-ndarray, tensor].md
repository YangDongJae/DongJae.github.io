---
title : 밑바닥에서 시작하는 Numpy 이해

categories : ComputerScience

description : import numpy as np만 하는 초심자도 이해하는 밑바닥 Numpy [Numpy 배열(ndarray)과 텐서(tensor)]

toc : True

toc_label : "목차"

tags : 

last_modified_at : 2022-03-18
---
# Numpy

## Numpy 배열(ndarray)과 텐서(tensor)
* ndarray : 텐서 데이터를 다루는 객체입니다.
* tensor : 선형대수의 데이터 배열(array)입니다.
* * 랭크(rank)에 따라 이름이 다릅니다.

![]({{ site.url }}/assets/images/Numpy/rank.png  )

## Numpy 배열(ndarray)의 메모리 구조
* 배열 생성은 **np.array()**함수를 사용하여 진행합니다.

```python
import numpy as np

np.array(a,b)
```
* np.array()함수의 기본적인 구조입니다. a라는 곳 에는 배열 정보가 입력되어야 합니다.

* b라는 곳 에는 Numpy 배열로 표현하려는 데이터 타입이 입력되어야 합니다.

```python
import numpy as np

test_array = np.array([1,4,5,8],float)
```

## Python list와의 차이점
* Numpy배열은 텐서의 구조에 맞춰 배열을 생성해야 합니다.
* * m x n 배열을 생성한다면, 이 행렬의 모든 엔트리(entry)는 데이터로 채워져야 합니다.
* * 반면에 리스트의 경우 데이터를 일부 채우지않아도 무리없이 작동합니다.

```python 
import numpmy as np

test_list = [[1,4,5,8],
             [1,4,5]]

np.array(test_list, float)
# Value Error
```
위 코드를 보면, test_list의 1행은 4개의 데이터가, 2행에는 3개의 데이터가 있습니다. **다시말해 2행 4열에 한개의 값이 비어있는 상태입니다.**<br>

이는 위에서 이야기한 **"행렬의 모든 엔트리는 데이터로 채워져야 함**에 맞지 않기 때문에, 에러를 발생시킵니다.