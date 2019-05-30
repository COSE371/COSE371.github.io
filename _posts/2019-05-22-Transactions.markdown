---
layout: post
title: "Week 13: Transactions"
date: 2019-05-22
categories: Lecturenote-and-QA
math: true
---

## Lecture Note

Week 13: Transactions [[pdf]](https://1drv.ms/b/s!AszT-SZB_jByqGJG0p35COWBmzv5) [[slide]](https://1drv.ms/p/s!AszT-SZB_jByqGGHMo-hH0qKpb2B)


<div class="slide">
<iframe src="https://onedrive.live.com/embed?cid=7230FE4126F9D3CC&amp;resid=7230FE4126F9D3CC%215217&amp;authkey=ABfFkJJjEbRMfeM&amp;em=2&amp;wdAr=1.7777777777777777" frameborder="0">포함된 <a target="_blank" href="https://office.com">Microsoft Office</a> 프레젠테이션, 제공: <a target="_blank" href="https://office.com/webapps">Office Online</a></iframe>
</div>


---



## Q & A

- 근데, S랑 S'에 대해서 성능 차이가 왜 발생하는지 모르겠습니다. S도 어짜피 T2에서 A를 읽을려면, T1에서 A를 다 write할 때 까지 기다려야 하는 것 아닌가요?

- Write하면 Memory에 반영을 한 것 같은데, Commit과의 차이는 무엇인가요?

- 그럼 write 끼리 swap 되어도 문제는 없는 건가요?

- commit을 하지않아도 db의 내용이 write에 의해 바뀐다면, commit의 의미가 퇴색되는 것 아닌가요?

- write 끼리 swap 되지 않는 이유는 무엇인가요?

- 그럼 트랜잭션 끝마다 매번 commit 을 붙이면 rollback의 위험성도 줄고 cascadeless 한스캐쥴을 만들수있지않을까요??

- 조금 천천히 나가주시면 안될까요 ㅠㅠ

- 지금까지의 스케줄링이 특정 데이터에 대해 single instance 만 가질 수 있다고 가정하는 것 같은데, replica를 만들어 각 트랜잭션마다 같은 데이터의 복제본을 가지고 처리하면 더 효율적으로 할 여지는 없을까요?

- 꼭 이웃한 줄만 swap하나요?

- 과제4 문제 올려주시면 안될까요??

- 같은 대상에 대해서 write가 2번 연속 붙어져 있는 상황이 존재할 수 있나요?

- Schedule 3이 1,2보다 왜 디스크 idle 이 적은지 모르겠어요