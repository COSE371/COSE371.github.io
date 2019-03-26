---
layout: post
title:  "Week 4+: IN VS EXISTS"
date: 2019-03-24
categories: Lecturenote-and-QA
---

데이터베이스 COSE 371(2) 4주차 강의내용 중 IN VS EXISTS에 대한 보충 설명입니다. 

## Lecture Note

<div class="slide">
<iframe src="https://onedrive.live.com/embed?cid=7230FE4126F9D3CC&amp;resid=7230FE4126F9D3CC%214572&amp;authkey=AJdKTcISeaiIV-s&amp;em=2&amp;wdAr=1.7777777777777777"  frameborder="0">포함된 <a target="_blank" href="https://office.com">Microsoft Office</a> 프레젠테이션, 제공: <a target="_blank" href="https://office.com/webapps">Office Online</a></iframe>
</div>

---

### 1. 필요성?

---

- 두 구문 모두 SQL의 표현력을 높여주는 역할을 합니다. 
  - 특히 MySQL이나 낮은 버전의 MariaDB에서는 INTERSECT 기능이나 EXCEPT 기능이 지원되지 않습니다. 이 경우 IN 또는 EXISTS 구문으로 구현할 수 있습니다 => Q4 참조.
- 차이점?
  - IN의 경우 값의 존재성을 검사할 때 사용하며, EXISTS의 경우 TUPLE의 존재성을 검사할 때 사용합니다. 
  - NULL과 관련된 이슈에 있어서도 두 구문이 차이납니다.
  - 다음과 같은 간략한 constant value set에 대한 검사를 수행할 때 IN을 유용하게 사용할 수 있습니다.


``` sql
MariaDB [cose371]> SELECT N_NATIONKEY, N_NAME, N_REGIONKEY 
    ->                    FROM NATION 
    ->                    WHERE N_NAME IN ('U.S.A.', 'USA', 'UNITED STATES');
+-------------+---------------+-------------+
| N_NATIONKEY | N_NAME        | N_REGIONKEY |
+-------------+---------------+-------------+
|          24 | UNITED STATES |           1 |
+-------------+---------------+-------------+
```

### 2. Correlated?

---

- IN은 correlated subquery 형태로 사용될 수도 있고, correlated subquery 형태로 사용되지 않을 수도 있습니다.

- 반면 **EXISTS 구분은 일반적으로 correlated subquery로 사용**됩니다. correlated가 아닌 EXISTS 구문은 별 의미가 없기 때문입니다. 아래 예제에서 볼 수 있듯 correlated 되어있지 않은 EXISTS 구문이 subquery에 대해 항상 FALSE 나 TRUE를 반환합니다.

``` sql

-- Correlated Subquery가 아닌 EXISTS 구문 --
MariaDB [cose371]>
MariaDB [cose371]> SELECT COUNT(DISTINCT C_Name)
->         FROM CUSTOMER WHERE C_ADDRESS LIKE '%abc%' AND
->              ------------ which is always true ------------
->              EXISTS
->              (SELECT O_CustKey
->                      FROM ORDERS
->                      WHERE LOWER(O_COMMENT) LIKE '%quickly%'
->              )
->              ------------ which is always true ------------
->              ;
+------------------------+
| COUNT(DISTINCT C_Name) |
+------------------------+
|                     99 |
+------------------------+
1 row in set (0.09 sec)

-- 위에서 EXISTS 구문을 제외시킴 --
MariaDB [cose371]>
MariaDB [cose371]> SELECT COUNT(DISTINCT C_Name)
    -> FROM CUSTOMER WHERE C_ADDRESS LIKE '%abc%' AND TRUE;
+------------------------+
| COUNT(DISTINCT C_Name) |
+------------------------+
|                     99 |
+------------------------+
1 row in set (0.09 sec)

```

### 3. IN <-> EXISTS

---

- 많은 경우 non-correlated IN 구문은 correlated EXISTS구문으로, correlated EXISTS 구문은 non-correlated IN 구문으로 바꿀 수 있습니다.
  - [IN <-> EXISTS](https://stackoverflow.com/questions/31297417/how-to-replace-the-in-operator-with-exists-operator-for-the-where-clause-part-o)


### 4. Performance (optimizer disabled)

- (DBMS의 Optimizer가 개입하지 않는다는 가정하에) IN과 EXISTS는 상황에 따라 다른 성능을 보입니다.
- 아래 예제는 correlated EXISTS 구문이 non-correlated IN 구문 보다 30배 가량 빠른 예제입니다.

``` sql

-- 현재 Session에 한해 EXISTS-TO-IN Optimization Rule을 적용하지 않음 --

MariaDB [cose371]> SET SESSION optimizer_switch='exists_to_in=off';
Query OK, 0 rows affected (0.00 sec)

-- Correlated EXISTS => 35.26초 --

MariaDB [cose371]> SELECT COUNT(DISTINCT C_Name)
    ->         FROM CUSTOMER WHERE C_ADDRESS LIKE '%abc%' AND
    ->         EXISTS
    ->         (SELECT O_CustKey
    ->                 FROM ORDERS
    ->                 WHERE O_custKey = C_CustKey AND LOWER(O_COMMENT) LIKE '%quickly%'
    ->         );
+------------------------+
| COUNT(DISTINCT C_Name) |
+------------------------+
|                     62 |
+------------------------+
1 row in set (35.26 sec)

-- Non-correlated IN => 1.69초 --

MariaDB [cose371]> SELECT COUNT(DISTINCT C_Name)
    ->  FROM CUSTOMER WHERE C_ADDRESS LIKE '%abc%' AND
    ->  C_CustKey IN
    ->  (SELECT O_CustKey
    ->          FROM ORDERS
    ->          WHERE LOWER(O_COMMENT) LIKE '%quickly%'
    ->  );
+------------------------+
| COUNT(DISTINCT C_Name) |
+------------------------+
|                     62 |
+------------------------+
1 row in set (1.69 sec)


```

- 위 Query를 처리할 때 DBMS가 어떤 Plan을 사용했는지 확인해보겠습니다.

``` sql

-- Correlated EXISTS => DEPENDENT SUBQUERY 기반 --

MariaDB [cose371]> EXPLAIN
    -> SELECT COUNT(DISTINCT C_Name)
    -> FROM CUSTOMER WHERE C_ADDRESS LIKE '%abc%' AND
    -> EXISTS
    -> (SELECT O_CustKey
    ->         FROM ORDERS
    ->         WHERE O_custKey = C_CustKey AND LOWER(O_COMMENT) LIKE '%quickly%'
    -> );
+------+--------------------+----------+------+---------------+------+---------+------+---------+-------------+
| id   | select_type        | table    | type | possible_keys | key  | key_len | ref  | rows    | Extra       |
+------+--------------------+----------+------+---------------+------+---------+------+---------+-------------+
|    1 | PRIMARY            | CUSTOMER | ALL  | NULL          | NULL | NULL    | NULL |  147940 | Using where |
|    2 | DEPENDENT SUBQUERY | ORDERS   | ALL  | NULL          | NULL | NULL    | NULL | 1481240 | Using where |
+------+--------------------+----------+------+---------------+------+---------+------+---------+-------------+
2 rows in set (0.00 sec)

-- Non-correlated IN => MATERIALIZED 기반 --

MariaDB [cose371]>
MariaDB [cose371]> EXPLAIN
    -> SELECT COUNT(DISTINCT C_Name)
    -> FROM CUSTOMER WHERE C_ADDRESS LIKE '%abc%' AND
    -> C_CustKey IN
    -> (SELECT O_CustKey
    ->  FROM ORDERS
    ->  WHERE LOWER(O_COMMENT) LIKE '%quickly%'
    -> );
+------+--------------+-------------+--------+---------------+--------------+---------+------+---------+-------------+
| id   | select_type  | table       | type   | possible_keys | key          | key_len | ref  | rows    | Extra       |
+------+--------------+-------------+--------+---------------+--------------+---------+------+---------+-------------+
|    1 | PRIMARY      | CUSTOMER    | ALL    | PRIMARY       | NULL         | NULL    | NULL |  147940 | Using where |
|    1 | PRIMARY      | <subquery2> | eq_ref | distinct_key  | distinct_key | 4       | func |       1 |             |
|    2 | MATERIALIZED | ORDERS      | ALL    | NULL          | NULL         | NULL    | NULL | 1481240 | Using where |
+------+--------------+-------------+--------+---------------+--------------+---------+------+---------+-------------+
3 rows in set (0.00 sec)

```

### 5. Performance (optimizer enabled)

---

- 상용 DBMS는 필요에 따라 IN을 동등한 EXISTS로, 또는 EXISTS를 동등한 IN으로 바꾸어 처리하는 최적화 과정을 가지고 있습니다.
  - [EXISTS-TO-IN (MariaDB)](https://mariadb.com/kb/en/library/exists-to-in-optimization/)
  - [IN-TO-EXISTS (MariaDB)](https://mariadb.com/kb/en/non-semi-join-subquery-optimizations/#the-in-to-exists-transformation)

- 그러나 DBMS에 전적으로 성능 최적화를 맡기는 것은 바람직하지 않습니다. 
  - 사용하는 DBMS에서 제공하는 문서를 잘 읽어보시고 다양하게 변형 질의문을 실험해봄으로써 최적화된 질의문을 찾으시는 것이 바람직합니다.

``` sql

-- Correlated EXISTS => 1.69초 --

MariaDB [cose371]> SELECT COUNT(DISTINCT C_Name)
    -> FROM CUSTOMER WHERE C_ADDRESS LIKE '%abc%' AND
    -> EXISTS
    -> (SELECT O_CustKey
    ->         FROM ORDERS
    ->         WHERE O_custKey = C_CustKey AND LOWER(O_COMMENT) LIKE '%quickly%'
    -> );
+------------------------+
| COUNT(DISTINCT C_Name) |
+------------------------+
|                     62 |
+------------------------+
1 row in set (1.69 sec)

-- Non-correlated IN => 1.80초 --

MariaDB [cose371]>
MariaDB [cose371]> SELECT COUNT(DISTINCT C_Name)
    -> FROM CUSTOMER WHERE C_ADDRESS LIKE '%abc%' AND
    -> C_CustKey IN
    -> (SELECT O_CustKey
    ->  FROM ORDERS
    ->  WHERE LOWER(O_COMMENT) LIKE '%quickly%'
    -> );
+------------------------+
| COUNT(DISTINCT C_Name) |
+------------------------+
|                     62 |
+------------------------+
1 row in set (1.80 sec)

-- 처리 방법 비교

MariaDB [cose371]> EXPLAIN
    -> SELECT COUNT(DISTINCT C_Name)
    -> FROM CUSTOMER WHERE C_ADDRESS LIKE '%abc%' AND
    -> EXISTS
    -> (SELECT O_CustKey
    ->         FROM ORDERS
    ->         WHERE O_custKey = C_CustKey AND LOWER(O_COMMENT) LIKE '%quickly%'
    -> );
+------+--------------+-------------+--------+---------------+--------------+---------+------+---------+-------------+
| id   | select_type  | table       | type   | possible_keys | key          | key_len | ref  | rows    | Extra       |
+------+--------------+-------------+--------+---------------+--------------+---------+------+---------+-------------+
|    1 | PRIMARY      | CUSTOMER    | ALL    | PRIMARY       | NULL         | NULL    | NULL |  147940 | Using where |
|    1 | PRIMARY      | <subquery2> | eq_ref | distinct_key  | distinct_key | 4       | func |       1 |             |
|    2 | MATERIALIZED | ORDERS      | ALL    | NULL          | NULL         | NULL    | NULL | 1481240 | Using where |
+------+--------------+-------------+--------+---------------+--------------+---------+------+---------+-------------+
3 rows in set (0.00 sec)

MariaDB [cose371]>
MariaDB [cose371]> EXPLAIN
    -> SELECT COUNT(DISTINCT C_Name)
    -> FROM CUSTOMER WHERE C_ADDRESS LIKE '%abc%' AND
    -> C_CustKey IN
    -> (SELECT O_CustKey
    ->  FROM ORDERS
    ->  WHERE LOWER(O_COMMENT) LIKE '%quickly%'
    -> );
+------+--------------+-------------+--------+---------------+--------------+---------+------+---------+-------------+
| id   | select_type  | table       | type   | possible_keys | key          | key_len | ref  | rows    | Extra       |
+------+--------------+-------------+--------+---------------+--------------+---------+------+---------+-------------+
|    1 | PRIMARY      | CUSTOMER    | ALL    | PRIMARY       | NULL         | NULL    | NULL |  147940 | Using where |
|    1 | PRIMARY      | <subquery2> | eq_ref | distinct_key  | distinct_key | 4       | func |       1 |             |
|    2 | MATERIALIZED | ORDERS      | ALL    | NULL          | NULL         | NULL    | NULL | 1481240 | Using where |
+------+--------------+-------------+--------+---------------+--------------+---------+------+---------+-------------+
3 rows in set (0.00 sec)

```

### 6. 주의

---

- **오해할 수 있는 진술**: 'EXISTS 보다 IN으로 처리하는 것이 더 빠르다' -> X
  - 4~5에서 사용한 예제는 DBMS optimizer 개입이 없다면 EXISTS가 IN보다 비효율적으로 처리되었던 예제입니다.
  - 그러나 IN이 EXISTS보다 비효율적으로 동작하는 경우도 존재합니다.
