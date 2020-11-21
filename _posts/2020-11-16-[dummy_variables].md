---
    title : " 가변변수 Dummy Variable, one hot encoding "

    describe : "데이터 분석에 필요한 지식 범주형 변수 인코딩 방법 Dummy Variable 과 one hot encoding의 차이점" 
    categories : 
        빅데이터   

    tags :
        빅데이터

    toc : True

    toc_label : "목차"        

    last_modified_at : 2020-07-12

---
# 가변수란 ?
> 가변수(Dummy variable, 假變數)란 독립변수를 0과1로 변환한 변수를 의미한다.

일반적인 경우 그 사실 여부에 대해 예/아니오로 확인 가능한 질적 변수(예: 남자인가? 대학교를 졸업했는가?)는 회귀 분석에 직접 투입하는 것이 불가능하다. 이러한 질적 변수를 회귀분석에 사용하기 위해 그 가부를 0 혹은 1 의 숫자 형태로 대응시킨 변수를 가변수라 한다.

* 즉 One hot Encoding과 같은형태로 생각하면 된다.

# 범주형 변수를 인코딩 하는 두가지 방법

## one hot encoding
날씨라는 범주형 변수에 맑음 흐림 비 눈 4가지가 있다고 생각해보자.

여기서 one hot encoding을 사용하면, 우리는 4개의 변수로 변환을 할 것입니다.

! intercept가 일으키는 공선성 문제에 대하여 추가조사 필요 함

## dummy encoding

날씨라는 범주형 변수에 맑음 흐림 비 눈 4가지가 있다고 생각해보자.

여기서 dummy인코딩을 사용하면, 우리는 4-1인 3개의 변수로 변환을 할 것입니다.

