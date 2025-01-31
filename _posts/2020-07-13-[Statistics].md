---
    title : "데이터 분석 통계 "

    describe : "데이터 분석에 필요한 통계지식" 
    categories : 
        ComputerScience

    tags :
        빅데이터

    toc : True

    toc_label : "목차"        

    last_modified_at : 2020-07-12

---

# 데이터 분석의 유형

### 기술적 데이터 분석 (Descriptive Data Analysis)
  - 주어진 데이터요약 / 집계하여 현재 모습을 묘사 / 기술하는것을 목표로함
  - 단순 계산 및 집계에 의한 팩트를 전달

### 탐색적 데이터 분석 (Exploratory Data Analysis)
  - 여러 변수 간의 관계 , 패턴 , 트랜드 등을 찾는다
  - 데이터 분석 초기에 가설 수립에 유용하다
  - 그래프를 통한 사실 확인이 주된 분석 작업

### 확증적 데이터 분석 (Confirmatory Data Analysis)
 - 도출된 가설을 겆믕한다. 주로 p-value를 기준으로 의사결정을 한다
 - 샘플에서 구한 통계량은 모집단에도 적용할 수 있는 지 검토하는 분석 유형
### 예측적 데이터 분석 ( Predictive Data Analysis)
  - 발생하지 않은 어떤 사건에 대한 예측이 주요 목표이다. 머신러닝 , 딥러닝 , Decesion Tree등 다양한 모델링 기법에 사용.

## 정형데이터의 종류

1. 수치데이터 
  * 연속형 데이터
  * 이산형 데이터

2. 범주형 데이터
  * 비순서형 범주 데이터 : 도시명 , 참 / 거짓 등
  * 순서형 범주데이터 : 평점 등

## 테이블 데이터
  * 데이터 분석에 가장 대표적으로 사용되는 형태
  * 엑셀 , 스프레드시트나 데이터베이스의 테이블과 같은 테이블 데이터

  Ex)

  |날짜|시간|금액|
  |:--:|:--:|:--:|
  |1/1|15:00|2,300|
  |2/1|15:00|23,000|
  |3/1|16:00|500|