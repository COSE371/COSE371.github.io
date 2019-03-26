---
layout: page
title: "Assignment #1: Formal Relational Query Language (~ 03/27) (Q&A 수정: 0325)"
categories: current
math: true
permalink: /assignment/
---

- Database System Concept 6th edition 연습문제 풀기 (총 27문제)
  - Practice Exercises
      - 6.1, 6.2, 6.3

  - Exercises
      - 6.10
      - 6.11(a,b,c,d)
      - 6.12
      - 6.13 
      - 6.14(a, c, d)

  -  enrollment: 등록 수, 수강인원을 뜻합니다.
  
- 제출기한
  - 정상제출: 3월 27일 14시까지 (채점결과의 **100%** 반영)
  - 지각제출: 4월 03일 14시까지 (채점결과의 **80%** 반영)
  - 최종제출: 4월 10일 14시까지 (채점결과의 **50%** 반영)


- 제출방법: [KULMS(블랙보드)](https://kulms.korea.ac.kr/) 에 파일 (**pdf**) 제출
  - 블랙보드 접속이 원할하지 않을 시, ws_choi@kore.ac.kr 로 보내주세요.


- 제출양식: [pdf, 한글, ms_word](https://1drv.ms/f/s!AszT-SZB_jByoyr84sI3g4jMWN8W) 중 택1
  - pdf: 인쇄하여 작성 후 스캔하여 제출해주세요. 스캐너가 없을 경우 스마트폰에 dropbox ([android](https://play.google.com/store/apps/details?id=com.dropbox.android&hl=ko), [iphone](https://itunes.apple.com/kr/app/dropbox/id327630330?mt=8))등의 application 설치하여 카메라로 스캔하시면 됩니다. 
  - [한글, MS_word] 한글이나 MS_word에 직접 타이핑해서 과제하시는 경우는 최종적으로 PDF로 변환하여 제출해주세요. 가급적 페이지 레이아웃 달라지지 않게해주세요.
- 채점방법: 각 문제 (총 27문제) 별 오류 내용 발견 시 0.15점 감점, 부분점수 없음
  - 블랙보드에서의 무제한 제출을 허용하나,
  - 가장 마지막 제출시각으로 정상/지각/최종 여부를 판단하고, 가장 마지막 제출한 내용을 평가하여 채점합니다.

### University Scheme

-  교재 Appendix A 보시면 University Scheme가 나와있습니다. 그 뒷부분에는 예제 instance들이 들어있습니다. 이를 참조하셔서 문제 푸시면 됩니다.

- Instance

![Imgur](https://i.imgur.com/lzkM7EM.png)

![Imgur](https://i.imgur.com/mU033zE.png)

### 과제관련 Q & A (New: 0325)

---

Q0. 과제 관련 질문입니다. 6.1 e,f,g 에서 Autumn 2009년도라는 조건이 나오는데 교재나 교수님께서 홈페이지에 올려주신 relation들에는 Autumn이라고 표기된 것이 없습니다,,, 물론 semantic하게 Fall을 Autumn이라고 인지할수는 있겠으나 그래도 좀 찝찝하네요. 과제 기한이 38시간 정도 남은 시점인데 명확히 해주셨으면 좋겠습니다.

> 교재에서 제공되는 relation instance에는 Fall로 되어 있는데 정작 문제에서는 Autumn으로 나와서 당황하셨을텐데, 수업 중에 말씀드렸듯 Semester 값을 FalL로 하시든 Autumn으로 하시든 둘 중에 하나로 하시면 됩니다. 둘 다 정답처리하겠습니다.

Q1. *쓰면 무조건 오답인가요?

Q2. 관게대수에서는 count(*) 쓰면 안되나요?

Q3. 그냥 교수님도 채점하시기 편하게 count(*) 허용해주시면 안되나요ㅠㅠ

Q4. 관계대수 피피티의 aggregate F에 count 있는데 쓰지 말고 풀라는 말씀이신가요 아니면 * 만 쓰지 말라고 하신건가요??

> Q1~Q4, Q9: 이번 학기에는 * 쓰셔도 답만 맞다면 정답처리하겠습니다. * 는 '모든 어트리뷰트 나열'이라고 해석하겠습니다.

Q5. 과제에서 답 부분에 쿼리를 쓰면 되는건가요?

> 네~

Q6. count-distinct는 써도 되나요? 

$$
\mathcal{G}_{count-distinct(ID)}(\sigma _{semester=``Spring'' \wedge year=2010}(teaches))
$$


> 필요하시다면 쓰시면 됩니다. 다만 count-distinct는 수업 중에 언급하지 않은 내용이라, 안쓴 경우에도 그것을 제외하고 맞다면 정답처리 하겠습니다.

Q7. * 안쓰면 모든 attribute를 다써야하나요? 관계대수에서요

> 세야하는 대상을 attribute 집합으로 표현하시면 됩니다. 

Q7. [6.12 a] 에서 “find course sections” 라는 말이 나오는데 여기서 course section이 무엇을 의미하는지 모르겠어요!!

>  section의 primary key인 (course id, sec id, semester, year)를 찾으시면 됩니다.


Q8. works relation 있는 person name이 employee relation에 존재하지 않을수도 있나요?

> 필요하신 경우, 해당 사항을 가정하시고 문제를 푸시면 됩니다.

Q9. select count (*) from course를 과제에 왜 쓰면 안되는건가요??

> SQL에서는 쓰셔도 됩니다. 슬라이드 및 관계대수에서는 교재 기준으로 * 라는 노테이션 언급이 없습니다.


### 과제관련 Q & A (old)

---

Q1. 풀이 써야 하는지, 태블릿 필기로 문제풀어도 되는지 궁금합니다

Q2. 과제는 답만 쓰나요 풀이도 쓰나요?

Q3. 답 칸 임의로 늘려도 되는지, 태블릿 전자필기로 써서 제출해도 되는지 궁금합니다!

Q4. 답 칸 너무 작아요 ㅜㅜ

> 풀이 쓰셔도 되고 안쓰셔도 됩니다. 답만 맞으면 정답처리하고, 답이 틀리면 오답처리합니다. 태블릿 필기로 문제 푸셔도 되고 일반 펜으로 푸셔도 되고, 워드나 한글로 작성하셔서 제출하셔도 됩니다. 다만 제출 양식은 pdf만 받습니다. 알아볼 수만 있게 작성해주세요...!

> 답칸 임의로 늘리셔도 됩니다. 문제 순서만 지켜주세요.

Q5. 과제할때도 Reaname Operation의 사용 대신 Semantic Sugar 사용하면 되는건가요??

> 쓰셔도 무방합니다.

Q6. 과제 제출시 assignment 사용해서 답을 변수로 기술해도 되나요?

> 그렇게하셔도 됩니다.

Q7. 과제는 DB Book 6판 기준인가요..??

> 맞습니다.

Q8. 과제에서 course section 이라는 말이 나오는데, 정확히 뭔가요??

> course: 강의정보 (개념적), section: 강의(실제 구체화된 강의, 몇년도 몇학기 등 실체화된 개념)

{% include dq.html %}
