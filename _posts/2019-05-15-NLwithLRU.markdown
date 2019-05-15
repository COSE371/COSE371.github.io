---
layout: post
title: "Week 11+: Nested Loop Join + LRU Simulation"
date: 2019-05-15
categories: Lecturenote-and-QA
math: true
---

그냥 코딩해봤습니다.

시험범위 아닙니다.

## Page 구조

시뮬레이션에 필요한 간단한 구조만 구현했습니다. 파일입출력으로 구현하지는 않았습니다.


```python
class page ():
    def __init__(self, name, id, tuples):
        self.name = name
        self.id = id
        self.tuples = tuples
        self.num = len(tuples)
        self.cursor = 0
        
    def init(self):
        self.cursor = 0        
        
    def read(self, objOffset):       
        if(objOffset >= self.num):
            raise Exception
        else:
            return self.tuples[objOffset]
    
    def __str__(self):
        return 'Page:' + self.name
```

다음과 같이 이름이 R1이며 id가 0이고 두 개의 tuple r1과 r2가 저장된 페이지를 만들어봅시다. 


```python
pageName = 'R1'
pageID   = 0
tuples   = ['r1', 'r2']

R1 = page(pageName, pageID, tuples)
```

다음과 같이 tuple을 읽을 수 있습니다. (이 예제에서는 tuple 입력은 따로 구현 안햇습니다.)

다만 page에 저장된 tuple의 수가 2이기 때문에 ```print(R1.read(2))```은 에러가 납니다.


```python
print('number of tuples in R1:', str(R1.num))
print(R1.read(0))
print(R1.read(1))
```

    number of tuples in R1: 2
    r1
    r2



```python
print(R1.read(2))
```


    ---------------------------------------------------------------------------

    Exception                                 Traceback (most recent call last)

    <ipython-input-113-bc1a2279c070> in <module>
    ----> 1 print(R1.read(2))
    

    <ipython-input-109-d92861b0f9b9> in read(self, objOffset)
         12     def read(self, objOffset):
         13         if(objOffset >= self.num):
    ---> 14             raise Exception
         15         else:
         16             return self.tuples[objOffset]


    Exception: 


## LRU 버퍼

시뮬레이션을 위해 아주 간단하게 만든 LRU 버퍼입니다.


```python
import sys
    
class frame():
    def __init__(self):
        self.isAllocated = False
        self.page = None
        self.TS = -1
        pass

    def isAllocated(self):
        return self.isAllocated;

    def getPage(self):
        global TS
        self.TS = TS
        return self.page

    def setPage(self, page):
        global TS
        self.page=page
        self.isAllocated=True
        self.TS = TS
        
    def free(self):
        self.page=None
        self.isAllocated=False
        self.TS = -1
        #WB logic
        
    def __str__(self):
        if(self.isAllocated):
            return 'Allocated Page: ' + str(self.page) + ', TS:' + str(self.TS)
        else:
            return 'EmptyFrame'
        
class LRU_buffer():
    def __init__(self, num, ALLPAGES):
        self.buffer= [frame() for _ in range(num)]
        self.pageTable = dict()
        self.ALLPAGES = ALLPAGES
            
    def chooseVictim(self):
                
        minTS = sys.maxsize
        for i, frame in enumerate(self.buffer):
            if(frame.TS < minTS):
                minTS = frame.TS
                victimIdx= i

        return victimIdx

    def hasEmptyFrame(self):
        for frame in self.buffer:
            if(not frame.isAllocated):
                return True

        return False
    
    def nextEmpty(self):
        for frame in self.buffer:
            if(not frame.isAllocated):
                return frame

    def hasPage(self, id):
        return id in self.pageTable
    
    def readPage(self, id):
        for page in self.ALLPAGES:
            if(page.id == id):
                return page
        return None
        
    def getPage(self, id):
        
        # HIT
        if(self.hasPage(id)):
            return self.pageTable[id].getPage()
        
                       
        # FAULT case 1: has an empty frame
        if(self.hasEmptyFrame()):
            frame = self.nextEmpty()
            frame.setPage(self.readPage(id))
            self.pageTable[id] = frame

        # FAULT case 2: no vacant space
        else:
            
            # buffer replacement: START #       
            global TS

            print('Buffer REPLACEMENT!!: RLU at TS', str(TS))
            print('Before: victim Selection')
            self.printStat()
            
            victimIdx = self.chooseVictim()
            victim = self.buffer[victimIdx]
            victimPageId = victim.getPage().id
            victim.free()
            del self.pageTable[victimPageId]

            frame = self.buffer[victimIdx]
            frame.setPage(self.readPage(id))
            self.pageTable[id] = frame   
            
            print('After: victim Selected: ', str(self.buffer[victimIdx].getPage().name))
            self.printStat()
        
            # buffer replacement: END #  


        return frame.getPage()
    
    def printStat(self):
        for frame in self.buffer:
            print(frame)
```

## Table Reader 

이제 Table Reader를 만들어보겠습니다.


```python
class Table():
    def __init__(self, name, list_of_page, buffer):
        self.name = name
        self.pages = list_of_page
        self.buffer = buffer
        self.init()

    def init(self):
        self.cursor = 0 
        self.pageIds = [page.id for page in self.pages]

    def __iter__(self):
        return self    
    
    def __next__(self):
      
        if(self.cursor >= len(self.pages)*2):
            raise StopIteration

        global TS
        
        TS += 1
        print('# TS ', str(TS))
        
        pageOffset = (self.cursor)//2
        objOffset  = self.cursor % 2
        
        pageId = self.pageIds[pageOffset]

        page = self.buffer.getPage(pageId)
        t = page.read(objOffset)

        self.cursor += 1
        

        print('\treadp:', page.name)

        return t
```

## Nested Loop Join + LRU 시뮬레이션

![Imgur](https://i.imgur.com/bTnO3Oc.png)

그림과 시뮬레이션 로그가 일치하는지 확인해보면서 코드를 보시면 공부에 도움이 될 듯합니다.


```python
R1 = page('R1', 0, ['r1', 'r2'])
R2 = page('R2', 1, ['r3', 'r4'])
S1 = page('S1', 2, ['s1', 's2'])
S2 = page('S2', 3, ['s3', 's4'])
S3 = page('S3', 4, ['s5', 's6'])
S4 = page('S4', 5, ['s7', 's8'])


lru  = LRU_buffer(3, [R1,R2,S1,S2,S3,S4])

r = Table('r', [R1, R2], lru)
s = Table('s', [S1, S2, S3, S4], lru)

TS = 0
for tt in r:
    s.init()
    for ts in s:
        TS += 1
        print('# TS ', str(TS), '\n\tmatch:', tt, ' and ', ts)
```

    # TS  1
    	readp: R1
    # TS  2
    	readp: S1
    # TS  3 
    	match: r1  and  s1
    # TS  4
    	readp: S1
    # TS  5 
    	match: r1  and  s2
    # TS  6
    	readp: S2
    # TS  7 
    	match: r1  and  s3
    # TS  8
    	readp: S2
    # TS  9 
    	match: r1  and  s4
    # TS  10
    Buffer REPLACEMENT!!: RLU at TS 10
    Before: victim Selection
    Allocated Page: Page:R1, TS:1
    Allocated Page: Page:S1, TS:4
    Allocated Page: Page:S2, TS:8
    After: victim Selected:  S3
    Allocated Page: Page:S3, TS:10
    Allocated Page: Page:S1, TS:4
    Allocated Page: Page:S2, TS:8
    	readp: S3
    # TS  11 
    	match: r1  and  s5
    # TS  12
    	readp: S3
    # TS  13 
    	match: r1  and  s6
    # TS  14
    Buffer REPLACEMENT!!: RLU at TS 14
    Before: victim Selection
    Allocated Page: Page:S3, TS:12
    Allocated Page: Page:S1, TS:4
    Allocated Page: Page:S2, TS:8
    After: victim Selected:  S4
    Allocated Page: Page:S3, TS:12
    Allocated Page: Page:S4, TS:14
    Allocated Page: Page:S2, TS:8
    	readp: S4
    # TS  15 
    	match: r1  and  s7
    # TS  16
    	readp: S4
    # TS  17 
    	match: r1  and  s8
    # TS  18
    Buffer REPLACEMENT!!: RLU at TS 18
    Before: victim Selection
    Allocated Page: Page:S3, TS:12
    Allocated Page: Page:S4, TS:16
    Allocated Page: Page:S2, TS:8
    After: victim Selected:  R1
    Allocated Page: Page:S3, TS:12
    Allocated Page: Page:S4, TS:16
    Allocated Page: Page:R1, TS:18
    	readp: R1
    # TS  19
    Buffer REPLACEMENT!!: RLU at TS 19
    Before: victim Selection
    Allocated Page: Page:S3, TS:12
    Allocated Page: Page:S4, TS:16
    Allocated Page: Page:R1, TS:18
    After: victim Selected:  S1
    Allocated Page: Page:S1, TS:19
    Allocated Page: Page:S4, TS:16
    Allocated Page: Page:R1, TS:18
    	readp: S1
    # TS  20 
    	match: r2  and  s1
    # TS  21
    	readp: S1
    # TS  22 
    	match: r2  and  s2
    # TS  23
    Buffer REPLACEMENT!!: RLU at TS 23
    Before: victim Selection
    Allocated Page: Page:S1, TS:21
    Allocated Page: Page:S4, TS:16
    Allocated Page: Page:R1, TS:18
    After: victim Selected:  S2
    Allocated Page: Page:S1, TS:21
    Allocated Page: Page:S2, TS:23
    Allocated Page: Page:R1, TS:18
    	readp: S2
    # TS  24 
    	match: r2  and  s3
    # TS  25
    	readp: S2
    # TS  26 
    	match: r2  and  s4
    # TS  27
    Buffer REPLACEMENT!!: RLU at TS 27
    Before: victim Selection
    Allocated Page: Page:S1, TS:21
    Allocated Page: Page:S2, TS:25
    Allocated Page: Page:R1, TS:18
    After: victim Selected:  S3
    Allocated Page: Page:S1, TS:21
    Allocated Page: Page:S2, TS:25
    Allocated Page: Page:S3, TS:27
    	readp: S3
    # TS  28 
    	match: r2  and  s5
    # TS  29
    	readp: S3
    # TS  30 
    	match: r2  and  s6
    # TS  31
    Buffer REPLACEMENT!!: RLU at TS 31
    Before: victim Selection
    Allocated Page: Page:S1, TS:21
    Allocated Page: Page:S2, TS:25
    Allocated Page: Page:S3, TS:29
    After: victim Selected:  S4
    Allocated Page: Page:S4, TS:31
    Allocated Page: Page:S2, TS:25
    Allocated Page: Page:S3, TS:29
    	readp: S4
    # TS  32 
    	match: r2  and  s7
    # TS  33
    	readp: S4
    # TS  34 
    	match: r2  and  s8
    # TS  35
    Buffer REPLACEMENT!!: RLU at TS 35
    Before: victim Selection
    Allocated Page: Page:S4, TS:33
    Allocated Page: Page:S2, TS:25
    Allocated Page: Page:S3, TS:29
    After: victim Selected:  R2
    Allocated Page: Page:S4, TS:33
    Allocated Page: Page:R2, TS:35
    Allocated Page: Page:S3, TS:29
    	readp: R2
    # TS  36
    Buffer REPLACEMENT!!: RLU at TS 36
    Before: victim Selection
    Allocated Page: Page:S4, TS:33
    Allocated Page: Page:R2, TS:35
    Allocated Page: Page:S3, TS:29
    After: victim Selected:  S1
    Allocated Page: Page:S4, TS:33
    Allocated Page: Page:R2, TS:35
    Allocated Page: Page:S1, TS:36
    	readp: S1
    # TS  37 
    	match: r3  and  s1
    # TS  38
    	readp: S1
    # TS  39 
    	match: r3  and  s2
    # TS  40
    Buffer REPLACEMENT!!: RLU at TS 40
    Before: victim Selection
    Allocated Page: Page:S4, TS:33
    Allocated Page: Page:R2, TS:35
    Allocated Page: Page:S1, TS:38
    After: victim Selected:  S2
    Allocated Page: Page:S2, TS:40
    Allocated Page: Page:R2, TS:35
    Allocated Page: Page:S1, TS:38
    	readp: S2
    # TS  41 
    	match: r3  and  s3
    # TS  42
    	readp: S2
    # TS  43 
    	match: r3  and  s4
    # TS  44
    Buffer REPLACEMENT!!: RLU at TS 44
    Before: victim Selection
    Allocated Page: Page:S2, TS:42
    Allocated Page: Page:R2, TS:35
    Allocated Page: Page:S1, TS:38
    After: victim Selected:  S3
    Allocated Page: Page:S2, TS:42
    Allocated Page: Page:S3, TS:44
    Allocated Page: Page:S1, TS:38
    	readp: S3
    # TS  45 
    	match: r3  and  s5
    # TS  46
    	readp: S3
    # TS  47 
    	match: r3  and  s6
    # TS  48
    Buffer REPLACEMENT!!: RLU at TS 48
    Before: victim Selection
    Allocated Page: Page:S2, TS:42
    Allocated Page: Page:S3, TS:46
    Allocated Page: Page:S1, TS:38
    After: victim Selected:  S4
    Allocated Page: Page:S2, TS:42
    Allocated Page: Page:S3, TS:46
    Allocated Page: Page:S4, TS:48
    	readp: S4
    # TS  49 
    	match: r3  and  s7
    # TS  50
    	readp: S4
    # TS  51 
    	match: r3  and  s8
    # TS  52
    Buffer REPLACEMENT!!: RLU at TS 52
    Before: victim Selection
    Allocated Page: Page:S2, TS:42
    Allocated Page: Page:S3, TS:46
    Allocated Page: Page:S4, TS:50
    After: victim Selected:  R2
    Allocated Page: Page:R2, TS:52
    Allocated Page: Page:S3, TS:46
    Allocated Page: Page:S4, TS:50
    	readp: R2
    # TS  53
    Buffer REPLACEMENT!!: RLU at TS 53
    Before: victim Selection
    Allocated Page: Page:R2, TS:52
    Allocated Page: Page:S3, TS:46
    Allocated Page: Page:S4, TS:50
    After: victim Selected:  S1
    Allocated Page: Page:R2, TS:52
    Allocated Page: Page:S1, TS:53
    Allocated Page: Page:S4, TS:50
    	readp: S1
    # TS  54 
    	match: r4  and  s1
    # TS  55
    	readp: S1
    # TS  56 
    	match: r4  and  s2
    # TS  57
    Buffer REPLACEMENT!!: RLU at TS 57
    Before: victim Selection
    Allocated Page: Page:R2, TS:52
    Allocated Page: Page:S1, TS:55
    Allocated Page: Page:S4, TS:50
    After: victim Selected:  S2
    Allocated Page: Page:R2, TS:52
    Allocated Page: Page:S1, TS:55
    Allocated Page: Page:S2, TS:57
    	readp: S2
    # TS  58 
    	match: r4  and  s3
    # TS  59
    	readp: S2
    # TS  60 
    	match: r4  and  s4
    # TS  61
    Buffer REPLACEMENT!!: RLU at TS 61
    Before: victim Selection
    Allocated Page: Page:R2, TS:52
    Allocated Page: Page:S1, TS:55
    Allocated Page: Page:S2, TS:59
    After: victim Selected:  S3
    Allocated Page: Page:S3, TS:61
    Allocated Page: Page:S1, TS:55
    Allocated Page: Page:S2, TS:59
    	readp: S3
    # TS  62 
    	match: r4  and  s5
    # TS  63
    	readp: S3
    # TS  64 
    	match: r4  and  s6
    # TS  65
    Buffer REPLACEMENT!!: RLU at TS 65
    Before: victim Selection
    Allocated Page: Page:S3, TS:63
    Allocated Page: Page:S1, TS:55
    Allocated Page: Page:S2, TS:59
    After: victim Selected:  S4
    Allocated Page: Page:S3, TS:63
    Allocated Page: Page:S4, TS:65
    Allocated Page: Page:S2, TS:59
    	readp: S4
    # TS  66 
    	match: r4  and  s7
    # TS  67
    	readp: S4
    # TS  68 
    	match: r4  and  s8

