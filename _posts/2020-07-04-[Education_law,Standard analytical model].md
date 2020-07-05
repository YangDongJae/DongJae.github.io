---
    title : "Law & Standard Analysis Model"

    categories : 
        2020 빅데이터 청년인턴    

    tags :
        2020 빅데이터 청년인턴

    toc : True

    toc_label : "목차"        

    last_modified_at : 2020-07-04

---

# What is Open Goverment Data?

데이터베이스 , 전자화된 파일 등 공공기관이 **법령 등에서 정하는 목적을 위하여** 생성 또는 취득하여 관리하고 있는 광 또는 전자적 방식으로 처리된 자료 또는 정보

## Tim berners lee Opean Data Charter 
1. Open by Default - 원칙적인 개방
2. Timely and Comprehensive - 적시성과 포괄성
3. Accessible and Usable - 접근성과 활용성
4. Comparable and Interoperable - 비교가능성과 상호운용성
5. For Imporved Governance and Citizen Egagement - governance( Top Down ) 과 시민참여 개선( 지향점 )
> Governance : 과거의 일방적인 정부 주도적 경향에서 벗어나 정부, 기업, 비정부기구 등 다양한 행위자가 공동의 관심사에 대한 네트워크를 구축하여 문제를 해결하는 새로운 국정운영의 방식’
 6. For Inclusive Development and Innovation - 개발과 혁신
 
 ## 대한민국 Open Goverment Data의 현재상황

 김대중 정부당시 전자정부정책으로인해 아날로그 데이터를 전자화로 옮기는 작업을 실시함. 덕분에 대한민국이 갖고있는 데이터의 량은 세계 Top 수준임.

</br>

OECD기준 OURdata index 2회여녹 1위
</br>Open Data Barometer 평가 4위 

### 전자정부 DATA 활용의 분류

1. G4C - Government for Citizen : 국민을 위한 전자정부 출범

2. G2G - Government to Government : 기관끼리의 전자결제 시스템 구축

3. G2B - Goverment to Business : 사업자 , 입찰사업 등

### 2020 Open 데이터 지향 방향

**데이터 기반의 행정**을 목표로 모든 행정절차를 데이터기반으로 전환중.

# Open Goverment Data 정책 & 주요사업

1. 기본계획 : 3년마다 실시하며, 어떻게 사업을 할 것 인지에 대한 내용
2. 시행계획 [평가지표] : 기본계획을 하달받은 각 기관에서 매년마다 KPI 목표 수립
3. 점검 [평가지표] : 법 제9조 공공데이터의 제공 운영실태 평가 & 법 제 10조 공공데이터의 이용 현황조사

## Open Goverment Data 정책 추진 경과
2020년 현재 진흥 정보 전략으로 진흥정보화 기본법 제정 : Open데이터 중심, 데이터의 질을 향상시키는 것에 대해 포커싱.

## Open Goverment Data 주요 사업 현황 ( SDLC , Life Cycle )


# law of Open Goverment Data
 
 ## Open Goverment data Quality Rank
  1. pdf - 문서형태의 데이터 
  2. XLS 
  3. CSV
  4. RDF
  5. LOD - 기계판독이 가능한 형태

  ## Open Goverment Data 사용시 유의사항
  * 공공데이터는 원칙적 개방을 기본으로함. 하지만 개방예외사항이 존재함
  * 데이터 개방으로하여금 제3자의 권리가 보장되지 아니할 경우 
    * Example) 도로별 범죄율 데이터를 공개하면 범죄율이 높개 측정된 도로의 상권은 망함.
  * 개인정보를 내포하고있는 경우
  * 공공기관이 제작한 데이터가 아닐경우
    * Example) 온라인에서 크롤링을 통해 얻은 데이터 기관에서 활용할 수 는 있지만, 공개할 수 없다.
    * 즉 공공기관이 수집한 데이터는 법령에의해 제작된것이 아니기때문에 공개할 수 없다.
  
  ## Open Goverment Data 제공절차 
  1. 이용자: 이용자의 데이터 신청 (방법 : 시행령 제 21조에 의거 , 서식 : 시행규칙 제 8조에 의거)
  2. 활용 지원 센터 : 즉시 소관기관에 이첩
  3. 공공기관의 장 : 제  17조 1항 정보 포함여부 검토 , 요청일부터 10일이내 제공여부 결정 or 기간 연장
  4. 공공기관의 장 : 제공결정시 신청인에게 통보 , 제 18조에 따른 공공데이터 목록 등록 or 제공 거부시 지체없이 거부결정의 내용과 사유를 신청인과 행안부장관에게 통보.

  ## Open Goverment Data의 활용

  ```python
Big Data(Volume , Variety , Variability , velocity , Value) 

        | |           | |           | |         | |
     Predictive    Real-Time      Insight    Agile Action
        | |           | |           | |         | |
        \./           \./           \./         \./

              Smart Decesion & Opttimization 
```
Predictive 는 과거 Reactive
RealTime은 과거 Batch 

  ### 빅데이터 활용 목적
  #### 공공기관 > 민간기관
  * 의사결정
  * 내부 프로세스/효율성 개선
  * 새로운 서비스 
  ---
  #### 공공기관 < 민간기관
  * 경영 효율화
  * 디지털 마케팅
  * 위험관리와 규제대응 (주로 금융권)

# 공공 빅데이터 업무활용 방법
## 업무 절차
1. 사전준비단계  
  * 추진체계 구성 : TF 팀 굿성
  * 빅데이터 분석과제 발굴 (데이터 확보 방안 , 분석과제 선정 , 과제의 이해 및 정의)
  * 계획 수립
2. 사업 추진단계 
  * 요건정의 -> 데이터 수집 -> 데이터 전처리 -> 분석 모델링 -> 모델 구현 -> 시각화 -> 검증 및 안정화
3. 활용 및 분석모델 고도화
* 업무 적용 효과 검증
* 사업결과 홍보
* 유지보수
* 분석모델 고도화
## 활용과제 도출 
### Biz Driven ( 기존 업무 중심)
* 기존 업무로부터 어떤 데이터를활용할지 추출하여 활용
### Policy Based (데이터 중심)
* 보유 데이터로부터 어떤 사업을 진행할지 추출하여 활용

## 공공 빅데이터 업무 활용 방법
! 결과보고서 작성 프로세스도 이와 유사함 결과보고서 작성시 1번 을 논리적으로 설득력있게 작성해야함.
1. 추진 목적 , 배경 , 방법 (Why , what , How에 기반한 Action Plan 수립.)
2. 관리 계획(How Management)
3. 홍보계획
4. 확산 계획
5. 성과 측정 계획