---
layout: post
title: "MysqlDump: Database Dump Script 만들기"
date: 2019-06-12
categories: etc
---

여러분들이 이때까지 작업하신 데이터베이스를 DDL+DML Script 형태로 출력하는 방법을 소개해드립니다.

과제 아닙니다 :)

### 1. mysqldump 이용해보기
```console
2019KU0080@dossa0328-18078:~$ cd                
2019KU0080@dossa0328-18078:~$ pwd                                                 
/home/db2019/2019KU0080                                                           

2019KU0080@dossa0328-18078:~$ mysqldump -u db2019KU0080 db2019KU0080 -p > dump.sql                      
Enter password: ***********
```

```sql
mysqldump: Couldn't execute 'SHOW FIELDS FROM `cnt_class`': View 'db2019KU0080.cnt_class' references invalid table(s) or column(s) or function(s) or definer/invoker of view lack rights to use them (1356)                  
```

``` console
2019KU0080@dossa0328-18078:~$ ls                            
dump.sql  public_html

2019KU0080@dossa0328-18078:~$ head dump.sql                                                                                         -- MySQL dump 10.15  Distrib 10.0.38-MariaDB, for debian-linux-gnu (x86_64)                                                         --                                      
-- Host: localhost    Database: db2019KU0080                                                                                                                                     
-- ------------------------------------------------------                                                                           -- Server version       10.0.38-MariaDB-0ubuntu0.16.04.1
/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;                               
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
```

### 2. Debugging

``` sql
mysqldump: Couldn't execute 'SHOW FIELDS FROM `cnt_class`':
 View 'db2019KU0080.cnt_class' references invalid table(s) or column(s) or function(s) or definer/invoker of view lack rights to use them (1356)  
```

dump 명령 후에 발생하는 위와 같은 에러는 주로 View를 등록한 후 View가 Referencing하고 있는 테이블 (즉, 피연산자 테이블)을 삭제하거나 컬럼을 삭제하는 경우에 발생합니다. invalid한 View를 삭제해주신 후 mysqldump를 수행하시면 정상적으로 dump.sql 만드실 수 있을 겁니다. 에러가 발생하면, 그 이후로는 dump가 진행되지 않으니 반드시 에러를 모두 잡아주셔야합니다. 