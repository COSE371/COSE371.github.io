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

### 과제 상세정보 및 제출양식

- MS office 사용자: [pptx 다운로드](https://drive.google.com/open?id=12qD-9mfxYmNl9TkmKz1DyPv_C40J-pIq) 
- Powerpoint가 없는 경우: [링크 접속](https://drive.google.com/open?id=12qD-9mfxYmNl9TkmKz1DyPv_C40J-pIq)  -> 구글 로그인 -> 내 드라이브에 추가 -> Google 프리젠테이션으로 열기

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

- [고려대학교 음악 정보 사이트(김영훈)](https://cose371.github.io/tp2018case)

### 참고자료

- [Codiad 사용법](https://cose371.github.io/codiadinstallationtutorial/)
- ERD 그리는 사이트
  - [Lucid Chart](https://www.lucidchart.com/) : [예시](https://www.lucidchart.com/invitations/accept/ab6dfb27-f3cd-412a-a9de-f919cdf15610)
  - [Vertabelo](https://www.vertabelo.com/): [예시](https://my.vertabelo.com/public-model-view/KKHmcf48F1LEF65bzFSnl4aj0SW0f7yvJw9sdHTnKOgjQNP2liUa9xQpPdd85Xl3?x=2040&y=2658&zoom=0.4786)
  
  <div class="slide">
  <script>if (typeof VertabeloEmbededObject === 'undefined') {var VertabeloEmbededObject = "loading";var s=document.createElement("script");s.setAttribute("type","text/javascript");s.setAttribute("src", "https://my.vertabelo.com/js/public-model/v1/api.js");(document.getElementsByTagName("head")[0] || document.documentElement ).appendChild(s);}</script><div class="vertabelo-public-model" data-height="400" data-width="640" data-logoType="created_with" data-modelGid="KKHmcf48F1LEF65bzFSnl4aj0SW0f7yvJw9sdHTnKOgjQNP2liUa9xQpPdd85Xl3" data-openLabel="EDIT MODEL IN YOUR BROWSER" data-x="4263" data-y="5554" data-zoom="0.4786" ></div>
  </div>

---
### Q & A

#### 과제 관련

- Term Project 구현할 때 ORM 사용해도 되나요? 아니면 반드시 SQL raw query를 사용해야 하나요?

> 됩니다. 하지만 가급적 SQL raw query로 합시다!

- 몰라요

> 이거 질문이 뭐였죠?

- "구현되는 기능에서 필요한 정보이지만 시스템 구현 범위 내에 해당 데이터 생성(insert) 기능이 포함되어 있지 않는 경우 해당 테이블의 데이터는 MariaDB에서 직접 생성하여 사용" 의미가 이해가 가지 않아요

- 텀프로젝트는 mall 디렉토리가 아니라 project 디렉토리에서 작업하면 되나요?

> 만약 codiad 안쓰고 ssh 로만 작업하실 경우는 project 디렉토리에서 작업하시면 됩니다.


- 텀프 기한 좀 늘려주세요ㅠ

- 아직 시작 안했는데, 몇일만에 가능할까요?

- 그럼 OOO모음 사이트는 다 안되는건가요? 모범사례랑 겹쳐서요 ㅠㅠ
  
- 과제 보고서 너무 많아요
  
---

#### PHP 관련

- 교수님이 값을 바꾸니까 제 페이지에서 정보가 바꼈는데, 왜그런가요?

- include는 해당 내용을 단순히 복붙하는 효과인가요?

- 두가지 다 상관없나요?

```php
<input type="hidden" name="product_id" value="<?=$product['product_id']?>"/> <? echo "<input type='hidden' name="product_id" value='{$product['product_id']}'/>" ?> 
```

- 이런식으로 input 태그만 끝에 /가 있는 이유가 있나요?

```php
<input readonly type="text" id="manufacturer_id" name="manufacturer_id" value="<?= $product['manufacturer_id'] ?>"/> 
```

- 아까 foreach 문에서 if else문에 selected 있고 없고 차이가 뭔가요?

```php
echo "<option value='{$id}' selected>{$name}</option>"; 랑 echo "<option value='{$id}'>{$name}</option>"; 
```

- form에서 post 로 보내지는 변수 이름은 input tag들의 id 로 들어가나요 name으로 들어가나요?

- 변수앞에있는 \$는 무엇을 의미하나요?

- mysqli_query 부분 한번만 더 설명부탁드립니다!

- 아까 form코드에서 ```<?php echo $action > ??``` 이부분 코드 다시 보여줄수있나요ㅠㅠ?

- case insensitive하게 검색하는 게 like operator을 쓰면 자동으로 되나요?

- php 뒤에 ?는 무슨의미인가요?

- 새로운 php파일을 만드는 기준은 뭔가요??
  
> 피...필요할 때?

--- 

### Codiad 관련

- codiad에서 만든 파일을 다른 디렉토리로 move 못하나요?

- codiad에서 index.php 만든거 어떻게 웹페이지로 띄워서 볼 수 있나요 ?

- CODIAD엔 MP3파일 못 넣나요??? 계속 넣어봤는데 분명 COMPLETE이라고 뜨는데 안 들어가있어요ㅠㅠ

- 저희가 만든 index.php 는 (http://115.68.231.165/자기학번) 에서 확인이 가능한데, 처음 codiad들어가서 있는 mynameis.php나 mynameis_post.php 같은 파일은 어떻게 확인할 수 있나요?

- 주석처리 하는 방법 다시 한번만 설명해주세요!!ㅠ

> 블록잡고 ```ctrl + /``` 또는 ```ctrl + shift + /``` 

- 방금 들어와서 잘 모르겠는데 User Name은 뭐로 해야 하나요?

> 아...아무거나? 그런데 해보니까 한글쓰면 안돼요. 되기는 됩니다. 한글로 가입하면 아이디 공백으로 두시면 됩니다.

- 그냥 거기 코디아드에 파일 새로 만들고 코드넣으면 되는거죠?

---

### Mall 관련

- 아까 온라인쉘에서 mall로 들어가는 방법이 어떻게 되나요....?

- 코디아드 안에서 한다는게 mall 파일안에서 새로 만들고 삭제하고 그러라는 건가용?

- password는 이메일주소인가요?

> 자신의 데이터베이스 사용해야하니 config.php에서 password는 이메일주소로 하면 되겠죠?

- 개인 데이터베이스로 작업하고 싶을 때 dbconnect의 $host 값이 뭐였죠? ㅠㅠ

> 바꾸시면 안되요 localhost에요.

