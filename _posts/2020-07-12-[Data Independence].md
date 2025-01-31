---
    title : "데이터 독립성 "

    describe : "데이터 독립성이란? , 데이터 3단계 구조 , 스키마 , 인스턴스 , 스키마 뷰 , 파일 시스템" 
    categories : 
        ComputerScience

    tags :
        빅데이터

    toc : True

    toc_label : "목차"        

    last_modified_at : 2020-07-12

---
# 데이터의 독립성
## 3단계 구조 (3 - Level Architecture)
* 하위 단계의 데이터 구조가 변경되어도 상위단계에 영향을 미치게 하지 않게 하기위해 사용.
* 관점에 따라 3개의 계층으로 분리하여 복잡한 데이터베이스의 구조를 단순화 시킴
* 하나의 데이터베이스를 세 단계로 나누어 기쑬하는 것을 3단계 **데이터베이스 구조**라고 함.
## 3단계 스키마

|항목|정의|핵심|
|:---:|:---|:---:|
|외부 스키마  External Schema|View 단계 여러 개의 사용자 관점으로 사용자가 보는 개인적 DB 스키마|사용자 관점 접근하는 특성에 따른 스키마 구성|
|개념 스키마  Conceptual Schema|1. 개념 단계 하나의 개념적 스키마로 구성 , 모든 사용자 관점을 통합한 조직 전체의 DB 기술  2. 조직 전체의 DB를 기술한 것으로 DB에 저장되는 데이터와 그들간의 관계를 표현하는 스키마| 통합 관점|
|내부 스키마 Internal Schema|내부 단계 , 내부 쓰키마로 구성 , DB가 물리적으로 저장된 형식 으로 물리적 장치에 Data가 실제적으로 저장되는 방법을 표현하는 스키마.|물리적 저장구조|

## 데이터 독립성의 종류
1. 논리적 독립성 
* 목적 : 사용자 특성에 맞는 변경 가능 , 톡합 구조 변경 가능 을 실현시키기 위해
*  개념적 스키마가 변경되어도 외부 스키마에는 영향을 미치지 않도록 지원. 즉 논리적 구조가 변경되어도 응용 프로그램에 영향 없음.
<Br>
2. 물리적 독립성
* 목적 : 물리적 구조 영향 없이 개념구조 변경 가능, 개념구조  영향없이 물리적 구조 변경 가능
* 내부 스키마가 변경되어도 외부 외부/개념 스키마는 영향을 받지않도록함.

## 사상(Data mapping)
1. 논리적 사상 : 외부적 뷰와 개념적 뷰의 상호 관련성을 정의
* 예) 사용자가 접근하는 형식에 따라 다른타입의 필드를 가질 수 있음. 기념적 뷰의 필드타입은 변화가 없음.
2. 물리적 사상 : 개념ㅁ적 뷰와 저장된 데이터베이스의 상호 관련성 정의
* 예) 만약 저장된 데이터베이스 구조가 바뀐다면 개념적 / 내부적 사상이 바뀌어야함.그래야 개념적 스키마가 그대로 남아있게됨.

## 스키마 vs 인스턴스
|구분|스키마 (Schema) |인스턴스 (Instance) |
|:--|:--|:--|
|정의|1. DB에 저장되는 데이터 구조 및 유형을 정의<br>2. DB의 전체적인 정의를 나타내며 일반적으로 논리스키마 지칭.|1. DB에 저장되는 값들을 나타냄|
|특징|핳ㄴ번 정의도면 잘 변경되지 않음|계속적으로 변화하는 DB특성으로 인해 자주 변경됨|
|언어|DDL (Data Definition Langugae) |DML (Data Manipulation Langugae)|

## 스키마 뷰 (Schema View)
* 특정 테이블로부터 조건에 맞는 내용들을 추출하여 생성한 가상 테이블
* 뷰 생성시에 정의한 뷰의 스키마 내용만이 저자오디었다가 실행시 에 기본 테이블로부터 내용을 가져와 생성함.
### 스키마 뷰 기능
1. 단순화
  * 두개 이상의 테이블을 조인하여 테이블을 형성 , 검색 , 이용 , 갱신
2. 다양한 관점
* 통함된 데이터들을 하나의 형ㅎ식으로 저장
* 사용자에게 서로 다른 데이터 이름 및 형식으로 데이터 제공
3. 독립성
* 테이블의 구조가 변경되더라도 뷰의 구조는 변경될 필요 없ㅅ음
* 데이터의 논리적 독십성 제공
4. 데이터 보안
* 데이터에 대한 접근을 제한