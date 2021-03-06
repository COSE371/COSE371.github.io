---
layout: page
title: "Assignment #3: E-R Modeling (~ 04/15)"
categories: old-assignment
math: true
permalink: /assignment3/
---

## E-R Modeling (~ 04/15)

---


다음 지시 사항들의 결과를 작성하시오.

- K 법률회사에서 이루어지는 업무를 관리하기 위한 데이터베이스를 설계하고자 한다. 이를 위한 **E-R diagram를 작성**하여라. (단, 아래 항목들을 포함하여야 함)
  - Entity Sets (primary key 지정해야 함)
  - Relationship Sets
  - Attributes
  - Cardinality Constraints & Participation Constraints (**모든 relation에 arrow notation + minimum & maximum notation 병기하여 작성할것**)

---

- 우리 회사(K 법률회사)는 교통위반, 국내분규, 민사소송, 살인 등 규모가 크고 다양한 종류의 업무들을 취급하는 법률회사이다. 우리 회사는 소송, 살인, 기타 부서로 이루어져 있으며 관리 목적에 따라 각 사건마다 특정부서로 할당된다. 
- 변호사는 특정부서에 소속되어 일을 한다. 우리는 사건의 각종 진행사항에 대한 정보를 필요로 하며 각 사건은 발생된 EVENT에 대한 일자, 개요와 함께 ID별로 관리되어야 한다. 사건들은 진행상황과 관련한 특수코드를 갖는데 예를 들면 시작은 1, 재판중은 2, 종료는 3으로 구분하며 각 사건에 대한 진행 상태를 알 수 있어야 한다.
- 우리는 사건이 어느 부서에 배정되었고 이 사건에 대한 간단한 개요를 포함하는 중요한 정보를 관리하고 싶다. 한 사건이 종료된 후 그것은 추후에 다시 계속될 지도 모른다. 재개된 사건에 대해서는 새 사건번호를 부여하지만  이전 사건과 연결될 수 있어야 한다. 
- 변호사들은 동시에 여러 개의 사건에 관여할 수 있으며 한 사건에는 여러 사람들이 관여될 수 있다. 우리는 특정 사건에 있어 사람들이 어떠한 역할 및 관계를 가지고 있는지 관리하고자 한다.  소송관계인은 이름, 생년월일과 유일한 번호에 의해 확인될 수 있어야 하며 사건에 관련된 사람은 판사, 목격자, 피고인, 변호사로 구분된다. 
- 우리는 이 네 유형의 사람의 정보를 알아야 하며 이 경우 변호비용 청구를 목적으로 변호사정보를 관리하지는 않는다. 


### 제출 및 채점 방법

---

- 제출기한
  - 정상제출: 4월 15일 14시까지 (채점결과의 **100%** 반영)
  - 지각제출: 4월 22일 14시까지 (채점결과의 **80%** 반영)
  - 최종제출: 4월 29일 14시까지 (채점결과의 **50%** 반영)


- 제출방법: [KULMS(블랙보드)](https://kulms.korea.ac.kr/) 에 파일 (**pdf**) 제출
  - 블랙보드 접속이 원할하지 않을 시, ws_choi@kore.ac.kr 로 보내주세요.

- 제출양식: pdf

- 채점방법
  - 요구사항과 관련된 다양한 해석이 존재할 수 있으나
  - 요구사항에서 명확하게 지시한 사항을 불이행하거나, 잘못 이행(arrow, minmax 노테이션 준수 등)할 때 마다 0.15점씩 감점

--- 

<a name = 'solution'>

## 모범답안

<div class="slide">
<iframe src="https://onedrive.live.com/embed?cid=7230FE4126F9D3CC&amp;resid=7230FE4126F9D3CC%214945&amp;authkey=ANLXYowjx7g7RP0&amp;em=2&amp;wdAr=1.7777777777777777" frameborder="0">포함된 <a target="_blank" href="https://office.com">Microsoft Office</a> 프레젠테이션, 제공: <a target="_blank" href="https://office.com/webapps">Office Online</a></iframe>
</div>
{% include dq.html %}
