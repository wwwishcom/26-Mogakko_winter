# 빙고내기
<img width="258" height="166" alt="image" src="https://github.com/user-attachments/assets/9ea8d93a-2afe-4f83-b533-bd1245d18cb2" />
모각코에서 한 하단의 백준 풀이 외에도 다양한 문제를 풀어 빙고를 완성시켰다.

## BaekJoon 11720. 숫자의 합

Python 풀이

[11720번: 숫자의 합](https://www.acmicpc.net/problem/11720)

문자열은 문자들의 리스트처럼 작동한다.

```python
n = int(input())
nums = input()

print(sum(int(digit) for digit in nums))
```

nums = “54321”

과 같다면

nums[0]은 당연히 5이고

nums[4]는 당연히 1이다.

이런 식으로 진행하면

nums를 input()으로 입력받았으므로 

for digit in nums를 통해 한 글자 한 글자 하나당의 숫자들을 받아 이들의 sum을 구하면 총합을 구할 수 있다.

## BaekJoon 5597. 과제 안 내신 분..?

Python 풀이

[5597번: 과제 안 내신 분..?](https://www.acmicpc.net/problem/5597)

```python
a = [i for i in range(1, 31)]
for _ in range(28):
    a.remove(int(input()))
print(min(a))
print(max(a))
```

### 문제 요약

 1~30번 학생 중 28명이 과제 제출. 안 낸 2명 찾기

문제를 보고 대강 든 생각은 우선 학생들이 30명이라고 주어졌기 때문에 (1, 31)이라는 범위의 리스트에서 입력한 출석번호를 빼면 제출하지 않은 학생들이 나오겠다는 생각을 했다.

따라서 아래와 같이 문제를 풀었다.

### 문제 풀이

1. 1~30 리스트 만들기
2. 제출한 28명 번호를 리스트에서 제거
3. 남은 2명 중 작은 번호, 큰 번호 출력

출력이 두 줄이며 첫 번째 줄엔 제출하지 않은 학생의 출석번호 중 가장 작은 것을 출력하고, 두 번째 줄에서 그 다음의 출석번호를 쓰라고 했으므로

min(a), max(a)를 차례대로 출력하면 된다.

**동작 예시:**

```python
a = [1,2,3,...,30]
3 제출 → remove(3) → [1,2,4,5,...,30]
1 제출 → remove(1) → [2,4,5,...,30]

28명 제출 후 → [5, 23] 남음
→ 5 출력
→ 23 출력
```

## BaekJoon 2562. 최댓값

Python 풀이

[2562번: 최댓값](https://www.acmicpc.net/problem/2562)

```python
nums = [int(input()) for _ in range(9)]
print(max(nums))
print(nums.index(max(nums)) + 1)
```

### 문제 요약

9개의 자연수 중 최댓값과 그 위치를 출력해야한다.

우선 다행히도 9개의 자연수라고 개수가 딱 정해져있다.

첫 번째 줄부터 아홉 번째 줄까지 한 줄에 하나의 자연수가 주어지므로

for _ in range(9)를 이용하여 반복하여 입력할 필요가 있어보인다.

이를 리스트에 저장하고 max() 를 통해 최댓값을 출력한 뒤, 이에 대한 인덱스를 찾으면 될 것 같다.

그리고 index에서 주의할 점은 리스트가 0부터 시작하기 때문에 인덱스값을 출력할 때 +1을 해주어야한다.

## BaekJoon 1978. 소수 찾기

Python 풀이

[1978번: 소수 찾기](https://www.acmicpc.net/problem/1978)

```python
n = int(input())
nums = list(map(int, input().split()))

count = 0 

for num in nums:
    if num == 1:
        continue
    is_prime = True
    for i in range(2, num):
        if num % i == 0:
            is_prime = False
            break
    
    if is_prime:
        count += 1

print(count)
```

1은 소수가 아니므로

```python
if num == 1:
```

을 통해서 숫자가 1일 때는 count 하지 않고 넘어가는 식으로 진행했다.

또한 나누어떨어지면 소수가 아니므로 

```python
if num % i == 0:
		is_prime = False
		break
```

코드를 사용했다.


