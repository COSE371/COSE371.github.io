---
layout: post
title:  "Week 3: Formal Relational Query Languages"
date: 2019-03-13
categories: Lecturenote-and-QA
---

데이터베이스 COSE 371(2) 3주차 강의내용입니다. 

Formal Relational Query Languages (Relational Algebra)에 대해 알아봅니다.

## Lecture Note


Week 3: Formal Relational Query Languages [[pdf]](https://koreaoffice-my.sharepoint.com/:b:/g/personal/ws_choi_korea_edu/EdTJnSkdnpdBoHdBre-lWFYBxTf5D_7gWccTWPCBveR8ZA?e=eQAeKg) [[slide]](https://koreaoffice-my.sharepoint.com/:p:/g/personal/ws_choi_korea_edu/EZvVeLrZvn9HhgvADieGhhoBEKn6_17gr2N1HKexvkWBcw?e=wF67Cb)


<div class="slide">
    <iframe src="https://koreaoffice-my.sharepoint.com/personal/ws_choi_korea_edu/_layouts/15/Doc.aspx?sourcedoc={ba78d59b-bed9-477f-860b-c00e2786861a}&amp;action=embedview&amp;wdAr=1.7777777777777777" width="100%" frameborder="0">포함된 <a target="_blank" href="https://office.com">Microsoft Office</a> 프레젠테이션, 제공: <a target="_blank" href="https://office.com/webapps">Office Online</a></iframe>
</div>




## 질의응답 Detail

---

질문이 너무 많네요. 다음주까지는 제가 시간이 나지 않을 것 같습니다. 바쁜 일 끝나고 답변해드리겠습니다.

**오늘도 열심히하겠습니다! - 강신환 올림**


relational algebra에서 and, or, not은 >, =, < 보다 order of operations 가 높은건가요?

화살표는 모두 reference 관계를 의미하는 건가요?

Schema Diagram for University Database 슬라이드에서 몇몇 개(course_id 같은)의 것에 밑줄쳐져 있는게 어떤 의미인가요

distinct 안 넣으면 중복된 게 안 날아가는 건가요

안녕하세요~~

union 연산이 필요한 이유를 모르겠습니다. 동일한 attribute를 갖고있는 서로다른 relation은 애초에 설계단계에서 잘못한거 아닌가요??

cartesian product에서 disjoint 부분 다시 설명해줄 수 있나요?

If attributes of r(R) and s(S) are not disjoint, then renaming must be used.가 어떤 의미인지 다시한번만 설명해주세요.

project operation하면 새로운 relation이 생기는 건가요 아니면 원래 relation에서 제거된 채로 바뀌는 건가요

relational algebra에서 and or not 오퍼레이터가 > = < 보다 연산순위가 높나요?

앗 분반이랑 년도/학기 구분을 해야해서 그런건가용..

그럼 연도와 분반을 union 시킬 때 표시되는 attribute는 연도와 분반중 무엇으로 표시되나요?

11페이지에서 sql에서는 distinct 붙여야한다했는데 그럼 어떻게 써야하나요? 각 select 뒤에 붙여도 안될것같은데..!

덥네요..

년도까지 포함해야 superkey로서 기능할 수 있는 것 아닌가요? 매 학기 데이터가 따로 관리되어서 상관없는건가요?

foreign key다시 설명해주실 수 있나요ㅠ?

교집합은 없나요?

도메인이 compatible하다는건 타입만 같으면 되는 건가요? 예를들어 연도와 분반이 모두 정수라는 같은 타입으로 나타내질 경우도 compatible하다고 할 수 있나요?

term의 정의에서 중괄호는 무슨 의미인가요

"Schema Diagram for University Database" 슬라이드를 보면 section, teaches, takes 테이블에 겹치는 attribute가 너무 많은데 이거는 course_id attribute만 있어도 충분하지 않았을까요?

union이 쿼리의 성능을 떨어뜨리는 걸로 아는데 2개 이상의 테이블을 합친다는거 외에 명령수행 절차 내부에 또다른 특별한 이유가 있는건가요? 아니면 테이블 합치는게 그렇게 오버헤드가 큰가요?

10번 슬라이드 우측하단에 원기둥은 왜 있나요?

스크린에 보이는 소크라티브 질문이 작아서 잘 안 보입니다.. 모바일로 볼 수 있는 방법이 있나요?


