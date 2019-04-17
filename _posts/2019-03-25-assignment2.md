---
layout: page
title: "Assignment #2: SQL Practice (~ 04/03)"
categories: current
math: true
permalink: /assignment2/
---

## SQL Practice (~ 04/03)

---


다음 지시 사항들을 시행하시오.

1. A와 B에 제시되어 있는 관계형 스키마들에 해당하는 MariaDB의 테이블(table)들을 생성하여라.
   - [CREATE TABLE .......]
   - 밑줄 친 애트리뷰트는 primary key를 나타내며 각 컬럼 타입 및 제약조건은 임의대로 정의하여 사용하시오.
2. 1.에서 생성한 테이블들 각각에 샘플 데이터(최소 5개 이상)들을 입력하고 각 테이블의 입력된 데이터를 출력(결과 화면 캡쳐)하여 제시하시오.
   - [INSERT INTO ....]
3. A와 B에 제시되어 있는 질의를 SQL로 작성하여 실행하고 그 결과(결과 화면 캡쳐)를 제시하시오.

**주의: 모든 작업은 지정 [서버](https://cose371.github.io/serverInfo/)에서 본인의 MariaDB 계정으로 수행하십시오.**


---

### A. 관계형 스키마(relational schema)-함정 정보 관리

---

- classes (<u>class</u>, type, numGuns, displacement)
   - “class”는 새로운 급의 군함이 만들어졌을 때 그 급을 나타내기 위하여 붙여지는 명칭이다. 
     - e.g.) 광개토대왕함이 만들어지고 난 후 이와 유사한 규모의 군함이 만들어 지면 그 군함을 “광개토대왕함급”이라고 class 명을 붙이게 된다.
   - “type”은 군함의 기능을 나타내는 것으로 전함(BB), 순양함(CC), 구축함(DD), 호위함(FF) 등이 있다.
   - “numGuns”는 해당 군함에 설치된 함포의 수를 나타내며, “displacement”는 군함의 배수량(주로 ton수로 표기)을 나타낸다.
- ships (<u>s_name</u>, class, country, launched)
   - “s_name”은 군함의 이름(예를 들어, 독도함)을 나타냄
   - “country”는 해당 군함을 보유하고 있는 국가명을 나타냄
   - “launched”는 해당 군함이 취역한 년도를 나타냄
- battles (<u>b_name</u>, year)
   - “b_name”은 해전명을 “year”는 해전이 발발한 년도를 나타냄
- outcomes (<u>s_name</u>, <u>b_name</u>, result)
   - 해당 군함(s_name)이 특정 해전(b_name)에 참여한 내역을 결과(result : 침몰, 손상, OK 등)와 함께 나타냄

(1) “노량” 해전에서 “침몰”된 군함의 보유 국가명을 찾아라.

(2) 취역한 년도에 해전에 참전하여 손상을 당한 군함의 이름을 찾아라.

(3) 가장 많은 함포를 보유하고 있는 군함의 이름(class)을 찾아라. 
   - 군함 급 명칭 (class)을 찾아라로 해석하시면 됩니다.

(4) 배수량이 5000톤보다 큰 모든 급(class)의 군함을 보유하고 있는 국가의 이름을 찾아라. 

(5) “대한민국”이 보유하고 있는 군함들의 이름들을 찾되 해당 군함들이 참전한 기록이 있다면 참전한 해전명을 함께 찾아라. 

(6) 국가별 보유 군함의 수와 총배수량을 구하여라(aggregate function을 이용).

(7) 다섯 번 이상 해전에 참전한 군함을 보유한 국가명을 찾아라.

(8) “1945”에 발발한 해전에 참전한 군함의 이름과 취역 년도를 찾아라.



---

### B. 관계형 스키마(relational schema)-호텔 관리

---

- hotel (<u>hotel_id</u>, hotel_name, city)
   - city는 호텔이 위치한 도시를 가리킨다.
- room (<u>hotel_id</u>, <u>room_id</u>, type, price)
   - 방의 유형(type)에는 “single_room”, “double_room”, “premium_room”이 있다.
- booking (<u>guest_id</u>, <u>hotel_id</u>, <u>room_id</u>, <u>date_from</u>, <u>date_to</u>)
   - booking 릴레이션은 호텔 방에 대한 예약 상세 정보 관리를 위해 사용되며 특정 교객(guest_id)에 의한 방의 예약은 호텔 번호(hotel_id), 방 번호(room_id), 예약 기간(date_from, date_to) 정보로 구성된다.
- guest (<u>guest_id</u>, guest_name, age, guest_city)
   - guest_city는 고객이 거주하고 있는 도시를 가리킨다.


(1) “한국호텔”의 “single_room”을 예약한 고객명(guest_name)을 찾아라.

(2) 보유하고 있는 방들의 가격(price) 평균이 가장 큰 호텔명(hotel_name)을 찾아라.

(3) 나이(age)가 50세 이상의 모든 고객의 이름(guest_name)을 찾되 해당 고객들 중 호텔 방을 예약한 이력이 있는 경우에는 예약한 호텔명(hotel_name)도 함께 찾아라. 

(4) 호텔 방의 가격 중 가장 싼 가격(price)를 찾아라. 

(5) 고객이 거주하는 도시에 위치한 호텔을 예약한 고객의 이름(guest_name)을 찾아라. 

(6) “홍길동” 고객에 의해 예약된 호텔명(hotel_name)들을 찾아라.

(7) 호텔별 가장 비싼 방의 가격들 중 가장 비싼 방의 가격을 구하여라.

(8) London에 위치하는 모든 호텔에 방을 예약한 고객이름(guest_name)을 찾아라.


### 제출 및 채점 방법

---

- 제출기한
  - 정상제출: 4월 03일 14시까지 (채점결과의 **100%** 반영)
  - 지각제출: 4월 10일 14시까지 (채점결과의 **80%** 반영)
  - 최종제출: 4월 17일 14시까지 (채점결과의 **50%** 반영)


- 제출방법: [KULMS(블랙보드)](https://kulms.korea.ac.kr/) 에 파일 (**pdf**) 제출
  - 블랙보드 접속이 원할하지 않을 시, ws_choi@kore.ac.kr 로 보내주세요.


- 제출양식: pdf

- 제출내용:
  - 각 테이블 전체 출력 캡쳐본 8개

    ``` sql
    DESC TABLE_NAME;
    SELECT * FROM TABLE_NAME;
    ```

    ![Imgur](https://i.imgur.com/wpxgmBS.png)


  - 각 질의문 SQL 결과 캡쳐본 8개

    ``` sql
    SELECT * FROM TABLE_NAME;
    ```

    ![Imgur](https://i.imgur.com/ZEMkVZr.png)

  - 그림은 예시일 뿐, 이와 꼭 똑같지 않아도 됩니다.
  - 

- 채점방법: 각 문제 (총 24문제: 테이블 8개, SQL 16개) 별 오류 내용 발견 시 0.15점 감점, 부분점수 없음
  - 블랙보드에서의 무제한 제출을 허용하나,
  - 가장 마지막 제출시각으로 정상/지각/최종 여부를 판단하고, 가장 마지막 제출한 내용을 평가하여 채점합니다.
  - **주의: 모든 작업은 지정 [서버](https://cose371.github.io/serverInfo/)에서 본인의 MariaDB 계정으로 수행하십시오.**


--- 

## Q & A

Q1. 다음 번에 과제2 같은 숙제 내주실 때는 기본 데이터셋 몇 개라도 좀 주시면 안될까요.. 과제에 모든 문제에 1개 이상이라도 결과가 노출되게 하려니 너무 소모적인 시간이 발생합니다..ㅜ 혹시 과제의 복붙 금지를 위해서 시라면 기본 데이터셋은 제공하고 거기에 몇 개 더 추가하라고 내시는게 좀 더 좋지 않을까요.. 이상 과제 푸는 시간보다 알맞은 데이터 셋 제작에 시간이 더 소요된 미개한 중생입니다..

> 화이팅! 단순히 부정행위 방지를 위해 스스로 인스턴스 구성하라고 시키는 것은 아닙니다. 다양한 가능성을 염두하며 데이터 셋을 구성해보는 작업은 현재 작성하고 있는 질의가 제대로 동작하는지 확인하는 [좋은 방법](https://www.percona.com/blog/2014/09/10/generating-test-data-from-the-mysql-prompt/) 중 하나이며, 현업에서도 많이 사용된답니다. 과제 1은 교재에서 좋은 데이터 인스턴스를 주었기에 인스턴스 구성에 대한 깊은 고찰을 할 수 없는 반면, 과제 2의 경우 올바른 질의문 작성을 위해 스스로 다양한 케이스를 검토하셔야 합니다.


---

## 문제풀이

``` sql
-- (1) “노량” 해전에서 “침몰”된 군함의 보유 국가명을 찾아라.

-- (2) 취역한 년도에 해전에 참전하여 손상을 당한 군함의 이름을 찾아라.

-- (3) 가장 많은 함포를 보유하고 있는 군함의 이름(class)을 찾아라.

--- 관계대수형 풀이
SELECT DISTINCT country
FROM ships NATURAL JOIN classes NATURAL JOIN
(
   SELECT max(numGuns) as numGuns
   FROM ships NATURAL JOIN classes
) as temp;

-- IN 응용 풀이
SELECT DISTINCT country
FROM ships NATURAL JOIN classes 
	WHERE numGuns IN
(
   SELECT max(numGuns) as numGuns
   FROM ships NATURAL JOIN classes
);

-- ALL 기반 풀이
SELECT DISTINCT country
FROM ships NATURAL JOIN classes
WHERE numGuns >= 
	ALL (SELECT numGuns FROM classes);


-- 아래 풀이는 하나 밖에 못구하므로 좋은 풀이가 아님
SELECT class, max(numGuns) as num
FROM classes
ORDER by num DESC
LIMIt 1

-- Subquery as a scalar value 기반 풀이

SELECT DISTINCT country
FROM ships NATURAL JOIN classes 
	WHERE numGuns =
(
   SELECT max(numGuns)
   FROM ships NATURAL JOIN classes
);

-- (4) 배수량이 5000톤보다 큰 모든 급(class)의 군함을 보유하고 있는 국가의 이름을 찾아라.

--- count based 풀이법 

SELECT DISTINCT country
FROM ships NATURAL JOIN classes
WHERE displacement > 5000
GROUP BY country
HAVING count(DISTINCT class) = (
   SELECT count(DISTINCT class) FROM classes
   WHERE displacement > 5000
   );

-- 관계대수 기반 풀이법

SELECT DISTINCT country FROM ships
WHERE country NOT IN

   -- 결격사유 대상 집합
   (
      SELECT DISTINCT country
      FROM ships CROSS JOIN classes
      WHERE displacement > 5000
      AND (country, classes.class) NOT IN (

         -- 5000톤 이상 보유 현황
         SELECT DISTINCT country, class
         FROM ships NATURAL JOIN classes
         WHERE displacement > 5000
         )
   );

-- (5) “대한민국”이 보유하고 있는 군함들의 이름들을 찾되 해당 군함들이 참전한 기록이 있다면 참전한 해전명을 함께 찾아라.

SELECT s_name, b_name
FROM ships NATURAL LEFT OUTER JOIN outcomes
WHERE country="대한민국";

-- (6) 국가별 보유 군함의 수와 총배수량을 구하여라(aggregate function을 이용).

-- (7) 다섯 번 이상 해전에 참전한 군함을 보유한 국가명을 찾아라.
SELECT country, s_name
FROM ships NATURAL JOIN outcomes
GROUP BY country, s_name
HAVING count(b_name) >= 5;

-- (8) “1945”에 발발한 해전에 참전한 군함의 이름과 취역 년도를 찾아라.

-- (1) “한국호텔”의 “single_room”을 예약한 고객명(guest_name)을 찾아라.

-- (2) 보유하고 있는 방들의 가격(price) 평균이 가장 큰 호텔명(hotel_name)을 찾아라.
SELECT hotel_name, AVG(price) as price
FROM hotel NATURAL JOIN room
GROUP BY hotel_id, hotel_name
HAVING price >= ALL
(
   SELECT AVG(price) as price
   FROM hotel NATURAL JOIN room
   GROUP BY hotel_id, hotel_name
);
-- (3) 나이(age)가 50세 이상의 모든 고객의 이름(guest_name)을 찾되 해당 고객들 중 호텔 방을 예약한 이력이 있는 경우에는 예약한 호텔명(hotel_name)도 함께 찾아라.

SELECT guest_name, hotel_name
FROM guest NATURAL LEFT OUTER JOIN booking 
           NATURAL LEFT OUTER JOIN hotel 
WHERE age >= 50;

-- (4) 호텔 방의 가격 중 가장 싼 가격(price)를 찾아라.

-- (5) 고객이 거주하는 도시에 위치한 호텔을 예약한 고객의 이름(guest_name)을 찾아라.

-- (6) “홍길동” 고객에 의해 예약된 호텔명(hotel_name)들을 찾아라.

-- (7) 호텔별 가장 비싼 방의 가격들 중 가장 비싼 방의 가격을 구하여라.

-- (8) London에 위치하는 모든 호텔에 방을 예약한 고객이름(guest_name)을 찾아라.
```

{% include dq.html %}