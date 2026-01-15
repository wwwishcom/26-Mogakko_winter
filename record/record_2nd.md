## BaekJoon 2869. 달팽이는 올라가고 싶다

Python 풀이

[2869번: 달팽이는 올라가고 싶다](https://www.acmicpc.net/problem/2869)

문제가 너무 귀엽다

낮에는 A미터 올라가고 밤에는 B미터 내려간댄다

초딩 때 사고력문제 이런 거에서 많이 풀어본 거 같다

문제 이해가 됐으니 로직을 짜보자.

1. 첫째 줄에 세 정수 A, B, V(나무의 높이)를 입력받는다.
2. 하루에 달팽이가 올라가는 길이는 (A-B) 미터이다.
3. 며칠씩 올라간뒤 낮에 A미터 올라가고 정상에 올라가면, 그 즉시 며칠+1 을 계산하여 며칠이 걸리는지 알아낸다.
       

```python
A, B, V = map(int, input().split())
count = 0
distance = 0

while True:
    count += 1
    distance += A
    if distance >= V:
        break
    distance -= B

print(count)
```
어라..
백준에서 시간 초과라고 떴다

효율이 안 좋다는 말이다.

```python
import math

A, B, V = map(int, input().split())
print(math.ceil((V - A) / (A - B)) + 1)
```

맘에는 안 들지만 이런 식으로 진행해야겠다.

math.ceil을 통해서 올림을 진행하는데

핵심 조건부터 정리를 해보자면

낮: A만큼 올라감

밤: B만큼 내려감

목표: V 이상 도달

도착한 날에는 미끄러지지 않음

이렇게이다.

마지막날 직전의 위치가 가장 중요하다.

마지막 날 낮에 A를 더해서 V 이상이면 끝이므로

```python
전날까지의 위치 ≥ V - A
```

이 지점까지만 미리 올라가 있으면 된다.

하루 순이동은 A - B이므로

날짜는 x ≥ (V - A) / (A - B) 이런 식으로 된다.

다만 지금 x는 마지막날 제외한 날짜 수이므로 여기에 +1 을 해준다

## BaekJoon 1697. 숨바꼭질

Python 풀이

[1697번: 숨바꼭질](https://www.acmicpc.net/problem/1697)

**문제요약**

처음 봤을 땐 쉬워보였는데 생각보다 많이 어렵다 ^_^

```python
     N                              K
-------------------------------------------------
    빙수                           동생
```

수빈이의 위치는 N이고

동생의 위치는 K 라고 한다.

동생의 위치는 고정이며,

수빈이는 +1, -1, 또는 x2를 하여 순간이동 할 수 있다.

각각 1초씩 걸리며, 수빈이가 동생을 찾는 데 가장 빨리 걸리는 시간을 구해야한다.

간단하게 **로직**을 떠올려보자

우선 당연히도

1. map(int, input(). split()) 을 통해서 수빈이와 동생의 위치를 차례대로 입력받는다.
    
    그 다음으로는
    
2. n → n+1, n-1, 2n → . . .
    
    이런 식으로 갈 수 있는 위치들을 체크해본다.
    
    3방향으로 다 이동하되 가본 곳이면 큐에서 빼고, 안 가본 곳이면 큐에 추가한다.
    
    이때, 큐를 쓰는 이유는 리스트의 경우, 백준에서 자꾸 시간초과가 나는 걸 겪었기 때문.
    

일단은 시간을 기록할 visited[] 리스트를 만들어야하고,

처음 n값 (수빈이의 위치)를 0(걸리는 시간 0초)으로 잡고,

그 뒤로 n+1, n-1, 2n과 같은 위치의 각각 값은 1초가 되고,

이에 따라 세 방향으로 점점 생겨나는 새로운 값은 2초가 된다.

이때, 최소시간의 거리를 구하는 것이므로 중복된 위치에 +1초를 하면 안 되고, 새로운 위치에만 추가를 해야한다.

이처럼 시간을 기록하는 visited[]는 저장용이므로 리스트를 사용하고,

```python
0초: queue = [5]
      ↓ popleft()
     5 처리 (0초 위치) → 4, 6, 10 추가

1초: queue = [4, 6, 10]  ← 이 3개 모두 1초 위치
      ↓ popleft()
     4 처리 (1초 위치) → 3, 8 추가
      ↓ popleft()
     6 처리 (1초 위치) → 7, 12 추가
      ↓ popleft()
     10 처리 (1초 위치) → 9, 11, 20 추가

2초: queue = [3, 8, 7, 12, 9, 11, 20]  ← 이 7개 모두 2초 위치
      ↓ popleft()
     3 처리 (2초 위치) → ...
      ↓ popleft()
     8 처리 (2초 위치) → ...
     ...
```

위와 같이 세 방향으로 점점 새로운 위치들이 생기는데

가까운 곳부터 순서대로 탐색하기 위해

큐를 사용한다!

정리하자면, 큐는 순서대로 처리하기 위함이고

visited는 중복을 방지하기 위함이다.

따라서 아래와 같이 코드를 구성했다.

```python
from collections import deque

N, K = map(int, input().split())

if N == K:
    print(0)
else:
    visited = [-1] * 100001  
    queue = deque([N])       
    visited[N] = 0           
    
    while queue:
        current = queue.popleft()
        for next_pos in [current-1, current+1, current*2]:
            if 0 <= next_pos <= 100000 and visited[next_pos] == -1:
                visited[next_pos] = visited[current] + 1
                queue.append(next_pos)
                if next_pos == K:
                    print(visited[next_pos])
                    exit()
```

성공이다 ㅜ

솔직히 VS code에 썼다 지웠다 100번은 한 것 같다. 진심으로 너무한 문제였다!
