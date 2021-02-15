# 프로그래머스 - 해시

문제 링크 : [https://programmers.co.kr/learn/courses/30/lessons/42576\#qna](https://programmers.co.kr/learn/courses/30/lessons/42576#qna)

1.처음에는 그냥 단순하게 set 자료구조를 이용하여 풀려고 했다 -&gt; 실패

중복인 사람을 카운트 해야하는데 set을 하는 순간 중복인 사람이 사라져서 카운팅을 할 수가 없게 되어버림..ㅠ

2.딕셔너리를 이용하면 된다길래 딕셔너리로 구현을 했다 -&gt; 실패

가장 노멀한 케이스는 출력이 되지만,,\(위도 마찬가지다\) 효율성 테스트에서 최악을 보이고, 심지어 테스트케이스 3 4 5 죄다 안되어서 패스

3.인터넷을 검색하다 나온 새로운 모듈!

![](../.gitbook/assets/image%20%285%29.png)

바로 이건데, 1과 2를 결합한 느낌으로 풀 수 있었다.

collections.Counter\(participant\) 이렇게 하면 particiapant에 있는 값을 dictionary 화 해줌과 동시에 해당 key값들 중 중복되는 요소의 개수를 value로 넣어준다.

![](../.gitbook/assets/image%20%286%29.png)

이렇게 말이다 ! 이렇게 예쁘게 포장된 콜렉션은 더하기 빼기가 가능하다.

```text
import collections

def solution(participant, completion):
    
    result = collections.Counter(participant) - collections.Counter(completion)

    return list(result)[0]
```



