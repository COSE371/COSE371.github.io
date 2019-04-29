---
layout: post
title: "Term Project"
categories: term-project
math: true
permallink: tp2019
---

<div class="slide">
<iframe src="https://onedrive.live.com/embed?cid=7230FE4126F9D3CC&amp;resid=7230FE4126F9D3CC%214852&amp;authkey=AOc0ZTftCugVcUo&amp;em=2&amp;wdAr=0.6923076923076923" frameborder="0">포함된 <a target="_blank" href="https://office.com">Microsoft Office</a> 프레젠테이션, 제공: <a target="_blank" href="https://office.com/webapps">Office Online</a></iframe>
</div>


---


### 목표​

- 특정 업무를 지원하는 웹기반 데이터베이스 응용 시스템을 개발하는 것을 목적으로 함​
- 특정 업무는 본인이 임의로 선정하되 가상의 업무를 고안하여 개발하는 것도 가능함​
- 업무 규모는 개념적 설계 결과 기준으로 엔터티 세트 5개 이상, 기능 또는 프로세스 6개 이상이어야 한다.​


### 수행 내역​

- 업무의 요구사항 분석 및 개념적 설계 (DB, Functions & Processes)​: 요구사항 분석 및 개념적 설계 단계의 산출물은 아래와 같다​ (산출물 양식은 첨부한 양식을 참고함.)​
  - 업무개요서​
  - 기능분해도 및 기능 설명서​
  - 기능별 요구사항 명세서​
  - E-R diagram​
  - 프로세스 계층도 및 프로세스 설명서 ​

- 논리적 설계 (DB, Modules)​: 논리적 설계 단계의 산출물은 아래와 같다(산출물 양식은 첨부한 양식을 참고)​
  - 릴레이션 정의서​
  - 모듈 명세서​

- 시스템 구현​: 시스템 구현 단계의 산출물은 DB 구현 내역과 소스 코드를 말하며 DB 구현 내역은 각 테이블에 대한 스키마 정보 및 테이블 내의 샘플 데이터를 출력하여 문서로 작성함. (DB 구현 내역서, 소스 코드 요약 설명서)​
  - 구현되는 시스템은 핵심 데이터의 삽입, 수정, 삭제, 검색 기능이 반드시 포함되어져야 한다. 상품 판매(구매) 기능을 예로 들어, 일반 사용자들이 상품 정보를 검색하여 구매하는 경우, 구매정보 삽입, 수정 삭제 기능을 구현해야 한다. ​
  - 특정 정보의 검색 결과는 두 단계(검색 결과 전체에 대한 간략정보 & 특정 검색 결과에 대한 상세정보)로 볼 수 있도록 구현해야 함. ​
  - 구현되는 기능에서 필요한 정보이지만 시스템 구현 범위 내에  해당 데이터 생성(insert) 기능이 포함되어 있지 않는 경우 해당 테이블의 데이터는 MariaDB에서 직접 생성하여 사용.​
  - 시스템 구현 시 둘 이상의 테이블이 조인되어 처리되어야 하는 기능이 반드시 포함되어야 함.​
  - 웹 페이지 디자인은 http://www.oswd.org 에서 구현 시스템에 적합한 디자인을 다운로드한 후 변경하여 사용할 수 있음
  

### 배점 및 제출기한

#### 1. Development of Web DB application with no transaction [배점 7]

- 제출내용
   - Requirements Analysis
   - Design and Implementation
   - Report Submit 
- 제출기한
   - 정상제출: 5월 27일 14시까지 (채점결과의 **100%** 반영)
   - 지각제출: 6월 03일 14시까지 (채점결과의 **80%** 반영)
   - 최종제출: 6월 10일 14시까지 (채점결과의 **50%** 반영)


#### 2. Development of Web DB application with transaction/CC/Recovery [배점 2] 

- 제출 내용
  - System Refinement
  - Report Submit 
- 제출기한
   - 정상제출: 6월 10일 14시까지 (채점결과의 **100%** 반영)
   - 지각제출: 6월 17일 14시까지 (채점결과의 **80%** 반영)
   - **최종제출: 6월 23일 23시 59분까지 (채점결과의 50% 반영)**

### 제출방법

- 보고서 파일을 KULMS에 제출

### 2018학년도 1학기 모범사례

- [고려대학교 음악 정보 사이트(김영훈)](https://cose371.github.io/tp2018case/)

### 참고자료

- [Codiad 사용법](https://cose371.github.io/codiadinstallationtutorial/)
- ERD 그리는 사이트
  - [Lucid Chart](https://www.lucidchart.com/) : [예시](https://www.lucidchart.com/invitations/accept/ab6dfb27-f3cd-412a-a9de-f919cdf15610)
  - [Vertabelo](https://www.vertabelo.com/): [예시](https://my.vertabelo.com/public-model-view/KKHmcf48F1LEF65bzFSnl4aj0SW0f7yvJw9sdHTnKOgjQNP2liUa9xQpPdd85Xl3?x=2040&y=2658&zoom=0.4786)
  
  <div class="slide">
  <script>if (typeof VertabeloEmbededObject === 'undefined') {var VertabeloEmbededObject = "loading";var s=document.createElement("script");s.setAttribute("type","text/javascript");s.setAttribute("src", "https://my.vertabelo.com/js/public-model/v1/api.js");(document.getElementsByTagName("head")[0] || document.documentElement ).appendChild(s);}</script><div class="vertabelo-public-model" data-height="400" data-width="640" data-logoType="created_with" data-modelGid="KKHmcf48F1LEF65bzFSnl4aj0SW0f7yvJw9sdHTnKOgjQNP2liUa9xQpPdd85Xl3" data-openLabel="EDIT MODEL IN YOUR BROWSER" data-x="4263" data-y="5554" data-zoom="0.4786" ></div>
  </div>