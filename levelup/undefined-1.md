# 프로그래머스 - 정렬

{% embed url="https://programmers.co.kr/learn/courses/30/lessons/42748?language=python3" %}

```text
def solution(array, commands):
    answer = []
    result = []
    kcommands = []
    
    for i,j,k in commands:
        result.append(sorted(array[i-1:j]))
        kcommands.append(k)
        
    for i in range(len(result)):
        answer.append(result[i][kcommands[i]-1])
        
    return answer
```

그냥 리스트 정렬 잘 쓰면 되는 문제 쉽다.

다른 사람들의 풀이

1.map 과 lamda를 잘 쓴 경

```text
def solution(array, commands):
    return list(map(lambda x:sorted(array[x[0]-1:x[1]])[x[2]-1], commands))
```

```text
lambda x:sorted(array[x[0]-1:x[1]])[x[2]-1], commands
```

람다

`lambda 인자 : 표현식`

```text
def hap(x,y):
    return x+y
    
hap(10,20)

----------------

(lambda x,y:x+y)(10,20)
```

맵

`map(function,list)`

```text
list(map(lambda x: x ** 2, range(5)))
```

x제곱을 한 값들 그 x에는 range\(5\) 범위의 값이 들어가고 그것들을 적용시킨 결과를 list에 담아줌.



다시 본론으로 

```text
def solution(array, commands):
    return list(map(lambda x:sorted(array[x[0]-1:x[1]])[x[2]-1], commands))
```

list 결과물로 나와야 할 것은 정렬된 리스트에 있는 값 중 k-1위치에 있는 값이다.

x에 들어갈 값은 commands에 들어있는 것들이고 commands가 x로 들어간다.

-&gt; lambda로 슬라이싱을해, 리스트로 받은 것을 리턴할 때 commands에 저장된 인덱스 리스트로 리턴함.



