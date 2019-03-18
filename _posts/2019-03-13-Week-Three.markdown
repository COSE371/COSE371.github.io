---
layout: post
title:  "Week 3: Formal Relational Query Languages"
date: 2019-03-13
categories: Lecturenote-and-QA
---

데이터베이스 COSE 371(2) 3주차 강의내용입니다. 

Formal Relational Query Languages (Relational Algebra)에 대해 알아봅니다.

## Lecture Note


Week 3: Formal Relational Query Languages [[pdf]](https://1drv.ms/b/s!AszT-SZB_jByome8seJVSPE-2-50) [[slide]](https://1drv.ms/p/s!AszT-SZB_jByoma6YccNyaN0iWZB)


<div class="slide">
    <iframe src="https://onedrive.live.com/embed?cid=7230FE4126F9D3CC&amp;resid=7230FE4126F9D3CC%214454&amp;authkey=AG6yawfC6yOWfKo&amp;em=2&amp;wdAr=1.7777777777777777" frameborder="0">포함된 <a target="_blank" href="https://office.com">Microsoft Office</a> 프레젠테이션, 제공: <a target="_blank" href="https://office.com/webapps">Office Online</a></iframe>
</div>



## 질의응답 Detail

---

질문이 너무 많네요. 다음주까지는 제가 시간이 나지 않을 것 같습니다. 바쁜 일 끝나고 답변해드리겠습니다.


Q1. **오늘도 열심히하겠습니다! - 강신환 올림**

> 그러십시오 :)

relational algebra에서 and, or, not은 >, =, < 보다 order of operations 가 높은건가요?

distinct 안 넣으면 중복된 게 안 날아가는 건가요

union 연산이 필요한 이유를 모르겠습니다. 동일한 attribute를 갖고있는 서로다른 relation은 애초에 설계단계에서 잘못한거 아닌가요??

cartesian product에서 disjoint 부분 다시 설명해줄 수 있나요?

If attributes of r(R) and s(S) are not disjoint, then renaming must be used.가 어떤 의미인지 다시한번만 설명해주세요.

project operation하면 새로운 relation이 생기는 건가요 아니면 원래 relation에서 제거된 채로 바뀌는 건가요

relational algebra에서 and or not 오퍼레이터가 > = < 보다 연산순위가 높나요?



그럼 연도와 분반을 union 시킬 때 표시되는 attribute는 연도와 분반중 무엇으로 표시되나요?

11페이지에서 sql에서는 distinct 붙여야한다했는데 그럼 어떻게 써야하나요? 각 select 뒤에 붙여도 안될것같은데..!

덥네요..


교집합은 없나요?

term의 정의에서 중괄호는 무슨 의미인가요

도메인이 compatible하다는건 타입만 같으면 되는 건가요? 예를들어 연도와 분반이 모두 정수라는 같은 타입으로 나타내질 경우도 compatible하다고 할 수 있나요?

union이 쿼리의 성능을 떨어뜨리는 걸로 아는데 2개 이상의 테이블을 합친다는거 외에 명령수행 절차 내부에 또다른 특별한 이유가 있는건가요? 아니면 테이블 합치는게 그렇게 오버헤드가 큰가요?

필기본 웹으로 올려주시나요?

Outer Join Using Joins에서 (null,...,null) 이게 뭔지 다시한번만 말씀해주세요 ㅠㅠ

semantic sugar 안쓰면 어떻게 해야된다구요?ㅜㅜ

semantic sugar가 뭔가요

semantic 슈거가 무엇인가여..?

쿼리문 보여주신 것 중에 2번이 부담이 적다고 하셨는데 내츄럴 조인도 부담이 적나요?

혹시 윈도우랑 리눅스에 MariaDB 설치하는 방법은 알려주시나요?

카티션 프로덕트 3개도 되나요?

답 쓰는 칸이 너무 작아요 ㅠㅠ

예시 수식에서 instructor에는 괄호를 쓰고 teaches 에는 괄호를 안 쓰는 이유가 무엇인가요?

잘 들립니다

방금 작성하셨던 쿼리문에서는 instructor.name 이 아니라 name으로 한 것은 natural join 했기 때문인가요?

unknown and false는 그러면 unknown인가요?

아까 작성하신 쿼리에서 ID가 겹치는데 리네이밍 없이 카티전 곱 했던게 말씀하신 슈거? 인가요?

natural join은 일반적인 경우에서 관계대수의 조합으로 정의롤 못하나요? 만약 못한다면 attribute가 아주 많은 relation에서 join을 하려면 일일이 다 해줘야하는건가요?


알파벳 밑에 작은 단어 쓰는거 단축키가 어떻게 되나요??

참고용 슬라이드에서 이상하게 거꾸로 된 ㄷ 같이 생긴 기호는 뭔가요? ㅠㅠ

### 기타

---

10번 슬라이드 우측하단에 원기둥은 왜 있나요?

스크린에 보이는 소크라티브 질문이 작아서 잘 안 보입니다.. 모바일로 볼 수 있는 방법이 있나요?


