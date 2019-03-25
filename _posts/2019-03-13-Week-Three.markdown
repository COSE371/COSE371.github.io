---
layout: post
title:  "Week 3: Formal Relational Query Languages"
date: 2019-03-13
categories: Lecturenote-and-QA
math: true
---

데이터베이스 COSE 371(2) 3주차 강의내용입니다. 

Formal Relational Query Languages (Relational Algebra)에 대해 알아봅니다.

## Lecture Note


Week 3: Formal Relational Query Languages [[pdf]](https://1drv.ms/b/s!AszT-SZB_jByome8seJVSPE-2-50) [[slide]](https://1drv.ms/p/s!AszT-SZB_jByoma6YccNyaN0iWZB)


<div class="slide">
    <iframe src="https://onedrive.live.com/embed?cid=7230FE4126F9D3CC&amp;resid=7230FE4126F9D3CC%214454&amp;authkey=AG6yawfC6yOWfKo&amp;em=2&amp;wdAr=1.7777777777777777" frameborder="0">포함된 <a target="_blank" href="https://office.com">Microsoft Office</a> 프레젠테이션, 제공: <a target="_blank" href="https://office.com/webapps">Office Online</a></iframe>
</div>

## 슬라이드 정정

---

수업 중 말씀드렸듯 18페이지에 문제에서 요구하는 것이 instructor들의 name이었으므로, ID가 아닌 name을 Projection해주는 것이 맞습니다.

## 질의응답 Detail (new: 0325)

---

Q1. count(distinct ID)가 relational algebra에서도 되나요?

> 교재 표현법에 따르면 다음과 같이 사용합니다.

$$
\mathcal{G}_{count-distinct(ID)}(\sigma _{semester=``Spring'' \wedge year=2010}(teaches))
$$
> The aggregate function count-distinct ensures that even if an instructor teaches more than one course, she is counted only once in the result. 

Q2. 관계대수에서 aggregation function의 결과를 그냥 숫자로 볼 수 있나요? 예를 들면 ρ_{salary=avg(salary)}(instructor) 로 평균 월급 받는 교수의 정보를 얻어낼 수 있을까요?

Q3. caligraphic을 사용하는 경우 하나의 값이 return되는건지 relation이 return되는건지 궁금합니다

> Q2~Q3: aggregate 결과 역시 relation이며, scalar 값으로 활용할 수 없습니다. 다만, SQL에서는 attribute 개수가 하나이며, 그 domain이 numeric이며, tuple이 1개 밖에 없는 경우 숫자로 활용할 수 있습니다.

Q4. 그럼 각 학과 내의 강사 수를 구하려면 dept_name G count (instructor) 이렇게 하면 되나요? 아 instructor 가 아니라 id 로 하면 되는 건가요

> 과제 문제이므로 과제 채점 이후에 말씀드리겠습니다.

Q5. relational algebra에서도 nested subquery를 써도 돠나요?!

> 이미 사용하고 계십니다. 관계대수애서 사용되는 각 expression은 relation입니다.

Q6. teaches 테이블을 예로 들자면, 캘리그라픽 앞에 cousre_id, ID 캘리그라픽 (teaches) 이런식으로 작성하면 output이 어떻게 나오나요?

> 문법에 오류가 있는 듯합니다. $\mathcal{G}$ 뒤에 하나 이상의 aggregation function이 있어야 합니다.


## 질의응답 Detail (old)

---


Q1. **오늘도 열심히하겠습니다! - 강신환 올림**

> 그러십시오 :)


---


### MS Office에서 관계대수 작성하기

Q2. 알파벳 밑에 작은 단어 쓰는거 단축키가 어떻게 되나요??

> 꿀팁공유

- MS office: 수식입력 누르시거나 (텍스트 입력할 공간에 커서 노르고 ```Alt```+N+E+I) 
    - Selection: ```\sigma``` 치고 스페이스 한 번 ㅋㅋㅋ
    - Projection: ```\Pi``` 치고 스페이스 한 번
    - Cartesian Product: ```\times``` 치고 스페이스 한 번
    - Join: ```\bowtie``` 치고 스페이스 한 번
    - theta: ```\theta``` 치고 스페이스 한 번
    - 아랫첨자: ```_``` (쉬프트 0 오른쪽에 있는거 ㅋㅋ)치고 스페이스 한 번하면 아랫첨자 공간 생깁니다.
    - 윗첨자: ```^``` (쉬프트 6)치고 스페이스 한 번하면 윗첨자 공간 생깁니다.
    - 언더바가 포함된 문자열: 따옴표안에 문자열 넣고 다 쓴 후 스페이스 한 번. "inst_id" 써놓고 마지막 따옴표 뒤에 커서놓고 스페이스 한번
    - 그룹 없는 Aggregation: ```\scriptG``` 쓰고 다시 언더바 치고 스페이스바, 아래첨자 공간에 Aggregate Function 나열 
    - 그룹 있는 Aggregation: 아무 글자나 쓰신 후 언더바 치신 다음에 글자를 지우세요. 그렇게 생긴 아랫첨자 공간에 Group 명시 attribute들 나열한 후 나머지는 그룹 없는 Aggregation과 동일하게 작성하세요.

- 한글은 좀 달라요. ```Ctrl```+ N + M 으로 수식편집기 켜시고  
  - Selection: sigma 
  - Projection: Pi 
  - Cartesian Product: times
  - Join: 저도 모르겠네요. ⋈ 복붙하시는게 정신건강에 이로울 듯 합니다.
  - theta: theta
  - 아랫첨자: 언더바 (쉬프트 0 오른쪽에 있는거 ㅋㅋ)치고 원하는 것 { } 안에 넣으시면 됩니다. sigma_{"inst_id"=1074}
  - 윗첨자: hat (쉬프트 6)치고 원하는 것 { } 안에 넣으시면 됩니다.
  - 언더바가 포함된 문자열: 따옴표안에 문자열 넣으시면 됩니다. 언더바가 아니라 일반 하이픈이 나올 수도 있는데, 그냥 그려려니 합시다.
  - 그룹 없는 Aggregation: ```G``` (그냥 G 씁시다...) 언더바 치고 Aggregate Function을 { } 안에 나열
  - 그룹 있는 Aggregation: ```""_{a,b,c} G_{min(x)}(r)``` 이런식으로 써보세요.

- Outer Join: MS든 한글이든, 아래있는 symbol 복사해서 쓰는게 정신건강에 이롭습니다.
  - Left Outer Join : ⟕
  - Right Outer Join: ⟖
  - Full Outer Join: ⟗
  
### 관계대수 Cartesian Product 

---

Q3. cartesian product에서 disjoint 부분 다시 설명해줄 수 있나요?

Q4. If attributes of r(R) and s(S) are not disjoint, then renaming must be used.가 어떤 의미인지 다시한번만 설명해주세요.

Q5. semantic sugar 안쓰면 어떻게 해야된다구요?ㅜㅜ

Q6. semantic sugar가 뭔가요

Q7. semantic 슈거가 무엇인가여..?

Q8. 아까 작성하신 쿼리에서 ID가 겹치는데 리네이밍 없이 카티전 곱 했던게 말씀하신 슈거? 인가요?

>  Q3~Q8. 릴레이션 $r(R)$과 $s(S)$에 대해 $r \times s$를 수행하려고 합니다. 만약 $R \cap S = \emptyset$ 라면 (즉, [disjoint](https://en.wikipedia.org/wiki/Disjoint_sets)하다면) 아무 문제 없이 Cartesian Product 사용할 수 있습니다. 그러나 만약 $R \cap S \neq \emptyset$ 라면, 즉, 하나 이상의 attribute을 두 스키마에서 공유한다면 attribute name이 ambiguous해지겠죠? 이러한 모호성을 피하기 위해 일반적으로는 Rename Operator를 사용합니다. 다만 Rename Operator가 다소 손이 많이갑니다. 이때 Rename 대신, 간단하게 .을 찍어서 어떤 스키마에서 유래한 attribute인지 명시해주는 notation이 있습니다 (교재 222페이지, 3주차 슬라이드 18페이지). 수학적으로는 엄밀하지 않는 표현이나, 관계대수를 다루는 대부분의 교재에서는 이러한 표기를 허용합니다. 그러한 측면에서 .찍고 사용하는 표현법이 [semantic sugar](https://en.wikipedia.org/wiki/Syntactic_sugar)라는 용어를 사용했는데, 혼란이 가중된 것 같네요. semantic sugar라는 표현은 책이나 슬라이드에는 등장하지 않는 용어이니, 기억해두지 않으셔도 됩니다. 


Q10. 카티션 프로덕트 3개도 되나요?

> 네


### Join: Natrual, Theta, Outer

---


Q9. natural join은 일반적인 경우에서 관계대수의 조합으로 정의롤 못하나요? 만약 못한다면 attribute가 아주 많은 relation에서 join을 하려면 일일이 다 해줘야하는건가요?

> 다음과 같이 표현 가능합니다 (교재 231 페이지 참조)

> $r \Join s = \Pi _ {R \cup S}  ( \sigma _{ r.A_1 = s.A_1 \wedge r.A_1 = s.A_1 \wedge ... r.A_n = s.A_n } (r \times s) )$ , where $R \cap S =$ { $A_1, A_2, ..., A_n$}.


Q19. 방금 작성하셨던 쿼리문에서는 instructor.name 이 아니라 name으로 한 것은 natural join 했기 때문인가요?

Q20. Outer Join Using Joins에서 (null,...,null) 이게 뭔지 다시한번만 말씀해주세요 ㅠㅠ



### 관계대수 Set operation

---

Q11. 교집합은 없나요?

> 있습니다. 슬라이드 뒷부분에 나옵니다.

Q12. union 연산이 필요한 이유를 모르겠습니다. 동일한 attribute를 갖고있는 서로다른 relation은 애초에 설계단계에서 잘못한거 아닌가요??


Q13. union이 쿼리의 성능을 떨어뜨리는 걸로 아는데 2개 이상의 테이블을 합친다는거 외에 명령수행 절차 내부에 또다른 특별한 이유가 있는건가요? 아니면 테이블 합치는게 그렇게 오버헤드가 큰가요?


Q14. 그럼 연도와 분반을 union 시킬 때 표시되는 attribute는 연도와 분반중 무엇으로 표시되나요?


Q15. 도메인이 compatible하다는건 타입만 같으면 되는 건가요? 예를들어 연도와 분반이 모두 정수라는 같은 타입으로 나타내질 경우도 compatible하다고 할 수 있나요?

> 맞습니다. compatible이라는 표현이 다소 걸리실 경우, 교재의 표현을 참고하시면 좋을 것 같습니다.

> 교재) The domains of the ith attribute of r and the ith attribute of s must be the same, for all i.



### SQL vs Relational Algebra

---

Q16. distinct 안 넣으면 중복된 게 안 날아가는 건가요

> 관계대수에서는 그렇지 않지만, SQL에서는 distinct를 넣지 않으면 중복된 값이 포함되어 나타납니다. 그렇죠?

![Imgur](https://i.imgur.com/hE7B96u.png)

Q17. 11페이지에서 sql에서는 distinct 붙여야한다했는데 그럼 어떻게 써야하나요? 각 select 뒤에 붙여도 안될것같은데..!

> 질문의 의미를 정확히 모르겠네요. 덧글로 달아주시면, 답변해드리겠습니다.


### 질의 효율

---

Q18. 쿼리문 보여주신 것 중에 2번이 부담이 적다고 하셨는데 내츄럴 조인도 부담이 적나요?

> 관계대수적 관점에서 보았을 때는 Natural Join 자체가 Cartesian Product -> Select -> Projection 입니다. Cartesian Product가 들어가니 단독 연산 중 비용이 큰 편이겠죠? 부담이 큰 편입니다. 다만 첨언허자면, 관계대수 연산자가 질의처리 구현체와 1:1 대응되지는 않습니다. 논리적 연산자인 Natural Join을 물리적 레벨에서 구현하는 방법은 여러가지입니다. [BNL](https://en.wikipedia.org/wiki/Block_nested_loop)과 [Hash Join](https://en.wikipedia.org/wiki/Hash_join) 등이 있고, 이러한 기법은 중간고사 이후에 다룹니다. 어떤 알고리즘으로 조인하는지에 따라 부담이 달라집니다. DBMS는 통계정보 등을 이용해서 최적의 알고리즘을 선택하여 질의를 수행합니다. 만약 효율적인 물리적 내츄럴 조인 수행 기법을 사용할 수 있다면, 내추럴 조인의 부담은 생각보다 낮아지는 편입니다 (그래도 Projection이나 Selection에 비해 연산 비용이 높은 편).



### 관계대수 기타 

---

Q21. relational algebra에서 and, or, not은 >, =, < 보다 order of operations 가 높은건가요?

Q22. relational algebra에서 and or not 오퍼레이터가 > = < 보다 연산순위가 높나요?

Q23. project operation하면 새로운 relation이 생기는 건가요 아니면 원래 relation에서 제거된 채로 바뀌는 건가요

Q24. term의 정의에서 중괄호는 무슨 의미인가요

Q25. unknown and false는 그러면 unknown인가요?

Q26. 예시 수식에서 instructor에는 괄호를 쓰고 teaches 에는 괄호를 안 쓰는 이유가 무엇인가요?

Q27. 참고용 슬라이드에서 이상하게 거꾸로 된 ㄷ 같이 생긴 기호는 뭔가요? ㅠㅠ

> $\Pi$ 랍니다. $\Pi \Pi$



### 기타

---

Q28. 필기본 웹으로 올려주시나요?

> ok

Q29.답 쓰는 칸이 너무 작아요 ㅠㅠ

> 화이팅

> 답 쓰는 칸 조정하셔도 됩니다. 문제 순서만 지켜주세요.

Q30.혹시 윈도우랑 리눅스에 MariaDB 설치하는 방법은 알려주시나요?

> [화이팅](https://mariadb.com/downloads/)

Q31. 10번 슬라이드 우측하단에 원기둥은 왜 있나요?

> 하이퍼링크입니다.

Q32. 스크린에 보이는 소크라티브 질문이 작아서 잘 안 보입니다.. 모바일로 볼 수 있는 방법이 있나요?


