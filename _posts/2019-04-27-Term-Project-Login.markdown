---
layout: post
title: "Term Project: 로그인 기능 구현하기 (Optional)"
categories: term-project
math: true
permalink: tpLogin
---

### 주의: Optional!!!!

- **Login 기능은 구현할 필요 없습니다.** 본 과제의 프로젝트 구현 범위 밖입니다.
  - 사실 GPA 높이시려면 이거 구현할 시간에 다른거 공부하는게 유리합니다 :) 
- 다만 관심이 있는 학생들에게 정보를 제공해드리기 위해 본 블로그를 작성했습니다.

---

- **Implementing user authentication is not necessary**. It is far beyond the scope and the goal of the term project.
- I wrote this post just in case some students are interested in implementing it.

---

### 구 버전의 mall

- 이번에 우리가 예제로 사용하는 mall 사이트는 얼마전에 개편된 예제 사이트입니다.
- 이것 외에 기존에 써오던 mall 예제의 경우 로그인이 COOKIE 기반으로 구현되어 있습니다.
- 그에 대한 **가이드 문서**[(download)](https://1drv.ms/b/s!AszT-SZB_jByp2zyUM62WccJGCnu)를 잘 읽어보시고, 로그인 및 사용자 권한에 따른 html 내용 변환 로직이 설명을 참조하여 구현해보세요. 
  - 다만 가이드 문서에서 다루는 MALL 예제는 여러분 디렉토리에 설치되어 있는 MALL 코드와 다소 다를겁니다. 테이블 구성도 다릅니다. 이를 유의하여 읽어주세요.

--- 

### 참고자료

#### 1. COOKIE/SESSION-based

- 가이드 문서의 login 기능은 [COOKIE 기반](https://zetawiki.com/wiki/PHP_%EC%BF%A0%ED%82%A4_%EB%A1%9C%EA%B7%B8%EC%9D%B8_%EA%B5%AC%ED%98%84)으로 구현되었습니다. 제타위키 문서를 참조하세요.
- 다른 방식의 구현으로는 [SESSION 기반](https://zetawiki.com/wiki/PHP_%EC%84%B8%EC%85%98_%EB%A1%9C%EA%B7%B8%EC%9D%B8_%EA%B5%AC%ED%98%84) 방법도 있습니다. 제타위키 문서를 참조하세요.

#### 2. Token-based 

- [문서참조](https://medium.com/dev-bits/a-guide-for-adding-jwt-token-based-authentication-to-your-single-page-nodejs-applications-c403f7cf04f4)
