# 프로그래머스 - 완전탐색

프로그래머스 - 모의고사 문제

{% embed url="https://programmers.co.kr/learn/courses/30/lessons/42840" %}

```text
def solution(answers):
    answer = []
    pattern = [[1,2,3,4,5],[2,1,2,3,2,4,2,5],[3,3,1,1,2,2,4,4,5,5]]
    
    x=0
    y=0
    z=0
    
    for i in range(len(answers)):
        
        if pattern[0][i%5] == answers[i]:
            x = x+1 
        if pattern[1][i%8] == answers[i]:
            y = y+1
        if pattern[2][i%10] == answers[i]:
            z = z+1
            
    result = [x,y,z]
    
    
    temp = result.count(max(result))
    if temp > 1:
        
        for i in range(temp):
            
            if result[i] == max(result):
                answer.append(i+1)
    else :
        answer.append((result.index(max(result))+1))
    
        
    
    return answer
```

초기에 내가 작성한 코드..

![](../.gitbook/assets/image%20%287%29.png)

이렇게 정확성이 삐꾸나는데..ㅠㅠ 왜인지 알아봐야겠다.

```text
def solution(answers):
    answer = []
    pattern = [[1,2,3,4,5],[2,1,2,3,2,4,2,5],[3,3,1,1,2,2,4,4,5,5]]
    
    x=0
    y=0
    z=0
    
    for i in range(len(answers)):
        
        if pattern[0][i%5] == answers[i]:
            x = x+1 
        if pattern[1][i%8] == answers[i]:
            y = y+1
        if pattern[2][i%10] == answers[i]:
            z = z+1
            
    result = [x,y,z]
    
    
    for person,score in enumerate(result):
        if score == max(result):
            answer.append(person+1)

        
    
    return answer
```

아래 점수 출력부분만 다른 코드,, 원래 코드와 뭐가 차이가 나는지 분석해봐야함 !

### 풀이 모음

```text
def solution(answers):
    p = [[1, 2, 3, 4, 5],
         [2, 1, 2, 3, 2, 4, 2, 5],
         [3, 3, 1, 1, 2, 2, 4, 4, 5, 5]]
    s = [0] * len(p) 

    for q, a in enumerate(answers): 
        for i, v in enumerate(p): 
            if a == v[q % len(v)]:
                s[i] += 1
    return [i + 1 for i, v in enumerate(s) if v == max(s)]
```



```text
from itertools import cycle

def solution(answers):
    giveups = [
        cycle([1,2,3,4,5]),
        cycle([2,1,2,3,2,4,2,5]),
        cycle([3,3,1,1,2,2,4,4,5,5]),
    ]
    scores = [0, 0, 0]
    for num in answers:
        for i in range(3):
            if next(giveups[i]) == num:
                scores[i] += 1
    highest = max(scores)

    return [i + 1 for i, v in enumerate(scores) if v == highest]
```

### Enumerate 

열거하다 라는 뜻을 가지고 있는 내장함수. 이 함수는 순서가 있는 자료형을 입력으로 받아 인덱스 값을 포함하는 enumerate 객체를 돌려준다.

예\)

```text
for i, name in enumerate(['body', 'foo', 'bar']):
     print(i, name)
---------------------------------------------------------------------------

0 body
1 foo
2 bar
```

위와 같이 인덱스 = 응시자의 이름을 인덱스로 처리할 때 유용할 것 같다.



### Cycle 

iterable 에서 요소를 반환하고 각각의 복사본을 저장하는 반복자를 만든다.

반복가능한 요소가 모두 소모되면 저장된 사본에서 요소를 리턴한다. 반복가능한 요소가 모두 소모될때까지 무한정 반복한다.



```text
import itertools
list1 = [1,2,3,4]
list2 = ['a','b','c','d','e','f','g']
for list1_item , list2_item in zip(itertools.cycle(list1) , list2) : 
    
    print((list1_item),list2_item))
    
''''
결과
''''
1 a
2 b
3 c
4 d
1 e
2 f
3 g
```



