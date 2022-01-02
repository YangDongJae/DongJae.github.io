---
    title : "빅데이터 분석 방법론 "

    describe : "KDD , SEMMA , CRISP-DM" 
    categories : 
        ComputerScience

    tags :
        빅데이터

    toc : True

    toc_label : "목차"        

    last_modified_at : 2020-07-25

---
# 빅데이터 분석 방법론

| 종류 | 특징  | Process |
| :---------:|:---------:|:---------:|
| KDD | 데이터 중심 Insight 도출 | 2Selection -> Preprocessing -> Transformation -> Data modeling -> Interpretation/ Evaluation|
| SEMMA|문제의 정의 자체가 어려운 내용을 데이터 기반으로 문제 재정의 및 해결방안 탐색하여 개선|Sample -> Explore -> Modify -> Model -> Assess|
| CRISP - DM| 비지니스와 데이터 이해를 시작으로 6단계로 수행함.|  Business understanding -> Data understanding -> Data preparation -> Modeling -> Evaluation -> Deployment|

## KDD

필요 데이터 선택 or 생성 ➡️ 데이터 전처리 ➡️ Feature Engineering ➡️ 분석모델 적용 ➡️ 해석 및 평가

## SEMMA
데이터가 정말 많고, 그 데이터속에서 탐색을 해야하는 상황일 때 주로사용. (Bottom up 방식)

분석 데이터 추출 (garbage in garbage out 주의하여 적합한 데이터 추출) ➡️ 데이터 이해  및 비지니스 이해 , 데이터 내 이상치 제거 ➡️ 분석 대상 데이터 변환을 통한 데이터 정보 표현 극대화 ➡️ 모델 적용 ➡️ 모델 평가 및 검증 , 비교 및 추가 분석 여부 

## CRISP - DM
**해결해야하는 비지니스 문제로부터 데이터 관점의 분석문제로 변환** </br>
Example) 고객 이탈 증대 ➡️ 고객 이탈에 영향을 미치는 요인 식별 , 이탈 가능성 예측</br>

사용자 요구사항 이해 ➡️ 데이터 이해 , 데이터 내 문제점 식별 및 인사이트 도출 ➡️ 데이터 샘플링 ➡️ 모델 적용 ➡️ 모델 평가 ➡️ 실무계획 수립 , 프로젝트 종료