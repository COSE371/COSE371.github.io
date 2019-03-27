---
layout: page
title: 실습서버 관련 정보
permalink: /serverInfo/
---

### 실습서버 환경 

|항목|내용|
|---|---|
|OS| Ubuntu |
|DBMS| MariaDB|
|Encoding|UTF-8|
|서버 주소|115.68.231.165|

---

### 실습서버 접속 방법


#### 1. SSH 접속

- (방법 1) [Online Shell](http://115.68.231.165/shell) 접속
    - Online Shell 접속 시 id와 passwd는 socrative 접속 코드와 동일 (소문자만 사용)
- (방법 2) Putty 등의 SSH client 이용

#### 2. Ubuntu 접속: 아래와 같이 접속
   
``` console
dossa0328-18078 login: **학번**
Password: **메일주소**                                                                     
Last login: Wed Mar 27 11:12:48 KST 2019 from 163.152.111.34 on pts/16        
Welcome to Ubuntu 16.04.1 LTS (GNU/Linux 4.4.0-116-generic x86_64)            
                                                                              
 * Documentation:  https://help.ubuntu.com                                    
 * Management:     https://landscape.canonical.com                            
 * Support:        https://ubuntu.com/advantage                               
                                                                              
  Get cloud support with Ubuntu Advantage Cloud Guest:                        
    http://www.ubuntu.com/business/services/cloud                             
                                                                              
557 packages can be updated.                                                  
0 updates are security updates.                                               

```

#### 3. MariaDB 접속: 아래와 같이 접속
   
``` console
학번@dossa0328-18078:~$ mysql -u **db학번** -p                                
Enter password: **메일주소**                                                               
Welcome to the MariaDB monitor.  Commands end with ; or \g.                   
Your MariaDB connection id is 1382                                            
Server version: 10.0.34-MariaDB-0ubuntu0.16.04.1 Ubuntu 16.04                 
                                                                              
Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.          
                                                                              
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
                                                                              
MariaDB [(none)]> use **db학번**                                                 
Reading table information for completion of table and column names            
You can turn off this feature to get a quicker startup with -A                
                                                                              
Database changed                                                              
MariaDB [db학번]> **(종료시: \q)**     
```

#### 로그인이 잘 안되는 경우

- 접속이 잘 안되시는 분들은 온라인 쉘 말고, UTF-8 인코딩을 지원하는 다른 SSH 프로그램을 사용해보시기 바랍니다.
  - ex) Window: [putty](http://hputty.org/) 설치후 115.68.231.165 접속 (포트 22)
  - ex) Linux or MaxOS: 터미널 실행 후 ssh YOURID@115.68.231.165



### 개인별 계정정보

---

|항목|계정|비밀번호|예제|
|---|---|---|---|
|Ubuntu|학번|포털에 기재한 메일주소|2009190719, ws_choi@korea.ac.kr|
|Maraidb|db학번|포털에 기재한 메일주소|db2009190719, ws_choi@korea.ac.kr|



### QA

---

Q1. 아이디 학번 비밀번호 메일 맞나여..

> 온라인 쉘 접속을  id, 비밀번호는 수업시간에 말씀드렸습니다. 우분투의 경우 학번 비밀번호 맞고, Mariadb는 아이디가 db학번, 비밀번호는 메일주소입니다. 잘 안되시면 ws_choi@korea.ac.kr로 학번정보 보내주세요. 계정정보 드리겠습니다.



{% include dq.html %}
