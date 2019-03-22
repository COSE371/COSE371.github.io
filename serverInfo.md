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

### 실습서버 접속 방법

- [Online Shell](http://115.68.231.165/shell) 이용
  - Online Shell 접속 시 id와 passwd는 socrative 접속 코드와 동일 (소문자만 사용)
- 또는 Putty 등의 SSH client 이용하셔서 접근하세요.
- **로그인 잘 안될 경우**
  - 접속이 잘 안되시는 분들은 온라인 쉘 말고, UTF-8 인코딩을 지원하는 다른 SSH 프로그램을 사용해보시기 바랍니다.
    - ex) Window: [putty](http://hputty.org/) 설치후 115.68.231.165 접속 (포트 22)
    - ex) Linux or MaxOS: 터미널 실행 후 ssh YOURID@115.68.231.165


### 개인별 계정정보

|항목|계정|비밀번호|예제|
|---|---|---|---|
|Ubuntu|학번|포털에 기재한 메일주소|2009190719, ws_choi@korea.ac.kr|
|Maraidb|db학번|포털에 기재한 메일주소|db2009190719, ws_choi@korea.ac.kr|


### Maria DB 접속방법

``` console
학번@서버주소:~$ mysql -u db학번 -p 
```

### QA

Q1. 아이디 학번 비밀번호 메일 맞나여..

> 온라인 쉘 접속을  id, 비밀번호는 수업시간에 말씀드렸습니다. 우분투의 경우 학번 비밀번호 맞고, Mariadb는 아이디가 db학번, 비밀번호는 메일주소입니다. 잘 안되시면 ws_choi@korea.ac.kr로 학번정보 보내주세요. 계정정보 드리겠습니다.



{% include dq.html %}
