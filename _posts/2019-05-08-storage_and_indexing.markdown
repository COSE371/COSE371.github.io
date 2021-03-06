---
layout: post
title: "Week 11: Storage Management & Indexing​"
date: 2019-05-08
categories: Lecturenote-and-QA
math: true
---

## Lecture Note

Week 11: Storage Management & Indexing [[pdf]](https://1drv.ms/b/s!AszT-SZB_jByqE7bDiHyDpc-BEgt) [[slide]](https://1drv.ms/p/s!AszT-SZB_jBypmTXAPUuBdkf6h8P)


<div class="slide">
<iframe src="https://onedrive.live.com/embed?cid=7230FE4126F9D3CC&amp;resid=7230FE4126F9D3CC%214964&amp;authkey=AEXQJW9Csw1j08E&amp;em=2&amp;wdAr=1.7777777777777777" frameborder="0">포함된 <a target="_blank" href="https://office.com">Microsoft Office</a> 프레젠테이션, 제공: <a target="_blank" href="https://office.com/webapps">Office Online</a></iframe>
</div>


---



## Q & A

minimum 조건은 왜 필요한가요?

그러면 디스크에서 읽어올때 무조건 read only 상태로 초기화가 되어서 cache에 저장이 되나요?

k1이랑 같은 키는 p1로 가나요 p2로 가나요?

오늘 조금만...일찍 끝내주시면 안될까요...?

너무 더워요..

MRU를 파일스캔할 때 쓰인다고 하셨는데 애초부터 다시 쓰지 않을 데이터를 읽을 때 왜 버퍼에 옮겨적나요? 그냥 메모리에서 바로 읽으면되지않나요

n은 데이터의 전체 개수인가요?

지금 보고있는 강의자료 어디에 있는건가요..?

b+ tree 슬라이드에 나오는 n 이 전체 데이터 갯수가 아니라 degree 인가요?

Forced output이 해당 블록이 버퍼에서 내려가지 않더라도 현재 상태대로 파일시스템에 업데이트하는 걸 의미하는 건가요?

스승의 은혜는 하늘 같아서- 일찍 마치도록 하겠습니다.

정순영 교수님이 책임지고 DB때 알려주신다하셨어요

b+ tree에서 n이 무엇을 믜이하나요?

교체 상황이 발생 했을 때, buffer의 각 frame에 있는 time stamp를 다 확인해서 가장 오래전에 사용된 프레임을 찾아야 하나요

trie랑 b tree랑 다른건가요?

지금 naturlajoin example에서 LRU 기준으로 본다면 버퍼로 가져온 데이터가 아닌 가장 마지막에 접근한 데이터를 교체해야하므로 P1이 P5로 대체되어야 하는것으로 보입니다. B1은 조건문에 의해서 가장 최신상태의 접근상태를 가지므로 B2가 들어오게 되더라도 B1이 아닌 P2가 B2로 대체될 것으로 보이구요. 그래서 문제가 되는것으로 생각됩니다.

스승님 감사합니다

왜 takes가 블락이 여러개인가요?ㅠㅠ 테이블은 하나인데..

음악듣는 LP판이랑 똑같이 생겼어요 혹시 같은 원리인가요?

2017320186

그래서 결국엔 B1의 기준에서 문제가 되지는 않을 것이고, 새로 B2가 들어왔을 때 나머지 테이블인 P1~P5에 대한 접근 순서가 결정되어 있다면 B1이 버퍼를 차지하고 있을 뿐만아니라 P1->P5순으로 테이블 접근 상태가 옛 상태이므로 B2가 들어왔을 때 현재 버퍼 상에는 조건 비교를 하기 위한 P1~P5는 버퍼내에 존재하지 않습니다. 따라서 실제로 조건 비교를 할 때마다 버퍼를 갱신해야하는 최악의 상태를 가질 것으로 보입니다.
