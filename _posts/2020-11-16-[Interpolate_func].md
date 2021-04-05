---
    title : "보간법(interpolation)과 numpy interpolate 함수"
    describe : "데이터 분석에 필요한 지식 보간법 interpolate, interolate in numpy" 
    categories : 
        TECH   

    tags :
        빅데이터

    toc : True

    toc_label : "목차"        

    last_modified_at : 2020-07-12

---
# 보간법이란?
보간법(interpolation)이란 통계적 혹은 실험적으로 구해진 데이터들(xi)로부터, 주어진 데이터를 만족하는 근사 함수(f(x))를 구하고,  이 식을 이용하여 주어진 변수에 대한 함수 값을 구하는 일련의 과정을 의미합니다. 예를 들어, (0, 0), (1, 10), (2, 20)이 주어졌을 때, 이들에 대한 근사 함수를 f(x) = 10x로 구하고, 1.5에 대한 함수 값으로 15를 구하는 것입니다.

> 예를 들어, (0, 0), (1, 20), (2, 40)이 주어졌을 때, 이들에 대한 근사 함수를 f(x) = 20x로 구하고, 1.5에 대한 함수 값으로 30을 구하는 것

```python
from scipy.interpolate import interp1d
import numpy as np

x = np.linspace(0, 10, num = 11 , endpoint = True)
y = np.cos(-x**2/9.0)
y = interp1d(x,y)
f2 = interp1d(x,y,kind = 'cubic')

xnew = np.linspace(0,10, num = 31 , endpoint = True)

#visualization
import matplotlib.pyplot as plt

plt.plot(x, y, 'o', xnew, f(xnew),'-', xnew, f2(xnew), '--')
plt.legend(['data','linear','cubic'], loc = 'best')
plt.show()
```